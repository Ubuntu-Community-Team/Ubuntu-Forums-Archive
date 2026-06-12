---
title: "Stay away from Linksys WUSB54GC (1737:0077)"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by inzpektor on 2010-03-21
Hi there.

I read some positive reviews about the Linksys WUSB54GC (1737:0077) wireless USB-adaptor and went out and bought it.

As it turns out there's absolutely zero support for this device on GNU/Linux.  There is no driver for the chipset (RaLink rt3070), except a futile attempt by some probably frustrated WUSB54GC-owners to port the rt2870 dirver to be compatible with rt3070.

I've spent 4 hours on following driver-make recipes to no avail.

Long story short: STAY AWAY FROM LINKSYS WUSB54GC

---

### Post by 666f6f on 2010-03-21
inzpektor great info.. After some similar experiences I have learned my lesson and I try to buy linux friendly equipment..

---

### Post by chili555 on 2010-03-21
I'd rather try to get the staging version of rt3070sta to work with it. I'm reasonably confident that I could.

---

### Post by timmynana on 2010-03-22
i've tried with my very basic knowledge to get rt3070 to work for my sweex 150n and found it fruitless too. Hope a simple solution works itself out

---

### Post by chili555 on 2010-03-23
> **timmynana said:**
> i've tried with my very basic knowledge to get rt3070 to work for my sweex 150n and found it fruitless too. Hope a simple solution works itself outHow would you like to be a test pilot? Please start a new thread and we'll get started.

---

### Post by mankidavu on 2010-05-01
I was able to get it working smoothly with the help of below thread:

[http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)

I heared that in Lucid Lynx also it works fine if we blacklist rt2870 module.

---

### Post by peepingtom on 2010-05-01
There is absolutely nothing wrong with this card, OP is mistaken.

[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

The above solution is excellent, it outlines the right way to have a driver control a device with an unsupported USB Device ID.
Doing only the Udev part after "The solution works? Ok, load the driver at startup" should work, it's an elegant solution. no need to compile a new module.
I'm not sure whether wusb54gc uses rt2870sta or rt3070sta, you can modify that guide to work with rt3070sta though.
Don't forget to substitute the usb dev ID and the model number in that tutorial for your own.



Also try blacklisting as said above. Sorry, I can't test this because I dont have this device.

---

