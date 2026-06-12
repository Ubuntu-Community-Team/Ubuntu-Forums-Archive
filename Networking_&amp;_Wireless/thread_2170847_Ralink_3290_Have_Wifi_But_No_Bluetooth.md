---
title: "Ralink 3290 Have Wifi But No Bluetooth"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by rittratt on 2013-08-27
I'm having a frustrating problem with my ralink 3290 wifi/bluetooth combo. Wifi works fine out of the box on Ubuntu Gnome 13.04 but today I tried to pair my new bluetooth headphones to find that my bluetooth device was not found on the laptop! lspci shows 
```
02:00.1 Blueooth: Ralink corp. RT3290 Bluetooth
```

but when I tried hcitool scan, as suggested by another post about this particular model, I get
```
Device is not available: No such device
```

I'm not sure what I'm missing or how to go about fixing this. Any ideas are greatly appreciate
 
=]

---

### Post by theperfectpunk on 2013-09-07
There are no drivers available for Ubuntu 13.04 LTS at the present due to upgraded kernel, which the driver no longer supports. However, you can downgrade to Ubuntu 12.04 LTS and successfully configure bluetooth and wifi by following these steps : [http://lifeindwarka.blogspot.in/2013/08/setting-up-hp-pavilion-g6-2313ax-on.html](http://lifeindwarka.blogspot.in/2013/08/setting-up-hp-pavilion-g6-2313ax-on.html)

---

### Post by josue-soto1 on 2013-09-23
Hi I had installed 12.04LTS 64 bit.
Drivers for WIFI works fine. However Bluetooth is not detected. 
I had tried solution: Setting Up Wifi and Bluetooth on 12.04 LTS posted previously, but cannot compile in the latest kernel 3.8. 

regards
Josue Soto

---

### Post by jdafoe1 on 2013-10-23
This worked for me on 13.10 64bit (kerrnel 3.11): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721). Comment #44

---

