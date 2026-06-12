---
title: "Netgear WNDA3100v2 Drivers"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by TipTricky on 2012-12-19
I am trying to use this usb wifi adapter in ubuntu 12.10 but i have used wine and diswrapper but i dont think i have the proper drivers. Can any one link a download to the proper drivers for this wifi card? Netgaer WNDA3100v2

---

### Post by chili555 on 2012-12-19
I probably have them and can attach them. Please post:```
lsusb
arch
```Thanks.

---

### Post by TipTricky on 2012-12-19
lsusb

Bus 001 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 004 Device 002: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

arch

i686

---

### Post by chili555 on 2012-12-19
> ID [COLOR="Red"]0846:9011[/COLOR] NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]Try these! If you get stuck, please post back and we'll be happy to help.

---

### Post by TipTricky on 2012-12-19
sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

any idea as to why i get this error? i used software center to install ndiswrapper

---

### Post by chili555 on 2012-12-19
> **TipTricky said:**
> sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

any idea as to why i get this error? i used software center to install ndiswrapperOld Chili was afraid of that. I must have been having another spell of denial. Please see here, unfortunately: [http://askubuntu.com/questions/206082/how-do-i-compile-ndiswrapper](http://askubuntu.com/questions/206082/how-do-i-compile-ndiswrapper)

---

### Post by TipTricky on 2012-12-19
ok so i fallowed the instructions from that post what now?
I type "sudo modprobe bdiswrapper" and it just drops me down to the next line

---

### Post by chili555 on 2012-12-19
> I type "sudo modprobe bdiswrapper" and it just drops me down to the next lineThat generally means you issued a command and the command was executed with no error or warning. That's what you wanted, yes?

Did you install the driver .inf and .sys files? What does this tell us?```
ndiswrapper -l
iwconfig
dmesg | grep ndis
```

---

### Post by TipTricky on 2012-12-19
Lol well i guess the next step would be unplug the Ethernet cable... :D Its working ok now. Thank you!!!

---

### Post by chili555 on 2012-12-19
Awesome! Please use thread tools at the top to mark Solved.

---

### Post by TipTricky on 2012-12-19
Thank you for your help and time!

---

