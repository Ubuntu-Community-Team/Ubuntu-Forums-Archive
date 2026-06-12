---
title: "Aircrack and b43 driver"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by Therax on 2009-07-15
Hi

I need some help with aircrack and and b43 driver.
I need to know how to get it runnig, so if anyone could
help me patch the driver and if theres anything else i should do
to get it working.

I am running Ubuntu 9.04, and BCM4318 with the b43 driver.

Thanks in advanced

---

### Post by Therax on 2009-07-16
Is there anyone that can help me?
I really need to get this working.

---

### Post by Shuttleu on 2009-07-16
> **Therax said:**
> Is there anyone that can help me?
I really need to get this working.
i can use aircrack using backtrack

but could you help me
how did you get your card to work
i have a bcm4318 and it never finds any netrworks in ubuntu but it does in other linux distros

~shut

---

### Post by Therax on 2009-07-17
I followed this guide to get it to work in Ububtu 9.04
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

Hope it helps you.

---

### Post by Debason on 2009-07-17
I have the same driver, made it work through the  			 			[Comprehensive ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847") topic on the top of this forum and needed some time and practice on aircrack to get it working.
I broke wep, needed 3-4 hours to get the data ( slow traffic) but I broke it. For aircrak use this [http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide)
Now it's wpa 's turn, I have all the summer :)
Hope this helps

---

### Post by schef on 2009-07-23
You don't have to pach the driver couse driver is already pached..you just need to disable the default driver in System -> Administration -> Hardware Drivers and then install the original driver from Broadcom webpage..
```
sudo apt-get install b43-fwcutter
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2[FONT=monospace]
[/FONT]tar xjf broadcom-wl-4.150.10.5.tar.bz2[FONT=monospace]
[/FONT]cd broadcom-wl-4.150.10.5/driver[FONT=monospace]
[/FONT]b43-fwcutter -w "/lib/firmware/" wl_apsta_mimo.o
modprobe b43
```This is it. Your card should rename from eth1 to wlan0. And then when you write:```
sudo airmon-ng start wlan0
``` you get this message: > Interface    Chipset        Driver

wlan0        Broadcom    b43 - [phy0]
                (monitor mode enabled on mon0)You can see that mon0 apired.
Now you use Airodump-ng with mon0.

---

