---
title: "Mini 9 and wireless on Maverick"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by walker98t on 2010-10-30
This post is the result of searching through the forums, taking bits and pieces from several posts, and a lot of trial and error. Many thanks to anyone and everyone who provided information in their posts. I apologize for not giving links to all the original pages; I simply can't remember all the pages I've stolen from. By the time I finally solved my wireless problem, I had followed the how-to's on several web pages, so I took the "take no prisoners" approach and in step 1 tried to wipe everything I had previously done before trying again. It would be great if one of the many Linux gurus out there would rewrite this, modifying procedures and making corrections. I'm sure some of the steps are unnecessary and there are undoubtedly better ways of doing those steps that are.

I have a Dell Mini 9. I've upgraded the BIOS to version A04, but I don't think it matters what BIOS version you have. The Mini 9 has the infamous Broadcom bcmwl 4312 wireless card. I started with a new install of Ubuntu 10.10 and followed the recommended procedure for setting up wireless. As many of you have discovered, the recommended procedure doesn't always work for the Mini 9. Here's what I did to get wireless working. This solution is specific to the Dell Mini 9 with the bcmwl 4312 card. It may work for other configurations, but there's no guarantee.

The procedure below assumes you have a working wired connection to the 'net. 

Issue 1: Ubuntu mis-identified the broadcom card, and as a result, Synaptic and the restricted driver app. didn't install the proper firmware. (The first link below provides the details.) Using Synaptic, completely remove bcmwl-kernel-source, broadcom-sta-common, broadcom-sta-source, b43-fwcutter, and bcmwl-modaliases. Do NOT remove bcm5700-source. Then in a terminal ( sudo apt-get install firmware-b43-lpphy-installer ) to download and install the correct version. Synaptic will also properly reinstall some of the other broadcom packages.

Issue 2: Once you have the firmware installed, go to restricted drivers in the Ubuntu menu and activate the STA driver. Ubuntu will download and install the correct driver for your firmware.

You may have to reboot, but you should now have working wireless. If not:

Issue 3: Some people have reported problems with Gnome Network Manager and ad hoc wireless connections. I've had problems configuring connections with GNM in past versions of Ubuntu so I prefer to use Wicd. It can be installed through  Synaptic. If you leave Network Manager installed and use Wicd, you may find you can detect wireless networks, but can't connect, or Wicd says you're connected but you can't get on-line. If so, go to Synaptic and completely remove the packages network-manager, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome. and mark Wicd for re-installation. I had to reboot at this point, and afterward everything functioned as it should.

Issue 4: I haven't had this problem, but some users with laptops have reported that the Gnome power management app interferes with wireless functioning. If, after all of the above you still can't connect or drop connections sporadically, try this command from the terminal:  ( sudo iwconfig eth1 power off ). This will turn off power management for the wireless card only.

Wireless now works on my Mini 9. The only problem I've had is sometimes when I boot, wireless is disabled; it happens maybe one out of five boots, and a reboot brings it back. I suspect it has to do with loading modules "out of order". Should be an easy fix when I finally take the time to look into it.

In no particular order, here are some of the links I used while working on this problem:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[http://ubuntuforums.org/showthread.php?t=1598620&highlight=10.10+bcmwl&page=2](http://ubuntuforums.org/showthread.php?t=1598620&highlight=10.10+bcmwl&page=2)
[http://ubuntuforums.org/showthread.php?t=1568403&highlight=wicd+vs+network-manager](http://ubuntuforums.org/showthread.php?t=1568403&highlight=wicd+vs+network-manager)
[http://ubuntuforums.org/showthread.php?t=1601484&highlight=turn+off+power+management](http://ubuntuforums.org/showthread.php?t=1601484&highlight=turn+off+power+management)

---

