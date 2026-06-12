---
title: "How to verify whether a USB device is recognized as a modem"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Sven6210 on 2010-03-04
I am running Ubuntu 9.10 KK (UNR) on my Netbook and I use the Huawei E5830 as UMTS modem. I can connect to the E5830 through WiFo (no problem at all) and USB.

How can I verify whether the E5830 is recognized as modem when connecting it to USB? It changes the mode from USB storage device to USB modem, however I think I can not access it as a modem.

Any help is welcome.

Thank you in advance

Sven

---

### Post by tnat on 2010-03-04
Hi,

```
ls -l /dev/tty*|grep ttyUSB0|wc -l
```

0.... no Huawei-modem connected
1.... device is registered as modem

**dmesg** should output something like
[ 1025.804206] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 1025.947828] usb 1-6: configuration #1 chosen from 1 choice
[ 1025.968345] option 1-6:1.0: GSM modem (1-port) converter detected
[ 1025.968661] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[ 1025.976248] option 1-6:1.1: GSM modem (1-port) converter detected
[ 1025.976530] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[ 1025.984702] option 1-6:1.2: GSM modem (1-port) converter detected
[ 1025.984985] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
[ 1025.999723] scsi11 : SCSI emulation for USB Mass Storage devices

---

### Post by Sven6210 on 2010-03-05
Great, thank you very much.

---

### Post by hatalar205 on 2010-03-05
Right click on Network Manager applet.
Edit Connections.
-Mobile Broad Band.
--Add
The rest is simple.

---

### Post by Sven6210 on 2010-03-21
I had some time on the weekend and did some tests with Ubuntu 10.04 beta1 - I am amazed how stable it already works. At least for me.

However I am still struggling with the Huawei E5830 modem. I also have a Huawei E160 which works perfectly with the network-manager. I'm able to connect to UMTS services and I can use all applications such as Firefox, Thunderbird, Skype and even Twickle for VoIP.

However I am failing with the E5830 in some way. When I am connected to the E5830 through USB I can run the above command and the computer says there is a modem installed. However network-manager does not see this modem and therefore I can not use the modem through USB. I can use it by connecting via WLAN with the modem - however I also would like to be able to use it (and change the APN settings) when connected through USB. The WLAN connection unfortunately does not allow changing the APN settings.

Has anybody some experience with the E5830 under Ubuntu?

---

### Post by pdc on 2010-03-22
I think the only other thing to suggest to you is to follow the advice of a seasoned mobile warrior like P Curtis

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

who says keep away from 9.10 and stick with 9.04 Ubuntu;

so one could only suggest you try a liveCD of 9.04 and see how you go

---

### Post by afss on 2010-03-22
i am trying to connect to internet via wll wireless phone.i was able to connect through xp..i am new to ubuntu and know very less of it.
i think ubuntu dont detect my modem.
this is my lsusb output

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 109b:3197  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0421:002f Nokia Mobile Phones 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

this is my wvdial output

Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check Def Route"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

can any1 tell me what the problem is

---

### Post by pdc on 2010-03-22
hi abss;

you have already opened a thread on this topic;

best not to double-post; stick to one, and new, thread

---

### Post by fxlovers on 2010-03-23
> **afss said:**
> i am trying to connect to internet via wll wireless phone.i was able to connect through xp..i am new to ubuntu and know very less of it.
i think ubuntu dont detect my modem.
this is my lsusb output

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 109b:3197  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0421:002f Nokia Mobile Phones 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

this is my wvdial output

Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check Def Route"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

can any1 tell me what the problem is

try this :

instal usb_modemswitch <= i use Ubuntu 9.10 [http://packages.ubuntu.com/karmic/usb-modeswitch](http://packages.ubuntu.com/karmic/usb-modeswitch)

then :

sudo modprobe usbserial vendor=0x109b product=0x3197

---

### Post by pdc on 2010-03-23
this guy is already running another thread fxlovers, and my post was suggesting to him he just stick to his other post!

---

### Post by fxlovers on 2010-03-23
> **pdc said:**
> this guy is already running another thread fxlovers, and my post was suggesting to him he just stick to his other post!

could you help me please?

i still can't connect to internet using skytech m110 evdo Rev.A Modem.

:popcorn:

---

