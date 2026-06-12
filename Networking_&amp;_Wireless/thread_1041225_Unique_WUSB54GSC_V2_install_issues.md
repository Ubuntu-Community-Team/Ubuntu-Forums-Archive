---
title: "Unique WUSB54GSC V2 install issues"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by T3kn0m0nk3Y on 2009-01-16
Ok, I'm a mid level linux user, but I'm having some real problems getting this wireless usb device to work. It's a WUSB54GSC V2. Just bought it yesterday - it works fine installed on my windows laptop.

I've read and searched quite a bit on the forums/google but can't seem to find the same situation.

I'm running 8.10 desktop
Linux nitrobrute 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

I've installed ndiswrapper:

root@nitrobrute:~# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.27-9-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 

I've tried to follow the various instructions posted on the forums for this but my situation doesn't quite match up.

on my driver cd (win xp/vista) is a /Drivers directory with two sets of drivers. XP_2K/ and Vista/ 

There are compeltely different files than listed anywhere online in both:

root@nitrobrute:/media/cdrom/Drivers# ls -lR
.:
total 4
dr-xr-xr-x 1 root root 2048 2008-08-04 03:06 Vista
dr-xr-xr-x 1 root root 2048 2008-08-04 03:06 XP_2K

./Vista:
total 517
-r-xr-xr-x 1 root root  15184 2008-07-16 10:13 bcmusbdhd.inf
-r-xr-xr-x 1 root root  10681 2008-07-16 20:01 bcmusbdhdlh64.cat
-r-xr-xr-x 1 root root 253944 2008-01-09 00:52 bcmusbdhdlh64.sys
-r-xr-xr-x 1 root root  10677 2008-07-16 20:10 bcmusbdhdlh.cat
-r-xr-xr-x 1 root root 238072 2008-01-09 00:52 bcmusbdhdlh.sys

./XP_2K:
total 227
-r-xr-xr-x 1 root root  10765 2007-11-10 06:48 bcm43xx64.cat
-r-xr-xr-x 1 root root  10695 2008-07-16 18:44 bcm43xx.cat
-r-xr-xr-x 1 root root  11675 2008-07-16 10:13 ndiswdm.inf
-r-xr-xr-x 1 root root 198144 2007-10-10 02:33 ndiswdm.sys


I've also tried putting WUSB54GSC.inf and rndismp.sys files into the ndiswrapper/dir copied from my successfully installed windows dir

When I run ndiswrapper -i on both .inf files. completing the instructions both seem to work. When running ndiswrapper -l the driver shows up. BUT...

When I go the the network control panel, it doesn't show any wireless device present. YES I rebooted after each try. 

I then followed instructions to install ndisgtk. Which worked smooth actually. Again I tried both xp/vista drivers, it looked successful but again no device shows up in network control panel.

The most recent attempt was with the vista driver and here is what ndiswrapper -l outputs:

root@nitrobrute:/media/cdrom/Drivers# ndiswrapper -l
bcmusbdhd : driver installed
	device (1737:0075) present

but as mentioned, still nothing shows up. In ndisgtk, it states "bcmusbdhd hardware present:yes"


I've fully updated the system with "aptitude upgrade" and I'm currently running on wired eth1 connection to my linksys router. I have a laptop sitting next to me connected on the wifi so I know that's solid.

I really need to figure this out as I have a hundred foot cat5 wire snaking through my house and down into my basement just to run updates/install pkgs. But I'm running out of idea's and patience.

thanks! -TM

---

