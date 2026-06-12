---
title: "Nook HD does not mont in xfce"
date: 2013-02-06
forum: Multimedia Software
---

### Post by landersohn on 2013-02-06
I have an interesting situation with my Nook HD.
When I configure the NOOK to use PTP and I plug it in running GNOME classic desktop, the device mounts just fine and I can transfer files.
However, when I do same thing while I am running xfce 4.8 nothing happens, the device is not recognized or mounted. However, I can manually mount it with gphotofs.

I am surprised that the desktop seems to make a difference.

If the Nook is set to MTP, it does get mounted when I plug it in under xfce, but I only see an html file, not the real file contents. gmtp works in this case and manual mount with mtpfs  works as well.

Has anybody seen this? I'd really like to mount the Nook in PTP mode and have it show up in thunar when I am running xfce.

I am on ubuntu 12.04, 3.5.0-23 kernel. My xfce is configure to not start GNOME services.
the fuse daemon is running.

---

### Post by eric41 on 2014-01-25
I haven't looked around at setting this up in ptp mode, but there are some tutorials out there to set up a script that will mount this device in mtp mode under 12.04/xfce, though i have found it easier to use gMTP, which is installable from software center.

---

### Post by bookrt on 2014-02-09
I have had the same problem in both LUbuntu 12.04 LTS and XUbuntu 12.04 LTS, and also Mint 16 XFCE. GMTP works in these distributions but feels clunky. However, to my surprise the device works seamlessly wtih Mint 16 Cinnamon (unfortunately Cinnamon was crashing my computer). I would like to know if there is any way of replicating Cinnamon's MTP/Android support within XUbuntu or LUbuntu, or if anyone is having success in other distributions.

---

### Post by bookrt on 2014-02-18
Updating...I upgraded to XUbuntu 13.10 and got the same behavior...HD+ set to MTP would mount but only trash folder and Setup were visible. I solved the problem by installing Nemo file manager through Software Center. Now the HD+ mounts and all files are recognized like any USB device without the need for GMTP.

---

