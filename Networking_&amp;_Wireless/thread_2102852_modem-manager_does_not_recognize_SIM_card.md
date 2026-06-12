---
title: "modem-manager does not recognize SIM card"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by diagonallemma on 2013-01-08
Hello,

I have a Thinkpad X61 with a built-in SIM card slot for mobile broadband. My Australian SIM card (Telstra) is always recognized, but now I'm in Switzerland and want to use another prepaid card (from Sunrise). The card works in my mobile phone, but when I put it into the notebook, I don't get any Mobile Broadband options in NetworkManager. /var/log/syslog shows an eternal loop of the following lines:

```

Jan  8 12:56:47 x61 NetworkManager[786]: <info> modem-manager is now available
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Sierra'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'X22X'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Option'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Nokia'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Huawei'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'SimTech'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Longcheer'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Linktop'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'AnyData'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'ZTE'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'MotoC'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Option High-Speed'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Samsung'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Wavecom'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Gobi'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Novatel'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Ericsson MBM'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Cinterion'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Iridium'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Loaded plugin 'Generic'
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  Successfully loaded 20 plugins
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  (ttyUSB0) opening serial port...
Jan  8 12:56:47 x61 modem-manager[2073]: <warn>  (ttyUSB0): port attributes not fully set
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  (ttyUSB1) opening serial port...
Jan  8 12:56:47 x61 modem-manager[2073]: <warn>  (ttyUSB1): port attributes not fully set
Jan  8 12:56:47 x61 modem-manager[2073]: <info>  (ttyUSB2) opening serial port...
Jan  8 12:56:47 x61 modem-manager[2073]: <warn>  (ttyUSB2): port attributes not fully set
Jan  8 12:56:51 x61 modem-manager[2073]: <info>  (ttyUSB2) opening serial port...
Jan  8 12:56:51 x61 modem-manager[2073]: <warn>  (ttyUSB2): port attributes not fully set
Jan  8 12:56:51 x61 modem-manager[2073]: <info>  (ttyUSB0) closing serial port...
Jan  8 12:56:51 x61 modem-manager[2073]: <info>  (ttyUSB0) serial port closed
Jan  8 12:56:51 x61 modem-manager[2073]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1 claimed port ttyUSB0
Jan  8 12:57:00 x61 modem-manager[2073]: <info>  (ttyUSB1) closing serial port...
Jan  8 12:57:00 x61 modem-manager[2073]: <info>  (ttyUSB1) serial port closed
Jan  8 12:57:00 x61 modem-manager[2073]: <info>  (ttyUSB1) opening serial port...
Jan  8 12:57:03 x61 modem-manager[2073]: <info>  (ttyUSB2) closing serial port...
Jan  8 12:57:03 x61 modem-manager[2073]: <info>  (ttyUSB2) serial port closed
Jan  8 12:57:03 x61 modem-manager[2073]: <info>  (ttyUSB2) opening serial port...
Jan  8 12:57:06 x61 modem-manager[2073]: <info>  (ttyUSB1) closing serial port...
Jan  8 12:57:06 x61 modem-manager[2073]: <info>  (ttyUSB1) serial port closed
Jan  8 12:57:09 x61 modem-manager[2073]: <info>  (ttyUSB2) closing serial port...
Jan  8 12:57:09 x61 modem-manager[2073]: <info>  (ttyUSB2) serial port closed
Jan  8 12:57:09 x61 NetworkManager[786]: <info> the modem manager disappeared
Jan  8 12:57:09 x61 NetworkManager[786]: <info> trying to start the modem manager...
Jan  8 12:57:09 x61 dbus[740]: [system] Activating service name='org.freedesktop.ModemManager' (using servicehelper)
Jan  8 12:57:09 x61 modem-manager[2130]: <info>  ModemManager (version 0.6.0.0) starting...
Jan  8 12:57:09 x61 dbus[740]: [system] Successfully activated service 'org.freedesktop.ModemManager'
Jan  8 12:57:09 x61 NetworkManager[786]: <info> modem-manager is now available
Jan  8 12:57:09 x61 modem-manager[2130]: <info>  Loaded plugin 'Sierra'
...

```

