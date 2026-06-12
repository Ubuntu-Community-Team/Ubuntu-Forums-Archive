---
title: "Roaming DVB Devices"
date: 2008-07-02
forum: Mythbuntu
---

### Post by lerrup on 2008-07-02
I am running latest myth on an up to date 8.04.

I have 3 DVB devices (2 x internal, 1 x USB).  These are multiplexed (?) and so I have 15 virtual tuners.

The problem is that these are assigned to different physical tuners should the computer be rebooted.  For example, USB could be 15-19 and then be rebooted and 15-19 could be assigned to PCI 1 and USB to 20-24.

Does anyone know why this is happening (is this a ubuntu problem with the way that it assigns device number) or is it the way that Mythtv deals with virtual tuners and so needs to be dealt with in a different way?

Any help it stopping the wandering would be good...

---

### Post by ian dobson on 2008-07-03
Hi,

It's not a Myth problem, rather a Linux problem.

When linux boots it looks for the hardware installed and tryes to load the drivers for whatever it found. Due to slight timing differences it could be that TunerA driver loads before or after TunerB driver.

The only thing you can do is use a UDEV rule to create symbolic links from the real dvb devices in /dev then get MythTV to use the symbolic links rather than the "real" devices.

Here a look here [http://ubuntuforums.org/archive/index.php/t-542903.html](http://ubuntuforums.org/archive/index.php/t-542903.html) or [http://stemp.wordpress.com/category/ubuntu-en/page/2/](http://stemp.wordpress.com/category/ubuntu-en/page/2/)

Regards
Ian Dobson

---

