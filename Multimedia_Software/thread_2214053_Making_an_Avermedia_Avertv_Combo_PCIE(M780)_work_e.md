---
title: "Making an Avermedia Avertv Combo PCIE(M780) work easy ATSC tuner"
date: 2014-03-30
forum: Multimedia Software
---

### Post by sdowney717 on 2014-03-30
My second post makes this first one superfluous.:KS

You need firmware file ngene_15.fw copied into /lib/firmware
I uploaded this so it will be easy to find

ngene_17.fw  ngene_18.fw are there but do not work, why?

It took some work finding it on the web. This page has a working link to that firmware
[http://forums.opensuse.org/showthread.php/483812-cannot-load-firmware-file-ngene_15-fw](http://forums.opensuse.org/showthread.php/483812-cannot-load-firmware-file-ngene_15-fw)

Link
[http://l4m-daten.de/downloads/firmware/dvb-s2/linux/all/ngene_15.fw](http://l4m-daten.de/downloads/firmware/dvb-s2/linux/all/ngene_15.fw)

here it is loaded
```
scott@scott-P5QC:~$ dmesg | egrep -i '(firmware|atsc|dvb)'
[   14.492485] ngene: Found Aver M780 ATSC/QAM-B
[   14.567009] ngene: Loading firmware file ngene_15.fw.
[   14.616274] DVB: registering new adapter (nGene)
[   14.616279] ngene 0000:04:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   15.545500] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
scott@scott-P5QC:~$ 
```

without ngene_15.fw in the folder, nothing loads

```
scott@scott-P5QC:~$ dmesg | egrep -i '(firmware|atsc|dvb)'
[   14.499905] ngene: Found Aver M780 ATSC/QAM-B
[   14.682950] ngene 0000:04:00.0: Direct firmware load failed with error -2
[   14.875974] ngene: Could not load firmware file ngene_15.fw.
[   15.567897] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
scott@scott-P5QC:~$ 
```

I found MeTV works well for ATSC and this tuner.
Here is a link discussing how this should be there, but I dont know why it is not.

[https://www.kernellabs.com/blog/?p=1418](https://www.kernellabs.com/blog/?p=1418)
> As long as you’re running a recent Linux distribution you should be fine. Support for the device was merged upstream months ago.

---

### Post by sdowney717 on 2014-03-30
[http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist)

This file shows up in the non free firmware list, so I suppose that is why it is not in the default installs.

scott@scott-P5QC:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
scott@scott-P5QC:~$ 

I found that 
sudo apt-get install linux-firmware-nonfree
will install it
It shows in the installed files list, so easy to install

---

