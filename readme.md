# Инструкция по прошивки Bluetooth модуля

Программа в Bluetooth модуле состоит из трех компонентов:
1. SoftDevice - программа BlueTooth стека;
2. BootLoader - загрузчик, для обновление ПО по воздуху;
3. Основкая прошивка;

Запись ПО поизводится в 2 этапа:
1. Прошивка SoftDevice и BootLoader, через программатор Segger J-Link:
	1. Подключить прграмматор Segger J-Link к Bluetooth модулю;
	2. Запустить программу Segger J-Flash;
	3. Выбрать контроллер NRF52840_xxAA;
	4. Записать файл s140_nrf52_7.2.0_softdevice.hex;
	5. Записать файл BootLoader v*.hex;

> файлы расположены по адресу T:\Bases\ПО от КБ\Программы для микроконтроллеров\BtBLE Nordic\ИЗМ5.174.018 v2.3\Модем периферийный\BootLoader v0.0.0

2. Прошивка основной программы, через программу SiamService;
	1. Запустить программу SiamService версии не ниже 2.14.0
	2. Через вкладку поиск, добавить устройство BL_0000
	(протокол и Адрес программа SiamService предложит автоматически, согласна настройкам модуля)
![Вкладка поиска](./image/SiamService1.png)
	3. Добавленное устройство появится в панели управления.
	4. Подключиться к усройству и перейти на вкладку настройки.
![Вкладка Настройки](./image/SiamService2.png)
	5. В разделе Основные настройки, установить номер, и сохранить.
![Вкладка Основные Настройки](./image/SiamService3.png)
	6. В разделе прошивка, выбрать файл основной прошивки (в формате *.bin) и обновить.
![Вкладка Прошивка](./image/SiamService4.png)
	>	* при успешном обновлении прошивки значения Size и Crc в разделе Current application изменятся и будут соответствовать значениям Size и Crc в разделе New application.
	>	* Если Size и Crc в разделе Current application не изменились или не соответствуют значениям Size и Crc в разделе New application, повторно запустить обновление.
	7. Выполнить перезапуск устройства. В разделе Основных настроек нажать кнопку "Reboot" или выключить питание.



# Инструкция по Обновлению прошивки

Для обновления прошивки используется программа SiamService версии не ниже 2.14.0

1. Запустите SiamService
2. Через панель поиска добавьте устройство, которое необходимо обновить, установив при подключении парамерты (выбрать протокол ModBus, Адрес 127)
![Вкладка поиска](./image/SiamService5.png)
3. В панели управления подключитесь к добавленному устройству.
4. В настройках устройства, в разделе основные найтройки переключите ражим **BootMode** в Bootloader и сохраните.
![Вкладка Настройки](./image/SiamService6.png)
5. Выполнить перезапуск устройства. В разделе Основных настроек нажать кнопку "Reboot" или выключить питание.
6. В панели управления отключитесь от устройства.
7. Через панель поиска, добавьте устройство BL_0000 (0000 - номер обновляемого устройства в режиме BootLoader), установив при подключении парамерты (выбрать протокол ModBus, Адрес 127)
![Вкладка поиска](./image/SiamService1.png)
8. В панели управления подключитесь к добавленному устройству.
9. В настройках устройства, в разделе прошивка выбрать файл основной прошивки (в формате *.bin) и обновить.
![Вкладка Прошивка](./image/SiamService4.png)

>	* при успешном обновлении прошивки значения Size и Crc в разделе Current application изменятся и будут соответствовать значениям Size и Crc в разделе New application.
>	* Если Size и Crc в разделе Current application не изменились или не соответствуют значениям Size и Crc в разделе New application, повторно запустить обновление.
10. В настройках устройства, в разделе основные найтройки переключите ражим **BootMode** в Application и сохраните.
![Вкладка Настройки](./image/SiamService7.png)
11. Выполнить перезапуск устройства. В разделе Основных настроек нажать кнопку "Reboot" или выключить питание.