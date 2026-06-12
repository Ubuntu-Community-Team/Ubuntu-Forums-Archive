---
title: "Wireless TP-WN821N not activated"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by Robertsand on 2012-02-02
Folks,

I'm new to Ubuntu but have a problem getting my wireless usb dongle to work. There doesn't seem to be anything on the forum that quite covers this....

I have booted up a sick W*&^$%s 7 pc with a usb Ubuntu system on a trial basis. If I can get the wireless dongle working I can ditch the old operation system (I won't use the W word again).

I'm running```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
``` and can see the Atheros powered usb device in ```
ubuntu@ubuntu:~$ lsusb
Bus 008 Device 002: ID 04fc:0005 Sunplus Technology Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 002 Device 002: ID 19b6:2048 Infotech Logistic, LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**[COLOR=Red]Bus 001 Device 003: ID 0cf3:7015 Atheros Communications, Inc. [/COLOR]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I even seem to have the firmware because if I search in the file system for ar9170* I have:
```
/lib/firmware/ar9170-1.fw
/lib/firmware/ar9170-2.fw
/lib/firmware/ar9170.fw
/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ar9170
/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
/usr/src/linux-headers-2.6.32-21/drivers/net/wireless/ath/ar9170
/usr/src/linux-headers-2.6.32-21-generic/include/config/ar9170
```so what is Ubuntuspeak for wake up TP-Link and talk to me!

Help gratefully received :confused:

Andrew

---

### Post by Robertsand on 2012-02-04
After many happy hours mucking about I have cracked the problem.

1. Download the drivers from the tp-link.com website for the appropriate version
2. Install ndiswrapper (I used ndisgtk gui app)
3. from the drivers folder in the download I extracted _all_ three files from the XP 32 bit subdirectory and put them into the /tmp folder.
4. Point ndisgtk (+ Install New Driver) at the netathuw.inf and clicked "Install"
5. Fairly soon the led on the dongle started flashing and soon after that the system automatically picks up the wireless network and off we go.

Trying to get the native linux driver to work was a waste of my time. I realise that lsusb gives the vendor:product ID which in the case on my version 3 dongle is 0cf3:7015 and this in turn points to the ath9k_htc driver. Pulling this out of the compat-wireless package ( [http://linuxwireless.org/en/users/Download/stable#Stable_compat-wireless_releases](http://linuxwireless.org/en/users/Download/stable#Stable_compat-wireless_releases) )
and the firmware ( [http://linuxwireless.org/download/htc_fw/](http://linuxwireless.org/download/htc_fw/) )got me nowhere!

Persistence will out!

Andrew

---

