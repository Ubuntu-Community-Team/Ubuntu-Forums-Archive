---
title: "Vmc blind !! Doesn't see Option Icon 431 (T-Mobile USB Stick 530)"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by Alijools on 2010-06-15
[SIZE=3][FONT=Calibri]... probably not vmc’s fault but mine [/FONT][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][FONT=Calibri] [/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Anyway, hi all, I’m running a Samsung N140 and I’m trying to connect the T-Mobile 530 dongle (Option Icon 431). I’m a complete newbie to Linux (and quite inexperienced with computers in general), just switched from Windows 7 to Ubuntu 9.10. I installed usb_modeswitch, ozerocdoff and then vmc, following the instructions on Betavine and used the config for the Vodafone K3760 (same modem I believe?).  All ok so far.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Now when I start vmc, it doesn’t recognise the modem ! I’ve tried different things without any luck and don’t really know what to look at now. I’ve seen that many users have the same problem, but unfortunately that last step is not as well documented as the installation of the packages, etc...[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Usb_modeswitch runs ok and the modem is recognised (last line)[/SIZE][/FONT]
[FONT=Courier New]root@julien-laptop:/home/julien# lsusb[/FONT]
[FONT=Courier New]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 004 Device 002: ID 0a5c:2151 Broadcom Corp. [/FONT]
[FONT=Courier New]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 001 Device 004: ID 0ac8:c33f Z-Star Microelectronics Corp. [/FONT]
[FONT=Courier New]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Courier New]Bus 001 Device 002: ID 0af0:7501 Option [/FONT]
[FONT=Courier New] [/FONT]
[FONT=Calibri][SIZE=3]The ports have been successfully created[/SIZE][/FONT]
[FONT=Courier New]root@julien-laptop:/home/julien# ls -l /dev/ttyUSB*[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 1 2010-06-15 15:06 /dev/ttyUSB1[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 2 2010-06-15 15:06 /dev/ttyUSB2[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 3 2010-06-15 15:06 /dev/ttyUSB3[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 4 2010-06-15 15:06 /dev/ttyUSB4[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 5 2010-06-15 15:06 /dev/ttyUSB5[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 6 2010-06-15 15:06 /dev/ttyUSB6[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 7 2010-06-15 15:06 /dev/ttyUSB7[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 8 2010-06-15 15:06 /dev/ttyUSB8[/FONT]
[FONT=Courier New]crw-rw---- 1 root dialout 188, 9 2010-06-15 15:06 /dev/ttyUSB9[/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The dmesg is quite longso I won’t paste it here but just attach it. A few lines look suspicious like[/SIZE][/FONT]
[FONT=Courier New][   16.437034] generic ttyUSB0: generic converter now disconnected from ttyUSB0[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Calibri][SIZE=3]Apologies for being one of the hundreds asking a maybe simple question but any help will be very appreciated !! [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]Thanks in advance[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

