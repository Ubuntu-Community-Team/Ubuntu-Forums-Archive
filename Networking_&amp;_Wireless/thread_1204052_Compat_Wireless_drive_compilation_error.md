---
title: "Compat Wireless drive compilation error"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Euphorion on 2009-07-04
Hallo

I have Jaunty in English on a Fujitsu Laptop with a D-Link DWA-160 (rev A) WLan Stick. This Stick uses the ar9170 Chip Set. The Compat-Wireless Drivers support this Chip Set. I wanted to compile the latest compat-wireless drivers (compat-wireless-2009-07-04). After issuing the make comand I received the following errors.


```
peter@peter-laptop:~/compat-wireless-2009-07-04$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.28-13-generic/build M=/home/peter/compat-wireless-2009-07-04 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  LD      /home/peter/compat-wireless-2009-07-04/drivers/misc/eeprom/built-in.o
  CC [M]  /home/peter/compat-wireless-2009-07-04/drivers/misc/eeprom/eeprom_93cx6.o
In file included from <command-line>:0:
/home/peter/compat-wireless-2009-07-04/include/net/compat.h:123: error: redefinition of ‘skb_queue_is_last’
include/linux/skbuff.h:477: error: previous definition of ‘skb_queue_is_last’ was here
/home/peter/compat-wireless-2009-07-04/include/net/compat.h:137: error: redefinition of ‘skb_queue_next’
include/linux/skbuff.h:491: error: previous definition of ‘skb_queue_next’ was here
make[3]: *** [/home/peter/compat-wireless-2009-07-04/drivers/misc/eeprom/eeprom_93cx6.o] Error 1
make[2]: *** [/home/peter/compat-wireless-2009-07-04/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/peter/compat-wireless-2009-07-04] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [modules] Error 2
```
Unfortunatly my computer knowledge is not sufficient in order to resolve these errors. Would be of great help if any one could help me out.
Thanks in advance

---

### Post by trvrlol on 2009-07-06
I am receiving the same errors and any help in fixing it would be much appreciated!

---

### Post by Euphorion on 2009-07-12
I have posted my problems on the Wireless for Linux support page, but have received to date no reply. There it seems that developers are taken more seriously. But what good is a mass of development activity when the normal user cannot install the drivers as described.

[http://thread.gmane.org/gmane.linux.kernel.wireless.general](http://thread.gmane.org/gmane.linux.kernel.wireless.general)

Will have to wait until the next Kernel offers better support.

---

### Post by rashwan on 2009-07-22
try to use the older one , that should work

lemme know the results please.

---

### Post by Euphorion on 2009-07-23
Hallo Rashwan

I must admit that I have not tried earlier Drivers. During my research in the German Ubuntu Forum I found a Post from a very knowledgeable user called Elektronenblitz63 under following link

 [http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

The "conversation" is in German but the instructions (Terminal Commands) are in English. He has as far as I can tell, created a how to install based on a earlier version. He seems to have simplified a few things in that unnecessary items have been removed. I must say that it compiled first time with out a hitch and it works. The only slight irritating thing is that no LEDs light up or flash, so after driver compile, install and plug in of the stick, you think that it is not working or nothing has happened, but it in reality it has.

I have been using this regularly for some weeks now and it works and is stable. According to my measurements with Netstumbler and a wlan info tool under windows, the in Ubuntu reported signal strength and bit rate are lower than actual. The actual signal strength is higher as well as the bit rate. In Ubuntu if I place the stick next to my router (transmitter) the max signal strength shown is 46%, in windows with the same configuration I have 100% (in Windows I am using the latest D-Link driver.

Hope this helps you and may be others

---

