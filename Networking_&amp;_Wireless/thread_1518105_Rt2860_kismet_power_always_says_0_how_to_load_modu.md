---
title: "Rt2860 kismet power always says 0 how to load module"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by zonemikel on 2010-06-26
Hello everyone

I have a WS- something or other by gigabyte, it has the "ralink rt2860" chipset according to lspci. 

It works well the only problem is in kismet or airodump-ng the power always shows as 0. 

In the kismet.conf i had to set the source to rt2500, it does not seem to like rt2860 or rt2x00. 

In airodump-ng it always says "chipset: ralink 2560pci" and "driver:rt2500" 

Is there any way i can use the rt2x00 drivers, would they allow for more things ? Any idea what i'm doing wrong ? 

Whats funny is that network manager can see the signal strenght of all the sources. this is annoying the hell out of me

---

### Post by zonemikel on 2010-06-26
bump, i'm still here

I did load the latest version of kismet 2010 rc 4 (i think). It wont start up right it says it cant autodetect the driver for my card and the kismet.conf isnt the same so i'm not sure how to manually add my driver. 

In the readme it says something about using the kernel driver is better  ... well i'll quote it 
> 
      There are 2 drivers for the RT28xx chipsets.  The in-kernel driver
      available as of Linux-2.6.31 works properly with Kismet.  This is by
      far the preferred driver to use.  Be sure to enable the RT28xx driver
      in the wireless drivers section, NOT the staging driver.  The staging
      driver is not mac80211 based and will not necessarily behave.

      The out-of-kernel driver does not conform to mac80211 controls.
      This driver also cannot be auto-detected (they don't provide a valid 
      identifier in /sys) so the driver type mus be manually specified with 
      'type=rt2870sta' on the source line.



I have no idea where the "wireless drivers section" is though, thats the only mention of it in the readme. 

Since my device is named "ra0" doesnt that mean its a out of kernel driver ? and modprobe reviels i'm using rt2860sta i think

thanks for any help

---

### Post by zonemikel on 2010-06-27
Help  ?

---

