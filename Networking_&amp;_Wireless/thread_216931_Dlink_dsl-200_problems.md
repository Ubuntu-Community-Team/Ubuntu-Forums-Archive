---
title: "Dlink dsl-200 problems"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by razard on 2006-07-16
I have that modem [http://eciadsl.flashtux.org/modems.php?modem=65]("http://eciadsl.flashtux.org/modems.php?modem=65")
i was trying to start. I was downloaded this files:
usermode :
[http://eciadsl.flashtux.org/download/eciadsl-usermode-0.11.tar.gz](http://eciadsl.flashtux.org/download/eciadsl-usermode-0.11.tar.gz)

Synch files:
[http://eciadsl.flashtux.org/download/eciadsl-synch_bin.tar.bz2](http://eciadsl.flashtux.org/download/eciadsl-synch_bin.tar.bz2)

pppoe source:
[http://frankandjacq.com/ubuntuguide/rp-pppoe-3.8.tar.gz](http://frankandjacq.com/ubuntuguide/rp-pppoe-3.8.tar.gz)

1. I installed rp-pppoe program. I puted all information abaut my account dns and other. What device to chooce i don't know and puted the default eth0. but i think it is wrong, really I don't know.

2. After rp-pppoe I extracted eciadsl-usermode-0.11.tar.gz and installed it. after it I extracted eciadsl-synch_bin.tar.bz2 and copied gs7470_synch04.bin file to /etc/eciadsl/. I try and other gs7470_synch**.bin files dupported by my modem but it don't work.

3 Then I write some commands in console I got that :
razard@razard-desktop:~$ sudo eciadsl-start
Password:

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

ERROR: modem not found
razard@razard-desktop:~$


razard@razard-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 
Optical Scroller Mouse
Bus 001 Device 002: ID 2001:5100 D-Link Corp. [hex]
Bus 001 Device 001: ID 0000:0000


razard@razard-desktop:~$ sudo eciadsl-doctor
You are using linux kernel version 2.6.15-23-386
Support for USB is OK
Preliminary USB device filesystem is OK
dabusb module is not loaded: OK
UHCI support is not needed
OHCI support is OK
/dev/ppp is OK
HDLC support is OK
HDLC support is OK (no bug)
I cannot find your ADSL modem: Fatal
 
What ubuntu members can suggest for beginner? I don't that to do ](*,) I already tryed it manual [http://eciadsl.flashtux.org/doc/eciadsl_install_en.txt]("http://eciadsl.flashtux.org/doc/eciadsl_install_en.txt")

---

### Post by morequarky on 2006-07-16
Have you read this?  Might help.  Might now.

USB is a tough monster.

Good luck.

hope you get Ethernet in the future.

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

---

