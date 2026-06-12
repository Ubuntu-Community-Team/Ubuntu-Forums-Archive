---
title: "bt device not running (timeout)"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by SteMMo on 2013-02-09
Hi there,

stefano@ghilba:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

stefano@ghilba:~$ uname -a
Linux ghilba 3.2.0-38-generic #59-Ubuntu SMP Tue Feb 5 17:53:49 UTC 2013 i686 i686 i386 GNU/Linux

I own a bt USB dongle i insert in the from of my Dell desktop.
This is some outputs I guess are useful for gurus:
 
stefano@ghilba:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)
 
stefano@ghilba:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)
 
stefano@ghilba:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0c10:0000  
Bus 005 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
 
stefano@ghilba:~$ dmesg | grep btusb
[   29.789052] usbcore: registered new interface driver btusb
 
stefano@ghilba:~$ hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:11:F6:08:8C:F2  ACL MTU: 120:20  SCO MTU: 0:0
	DOWN 
	RX bytes:1448 acl:0 sco:0 events:52 errors:0
	TX bytes:228 acl:0 sco:0 commands:52 errors:0
	Features: 0xff 0xff 0x05 0x38 0x18 0x18 0x00 0x00
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 

stefano@ghilba:~$ sudo rfkill unblock all
 
stefano@ghilba:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)
 
stefano@ghilba:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)

stefano@ghilba:~$ sudo killall bluetoothd

stefano@ghilba:~$ sudo bluetoothd
stefano@ghilba:~$ sudo service bluetooth restart
bluetooth stop/waiting
bluetooth start/running, process 2964

stefano@ghilba:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)
 
stefano@ghilba:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)

stefano@ghilba:~$ hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:11:F6:08:8C:F2  ACL MTU: 120:20  SCO MTU: 0:0
	DOWN 
	RX bytes:3620 acl:0 sco:0 events:130 errors:0
	TX bytes:570 acl:0 sco:0 commands:130 errors:0
	Features: 0xff 0xff 0x05 0x38 0x18 0x18 0x00 0x00
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 

The device seems to be detected but it was unable to going up due to the timeout.
Any idea?

---

### Post by SteMMo on 2013-02-13
It could be depend on the USB key...

I'm trying with the DBT-120 key by DLink and the system is running.
Even if, after a while, a bluez module goes in a crash :(

---

### Post by SteMMo on 2013-02-16
I'm trying with a Live CD (7.04): the first BT key is running!!!


ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux


ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty


dmesg:
[  170.574035] Bluetooth: Core ver 2.11
[  170.575086] NET: Registered protocol family 31
[  170.575097] Bluetooth: HCI device and connection manager initialized
[  170.575103] Bluetooth: HCI socket layer initialized
[  170.661863] Bluetooth: L2CAP ver 2.8
[  170.661870] Bluetooth: L2CAP socket layer initialized
[  171.019253] Bluetooth: RFCOMM socket layer initialized
[  171.019283] Bluetooth: RFCOMM TTY layer initialized
[  171.019287] Bluetooth: RFCOMM ver 1.8
[  180.395385] NET: Registered protocol family 10
[  180.395554] lo: Disabled Privacy Extensions
[  190.800583] eth0: no IPv6 routers present

[  471.923468] usb 4-2.1: new full speed USB device using uhci_hcd and address 3
[  472.063498] usb 4-2.1: configuration #1 chosen from 1 choice
[  472.397446] Bluetooth: HCI USB driver ver 2.9
[  472.457780] usbcore: registered new interface driver hci_usb



ubuntu@ubuntu:~$ hciconfig -a
hci0:   Type: USB
        BD Address: 00:11:F6:08:8C:F2 ACL MTU: 120:20 SCO MTU: 0:0
        UP RUNNING PSCAN ISCAN 
        RX bytes:402 acl:0 sco:0 events:17 errors:0
        TX bytes:317 acl:0 sco:0 commands:17 errors:0
        Features: 0xff 0xff 0x05 0x38 0x18 0x18 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'ubuntu-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Uncategorized
        HCI Ver: 1.2 (0x2) HCI Rev: 0x0 LMP Ver: 1.2 (0x2) LMP Subver: 0x757
        Manufacturer: Silicon Wave (11)


ubuntu@ubuntu:~$ hcitool scan
Scanning ...
        94:71:AC:6F:73:81       Alcatel One Touch 810D



ubuntu@ubuntu:~$ hcitool scan
Scanning ...
        94:71:AC:6F:73:81       Alcatel One Touch 810D
        00:60:D1:00:00:33       Bluetooth Mouse


ubuntu@ubuntu:~$ sudo hidd --connect  00:60:D1:00:00:33

The BT mouse is running!!!

ubuntu@ubuntu:~$ hcitool con
Connections:
        < ACL 00:60:D1:00:00:33 handle 7 state 1 lm MASTER 


If i try to pair the cell phone, I see each other PC and phone but it is not possible pair them: the cell reply me something like:

Pairing refused by ubuntu-0



Any idea??

How can i connect the address book of the phone?

---

### Post by SteMMo on 2013-08-18
Again, after months, i'm not able to use my bt key.

stefano@ghilba:~$ uname -a
Linux ghilba 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:23:24 UTC 2013 i686 i686 i386 GNU/Linux

dmesg:
[12546.974018] usb 2-1.3: new full-speed USB device number 3 using uhci_hcd
[12547.679256] Bluetooth: Generic Bluetooth USB driver ver 0.6
[12547.685484] usbcore: registered new interface driver btusb


stefano@ghilba:~$ hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:11:F6:08:8C:F2  ACL MTU: 120:20  SCO MTU: 0:0
	DOWN 
	RX bytes:724 acl:0 sco:0 events:26 errors:0
	TX bytes:114 acl:0 sco:0 commands:26 errors:0

stefano@ghilba:~$ sudo hciconfig hci0 up
[sudo] password for stefano: 
Can't init device hci0: Connection timed out (110)

---

