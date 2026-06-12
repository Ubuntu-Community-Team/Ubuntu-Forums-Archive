---
title: "ASUS USB Wireless - iwconfig returns nothing"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by bjornbjorn on 2005-12-15
Hi people! I'm trying to get my ASUS WL-167g USB wireless adapter to work with Breezy.

I found my usb device in this list:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

> Card: ASUS WL-167G

    * Chipset: RT2500USB
    * usbid: **0b05:1706**
    * Driver: 2.00.01.0000 ([http://www.ralinktech.com](http://www.ralinktech.com))
    * Other: Mandriva LE 2005 (kernel-2.6.11), ndiswrapper-1.2rc1. Must install Kernel-Source 2.6-2.6.11-6mdk to compile ndiswrapper, use "ndiswrapper -d 0b05:1706 rt2500usb"... to get Hardware present, works at 54 Mb Great !! No need to recompile kernel, it just works fine. Thanks, Thanks !! Well done. 

if I do an lsusb I see that the usbid is the same as the one mentioned above:
> bjorn@servbuntu:~/drivers/usb$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID **0b05:1706** ASUSTek Computer, Inc.
Bus 001 Device 001: ID 0000:0000


So, I installed ndiswrapper-utils and got the XP drivers (rt2500usb.inf  rt2500usb.sys).

I then ran:
ndiswrapper -i rt2500usb.inf
modprobe ndiswrapper

if I do an "iwconfig" this is listed:
> bjorn@servbuntu:~/drivers/usb$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.


.. so it doesn't find it at all ... I also tried adding it manually to /etc/networking/interfaces with no luck.

my kernel: Linux servbuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

anyone know what the problem might be?

- bjorn

---

### Post by Lambert on 2005-12-15
IF you run iwconfig and get no output then the driver isn't working.

What do you get running ndiswrapper -l (that is a lower case L)

Where did you get the drivers from?

---

### Post by bjornbjorn on 2005-12-15
> bjorn@servbuntu:~/drivers/usb$ ndiswrapper -l
Installed ndis drivers:
rt2500usb       driver present, hardware present


I got the drivers from the ASUS homepage.

- bjorn

---

### Post by bjornbjorn on 2005-12-16
*bump* .. so it seems the driver is working - since it says "rt2500usb driver present, hardware present" .. 

clues anyone? I'd "love" a list of things to check ;)

- bjorn

---

### Post by diantel on 2005-12-16
You have to activate your interface before you can use it

See if this works:
 sudo  ifconfig rausb0 up
and then: sudo  iwconfig rausb0
(If this not works probe with wlan0 instead of rausb0)

Why you use the windows drivers when you have linux native drivers that works much better. :). You can use the card in monitor mode and do a lot of thigs.
 
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

You can download it here: [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

---

### Post by diantel on 2005-12-16
I've found this page:
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

Herere says:
Ubuntu 5.10 (Breezy Badger) now supports the RT2500 Out of the box. You should be able to plug in the card, go to menu System->Administration->Networking Select the card, click properties, enter ESSID, WEP Key (if appropriate). Click OK, click activate.

So... You don't need ndiswrapper.

---

### Post by bjornbjorn on 2005-12-16
ok, cheers diantel, I'll try this later tonight ..

I've installed ubuntu in server mode btw - so I need to be able to do it all in shell. Shouldn't be a problem I guess..

- bjorn

---

