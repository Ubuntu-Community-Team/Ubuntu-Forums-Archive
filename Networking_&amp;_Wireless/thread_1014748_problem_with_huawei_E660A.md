---
title: "problem with huawei E660A"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by himerus on 2008-12-18
hi,
I'm using Ubuntu 8.10 i386, andi connected a huawei E660A and i get an invalid dial command.
my syslog sais:
```
Dec 18 12:24:00 himerus kernel: [38333.156074] usb 5-2: new full speed USB device using uhci_hcd and address 12
Dec 18 12:24:00 himerus kernel: [38333.370552] usb 5-2: configuration #1 chosen from 1 choice
Dec 18 12:24:00 himerus kernel: [38333.381952] usb-storage: probe of 5-2:1.0 failed with error -5
Dec 18 12:24:00 himerus kernel: [38333.383670] option 5-2:1.0: GSM modem (1-port) converter detected
Dec 18 12:24:00 himerus kernel: [38333.387743] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
Dec 18 12:24:00 himerus kernel: [38333.398000] usb-storage: probe of 5-2:1.1 failed with error -5
Dec 18 12:24:00 himerus kernel: [38333.399715] option 5-2:1.1: GSM modem (1-port) converter detected
Dec 18 12:24:00 himerus kernel: [38333.402505] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB3
Dec 18 12:24:00 himerus kernel: [38333.409258] usb-storage: probe of 5-2:1.2 failed with error -5
Dec 18 12:24:00 himerus kernel: [38333.411055] option 5-2:1.2: GSM modem (1-port) converter detected
Dec 18 12:24:00 himerus kernel: [38333.413295] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB4
Dec 18 12:24:00 himerus kernel: [38333.421223] scsi39 : SCSI emulation for USB Mass Storage devices
Dec 18 12:24:05 himerus kernel: [38338.428279] scsi 39:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Dec 18 12:24:05 himerus kernel: [38338.431158] scsi 39:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Dec 18 12:24:05 himerus kernel: [38338.477147] sr1: scsi-1 drive
Dec 18 12:24:05 himerus kernel: [38338.478442] sr 39:0:0:0: Attached scsi generic sg2 type 5
Dec 18 12:24:05 himerus kernel: [38338.485295] sd 39:0:0:1: [sdb] Attached SCSI removable disk
Dec 18 12:24:05 himerus kernel: [38338.485958] sd 39:0:0:1: Attached scsi generic sg3 type 0
```

i did sudo wvdial --config /etc/wvdial-huawei.conf
the wvdial-huawei.conf is :
```
[Dialer Defaults]
Modem = /dev/ttyUSB4
Baud = 3600000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 =
Area Code =
Phone = *99#
Username = Anything
Password = Anything
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 0
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1
```

the log is :
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.
--> Disconnecting at Thu Dec 18 12:27:35 2008

```

please, can someone help me out ? i need to use this pretty quick.

regards,
Viorel

---

### Post by razy60 on 2008-12-18
What happens if you try to use network manager?

Raz

---

