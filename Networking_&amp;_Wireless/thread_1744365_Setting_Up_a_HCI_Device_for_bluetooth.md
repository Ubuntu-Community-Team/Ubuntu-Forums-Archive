---
title: "Setting Up a HCI Device for bluetooth ?"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Selo on 2011-04-30
[SIZE=2]Hi there Ubuntu people !

I'm using Ubuntu 11.04 and bluetooth turn/off is not possible. However, with 2.6.37 kernel it is possible. Now i have gathered whole info about the device(mac adress, usb port etc) from 2.6.37 and what i need is to somehow use those info in kernel 2.6.38 so that bluetooth works.[/SIZE] 

**lsusb** in [COLOR=DarkGreen]2.6.37[/COLOR] (while bt is on)

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1241:1603 Belkin Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 09da:8090 A4 Tech Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**[COLOR=Navy]Bus 005 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device[/COLOR]**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[B]

hciconfig -a[/B] in [COLOR=DarkGreen]2.6.37[/COLOR]

```
hci0:    
    Type: BR/EDR  Bus: USB
    BD Address: 00:24:2C:F7:93:3B  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN 
    RX bytes:687 acl:0 sco:0 events:25 errors:0
    TX bytes:594 acl:0 sco:0 commands:25 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'Selocan-0'
    Class: 0x4a0100
    Service Classes: Networking, Capturing, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 2.1 (0x4)  Revision: 0x5259
    LMP Version: 2.1 (0x4)  Subversion: 0x424c
    Manufacturer: Broadcom Corporation (15)
```[B]
dmesg |grep Bluetooth[/B] in [COLOR=DarkGreen]2.6.37[/COLOR]

```
selo@Selocan:~$ dmesg |grep Bluetooth
[   48.128558] Bluetooth: Core ver 2.15
[   48.128588] Bluetooth: HCI device and connection manager initialized
[   48.128591] Bluetooth: HCI socket layer initialized
[   56.413602] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   56.505756] Bluetooth: L2CAP ver 2.15
[   56.505759] Bluetooth: L2CAP socket layer initialized
[   56.525260] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   56.525263] Bluetooth: BNEP filters: protocol multicast
[   56.543156] Bluetooth: SCO (Voice Link) ver 0.6
[   56.543159] Bluetooth: SCO socket layer initialized
[   56.637648] Bluetooth: RFCOMM TTY layer initialized
[   56.637654] Bluetooth: RFCOMM socket layer initialized
[   56.637656] Bluetooth: RFCOMM ver 1.11

```[B]
dmesg |grep Bluetooth[/B] in [COLOR=Red]2.6.38[/COLOR]

```
selo@Selocan:~$ dmesg |grep Bluetooth
[ 1395.958925] Bluetooth: Core ver 2.15
[ 1395.958965] Bluetooth: HCI device and connection manager initialized
[ 1395.958969] Bluetooth: HCI socket layer initialized
```**lsusb** in [COLOR=Red]2.6.38[/COLOR]

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1241:1603 Belkin Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 09da:8090 A4 Tech Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**[COLOR=Red]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```**hciconfig -a in **[COLOR=Red]2.6.38[/COLOR]--> Nothing happens**.**

---

### Post by Selo on 2011-04-30
Bumb

---