lsusb lists the wireless device as

```

Bus 006 Device 002: ID 1199:6813 Sierra Wireless, Inc. 

```

lsmod has those lines with "sierra" in them:

```

sierra                 17898  1 
usbserial              36683  4 sierra

```

From dmesg, these might be relevant:

```

[    7.739637] usbcore: registered new interface driver sierra
[    7.739724] sierra 6-1:1.0: >Sierra USB modem converter detected
[    7.739700] USB Serial support registered for Sierra USB modem
[    7.739724] sierra 6-1:1.0: >Sierra USB modem converter detected
[    7.742386] usb 6-1: >Sierra USB modem converter now attached to ttyUSB0
[    7.742649] usb 6-1: >Sierra USB modem converter now attached to ttyUSB1
[    7.742771] usb 6-1: >Sierra USB modem converter now attached to ttyUSB2
[    7.744024] thinkpad_acpi: rfkill switch tpacpi_wwan_sw: radio is unblocked
...
[    7.766614] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[    7.766616] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[    7.766697] iwl4965 0000:03:00.0: >Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[    8.644187] iwl4965 0000:03:00.0: >device EEPROM VER=0x36, CALIB=0x5
[    8.656980] iwl4965 0000:03:00.0: >Tunable channels: 11 802.11bg, 13 802.11a channels
[    8.657084] iwl4965 0000:03:00.0: >irq 46 for MSI/MSI-X
[   13.480006] wlan0: authenticate with 7e:11:be:24:aa:4b
[   13.488100] wlan0: send auth to 7e:11:be:24:aa:4b (try 1/3)
[   13.489197] wlan0: authenticated
[   13.498017] wlan0: waiting for beacon from 7e:11:be:24:aa:4b
[   13.592042] wlan0: associate with 7e:11:be:24:aa:4b (try 1/3)
[   13.593740] wlan0: RX AssocResp from 7e:11:be:24:aa:4b (capab=0x431 status=0 aid=1)
[   13.619752] wlan0: associated
[   13.619926] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.225285] init: modemmanager main process (758) killed by ABRT signal
[   31.225313] init: modemmanager main process ended, respawning
[   31.233475] init: modemmanager main process (2109) terminated with status 255
[   31.233504] init: modemmanager main process ended, respawning
[   31.242658] init: modemmanager main process (2111) terminated with status 255
[   31.242684] init: modemmanager main process ended, respawning
[   31.250566] init: modemmanager main process (2113) terminated with status 255
[   31.250593] init: modemmanager main process ended, respawning
[   31.259322] init: modemmanager main process (2115) terminated with status 255
[   31.259375] init: modemmanager main process ended, respawning
[   31.268315] init: modemmanager main process (2117) terminated with status 255
[   31.268344] init: modemmanager main process ended, respawning
[   31.275496] init: modemmanager main process (2119) terminated with status 255
[   31.275526] init: modemmanager main process ended, respawning
[   31.283100] init: modemmanager main process (2121) terminated with status 255
[   31.283127] init: modemmanager main process ended, respawning
[   31.290573] init: modemmanager main process (2123) terminated with status 255
[   31.290599] init: modemmanager main process ended, respawning
[   31.298025] init: modemmanager main process (2125) terminated with status 255
[   31.298052] init: modemmanager main process ended, respawning
[   31.305159] init: modemmanager main process (2127) terminated with status 255
[   31.305186] init: modemmanager respawning too fast, stopped

```

Would be grateful for any ideas!

---

### Post by silverbullet007 on 2013-01-17
I'm having a VERY similar issue.. my SIM hasn't changed but the USB Sierra Mercury isn't recognized by 12.10 and dmesg says the same that yours does.

---

