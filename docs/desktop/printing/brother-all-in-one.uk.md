---
title: Встановлення та налаштування принтера Brother All-in-One
author: Joseph Brinkman
contributors: Steven Spencer
tested with: 9.4
tags:
  - робочий стіл
  - підтримка принтера
---

## Вступ

Друк і сканування за допомогою багатофункціонального принтера Brother можливе в Linux завдяки стороннім драйверам принтера та сканера Brother «все в одному».

!!! info "примітка"

```
Процедуру перевірено на Brother MFC-J480DW.
```

## Передумови та припущення

- Робоча станція Rocky 9.4
- привілеї `sudo`
- Універсальний принтер і сканер Brother

У цьому посібнику передбачається, що ваш принтер доступний із вашої робочої станції через пряме з’єднання USB або LAN (локальна мережа). Підключення принтера до локальної мережі виходить за межі цієї статті.

## Додавання принтера в GNOME

1. Відкрийте ++"Settings"++
2. У меню зліва натисніть ++"Printers"++
3. Зверніть увагу на банер у верхній частині вікна з написом «Unlock to Change Settings».
4. Натисніть ++"Unlock"++ і введіть облікові дані `sudo`.
5. Натисніть ++"Add"++

Після натискання ++"Add"++ ++"Settings"++ почне сканування принтерів. Якщо ваш принтер не відображається, але ви знаєте його IP-адресу в локальній мережі, введіть IP-адресу вручну. Підключення принтера до домашньої мережі виходить за рамки цієї статті.

Відкриється вікно програмного забезпечення, яке намагається знайти та встановити драйвери принтера. Як правило, це не вдасться. Ви повинні перейти на веб-сайт Brother, щоб установити додаткові драйвери.

## Завантаження та встановлення драйверів

[Інструкції зі встановлення сценарію встановлення драйвера Brother:](https://support.brother.com/g/b/downloadlist.aspx?\&c=us\&lang=en\&prod=mfcj480dw_us_eu_as\&os=127){target="_blank"}

1. [Завантажте сценарій bash для драйвера принтера Brother MFC-J480DW](https://support.brother.com/g/b/downloadtop.aspx?c=us\&lang=en\&prod=mfcj480dw_us_eu_as){target="_blank"}

2. Відкрийте вікно терміналу.

3. Перейдіть до каталогу, куди ви завантажили файл на останньому кроці. напр. `cd Downloads`

4. Введіть цю команду, щоб розпакувати завантажений файл:

   ```bash
   gunzip linux-brprinter-installer-*.*.*-*.gz
   ```

5. Отримайте авторизацію суперкористувача за допомогою команди `su` або `sudo su`.

6. Запустіть інструмент:

   ```bash
   bash linux-brprinter-installer-*.*.*-* Brother machine name
   ```

7. Розпочнеться установка драйвера. Дотримуйтеся вказівок на екрані встановлення.

Процес встановлення може зайняти деякий час. Зачекайте, доки він завершиться. Після завершення ви можете надіслати тестовий друк.

## Підтримка сканера

Xsane — це утиліта для сканування, яка надає графічний інтерфейс користувача для сканування. Вона має пакети, доступні з репозиторію appstream, які не потребують додаткового налаштування.

```bash
sudo dnf install sane-backends sane-frontends xsane
```

Графічний інтерфейс Xsane виглядає лякаюче, але просте сканування є простим. Коли ви запускаєте Xsane, з’являється вікно з кнопкою, де ви можете ++"Acquire a preview"++. Буде зроблено попередній перегляд сканованого зображення. Після завершення сканування натисніть кнопку ++"Start"++ у головному меню.

Щоб отримати докладніший посібник із xsane, прочитайте цю [статтю математичного факультету Кембриджського університету](https://www.maths.cam.ac.uk/computing/printing/xsane){target="_blank"}

## Висновок

Після встановлення необхідних драйверів Brother і Xsane ви зможете друкувати та сканувати на своєму універсальному принтері та сканері Brother.