---
title: "BCM4306 is Not Working"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by Izzard on 2009-11-16
Ok, I know, it is like two thousand threads about broadcom chip. I'm using Ubuntu since 7.10 with no problem. Brodcom chip is detected, I go to Hardware Drivers>Searching>Activate Broadcom 43>Downloading>Installing>Reboot. Worked like a charm till 9.10 version.
I went on the same route, but after restart no internet. I downloaded fwcutter but no luck.

My wireless chip is  Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) [14e4:4320]

---

### Post by Izzard on 2009-11-17
I don't want to be annoying, but please. Anyone?

---

### Post by puppywhacker on 2009-11-17
I have an old type mac mini with the same chip 4e4:4320 (rev 03). I always used the b43 driver, not the ndiswrapper. I followed the fwcutter instructions from their website.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I had frequent network drops, but I increased some timer in the mlme.c and recompiled the module again. it's still running 9.04, didn't have time to upgrade

---

### Post by Mahngiel on 2009-11-18
**Step 1**:
Use version 012 of b43-fwcutter to your /home folder. 
Download, extract the b43-fwcutter tarball and build it


Code:
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2tar](http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2tar) 
xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..
[B]
Step 2[/B]:
Use version 4.150.10.5 of Broadcom's proprietary driver.  This is for Rev 03 of the driver.
Download and extract the firmware from this driver tarball:

Code:
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2tar](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2tar) 
xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
 
**Step 3:**
Restart your sysytem and update the proprietary drivers.  Have Fun!

---

### Post by jtwm0677 on 2009-11-22
> **Mahngiel said:**
> **Step 1**:
Use version 012 of b43-fwcutter to your /home folder. 
Download, extract the b43-fwcutter tarball and build it


Code:
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2tar](http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2tar) 
xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..
[B]
Step 2[/B]:
Use version 4.150.10.5 of Broadcom's proprietary driver.  This is for Rev 03 of the driver.
Download and extract the firmware from this driver tarball:

Code:
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2tar](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2tar) 
xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
 
**Step 3:**
Restart your sysytem and update the proprietary drivers.  Have Fun!

I've tried this fix, along with several others, but the only way i can get my bcm 4306 to work is using ndiswrapper. I need full functionality out of my wireless card, and have seen in other posts that it is very possible to achieve this. Someone please advise. i've tried this solution, along with many others, but the link to the second file in this one comes back 404: Not Found.. Please help.. Thanks in advance

---

### Post by bkratz on 2009-11-22
> **jtwm0677 said:**
> I've tried this fix, along with several others, but the only way i can get my bcm 4306 to work is using ndiswrapper. I need full functionality out of my wireless card, and have seen in other posts that it is very possible to achieve this. Someone please advise. i've tried this solution, along with many others, but the link to the second file in this one comes back 404: Not Found.. Please help.. Thanks in advance



Have you ever seen this listing?

[http://ubuntuforums.org/showthread.php?t=201902&highlight=4306&page=86](http://ubuntuforums.org/showthread.php?t=201902&highlight=4306&page=86)

It seems  like the last few pages are relatively recent.

---

### Post by jtwm0677 on 2009-11-22
Thanks, but it seems that the post you sent me too is for instructions for using ndiswrapper, which I can already use. What I need is to be able to use drivers OTHER than the windows based drivers that ndiswrapper uses. I have absolutely NO drivers showing in the proprietary driver list, and have seen elsewhere that there are ubuntu drivers for the bcm43xx, that do indeed show in the proprietary driver list. any other suggestions would be greatly appreciated. I'm VERY new to ubuntu, but have used windows since 3.1 many years ago, so many things in ubuntu are very strange to me.

---

### Post by CoolDreamZ on 2009-11-28
This thread may have a solution to your problem:

[http://ubuntuforums.org/showthread.php?t=1312603]("http://ubuntuforums.org/showthread.php?t=1312603")

---

