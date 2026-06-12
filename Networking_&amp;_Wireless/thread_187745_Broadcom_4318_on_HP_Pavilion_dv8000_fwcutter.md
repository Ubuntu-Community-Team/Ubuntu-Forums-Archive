---
title: "Broadcom 4318 on HP Pavilion dv8000: fwcutter?"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by EReckase on 2006-06-03
I've got an HP Pavilion dv8225nr, a laptop with an AMD64 processor, 1 GB of RAM, and a Broadcom 4318 wireless chipset.  I tried using the fwcutter utility on the drivers that I could get from the HP support website, but the version of the driver is 4.10.40.1, from 12/17/2005.  fwcutter complains that the checksum doesn't match and so it can't use that bcmwl5.sys file.  (The highest version of the 4318 drivers that I can see in the fwcutter documentation is 3.100.x.x, so could this be part of the problem?)

I was able to get ndiswrapper working with this card without too much wrangling, but while network-manager-gnome recognizes that there's a nearby wireless network, I can never connect to it.  If I start the network-manager-gnome while the wireless is connected, it indicates that there's no network connection at all, even while I'm surfing and writing this very post!  I don't care if I use the built-in bcm43xx driver or ndiswrapper, but it'd be nice to get network-manager-gnome working (as it was one of the primary reasons I upgraded to Dapper.)  If I can't, I might just blacklist the piece of crap and get a USB network dongle.

---

### Post by ????? on 2006-06-03
Did you try [this howto?](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by EReckase on 2006-06-03
I did try that howto, but an older version of it.  I'll retry and report my results.
](*,)

---

### Post by EReckase on 2006-06-06
After retrying that approach, I was unable to get any wireless network connectivity - while the ndiswrapper method happily allows me to scan for nearby networks, the fwcutter/bcm43xx approach reports that the interface does not support scanning.  I tried a few different firmwares as well.

I'm going to try to use the latest version of fwcutter to see if that works better, but I'm still curious whether or not the ndiswrapper method is compatible with network-manager-gnome.

---

### Post by EReckase on 2006-06-06
The latest fwcutter was able to use my 4.10 firmware for the 4318, but it still was unable to connect to anything...I'm going back to ndiswrapper.

---

