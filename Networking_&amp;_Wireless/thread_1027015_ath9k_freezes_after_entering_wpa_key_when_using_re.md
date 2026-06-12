---
title: "ath9k freezes after entering wpa key when using restricted nv drivers and smp kernel"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by David Mulligan on 2008-12-31
I've been trying to troubleshoot a rather frustrating problem.  Right after entering my WPA key my system would freeze.  No mouse movement and Ctrl-Alt-Fx, Ctrl-Alt-Del, and Ctrl-Alt-Backspace were all not working.  Reset is the only thing I could do.

My relevant setup is:
AMD Athlon 64 X2 4200+
Nvidia 7800GT
DFI Lanparty UT nF4 Ultra-D

I tried switching from network-manager to wicd with no change in behaviour.

After much googling I stumbled upon this [post]("http://www.nvnews.net/vbulletin/showthread.php?t=123993") which led me to this [sticky post]("http://www.nvnews.net/vbulletin/showthread.php?t=58498").  Based on these I came up with the following two work arounds that let me connect without crashes.

#1) Disabled the restricted nvidia drivers.  This worked but was unacceptable for me as I have a dual monitor setup.  I was using version 173 and did not try previous versions.

#2) I added pci=nommconf to my grub kernel parameters.
Update: this is not working anymore.  The failure must be intermittent enough to fool me into thinking it worked. :(

I hope this post is helpful.  Does anyone know if this bug has been logged?  Where do I look?  Where do I submit it?

Thanks!
David

---

### Post by David Mulligan on 2009-01-01
So the nommconf solution was bunk.  I guess the freezing doesn't happen every time and my couple of reboots last night fell into the few times it did work?

I also tried going back to build 93 of the nvidia drivers with no improvement.

I am looking for more ideas!  Obviously giving up my dual monitor setup or one of my cpu cores would not be optimal.

Thanks,
David

---

### Post by PauloVDweller on 2009-01-30
I can confirm there is definitely a problem with ath9k: I bought a Linksys wmp300n wireless adapter a couple of days ago, and while it is correctly detected and it can scan for APs in the surroundings, as soon as it tries to connect with a WPA protected network it hard locks my system as described in the above post. Didn't try with an unprotected network though. 

The problem doesn't concern the connection manager, I tried to connect with network-manager, wicd and terminal and obtained the same result.

I then tried to add backport repositories and update the system, and install the compat-wireless driver as suggested on this topic  [http://bugzilla.kernel.org/show_bug.cgi?id=12110](http://bugzilla.kernel.org/show_bug.cgi?id=12110)   in the linux wireless ath9k bug list, but to no avail; by the way, the problem described there is not the same as mine at all, I just thought those advices could work in my case too.  

It is also to be noted that it is stated in this bug report [http://bugzilla.kernel.org/show_bug.cgi?id=11760](http://bugzilla.kernel.org/show_bug.cgi?id=11760) that a very similar bug (system hanging up a few seconds after boot on Gentoo) should have been fixed.

My sistem spec below

Model: Dell xps 630
Processor: Intel core 2 quad Q9400 
RAM: 3 GB Dual channel DDR2 800 mhz 
Video card: Nvidia geforce 280gtx, driver nvidia-glx-177, kernel modules nvidiafb, nvidia
Network controllers: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02); Linksys WMP300N kernel modules: ath9k , kernel driver: ath9k (the former works, the latter doesn't)
OS: Ubuntu 8.10, kernel version 2.6.27-11-generic

---

### Post by David Mulligan on 2009-01-30
Paulo,

Try removing the nvidia driver.  This work around did work for me however I want to keep my dual monitor support so it was not acceptable as a solution.

Did you say that ath9k as a module did work?  How did you make it work?

David

---

### Post by PauloVDweller on 2009-01-31
David,
I don't really know if the ath9k module works as it should, seeing my problem and yours, but you could try to compile a newer version by following this guide: [http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers) 
That is the guide to install the compat-wireless version of the ath9k driver and kernel module (and many others), directly from the project site. It's easy enough, and if you are unsatisfied by the changes, you can quicly uninstall the thing as explained there. 

Also, in this bug report discussion ([http://bugzilla.kernel.org/show_bug.cgi?id=12110](http://bugzilla.kernel.org/show_bug.cgi?id=12110)) emerges that there are other ways to upgrade (and hopefully get to work) the ath9k driver, such as upgrading the whole kernel. In fact, the module and the drivers already are integrated in the newest kernel versions (>=2.6.27), and it looks like they are constantly getting upgraded, the new versions being released within kernel updates. In the related link you will find the information I reported and also a guide to update the kernel to the newer version, just look in the replies.

You could try one of these two ways as well as both, as I did, but I have to say that didn't change a thing in my case; maybe I did something wrong, but the instructions are simple enough and everything went fine when I followed them, so I dont think that is the case. 

As for the nvidia drivers, I will try to uninstall them and post the results, but I'm a bit skeptical on that: I'm not an expert at all, but why the graphic drivers should interfere with the network adapter ones? Still, there are so many things I don't know, so it's worth a try.

Until we meet again, farewell.

---

### Post by David Mulligan on 2009-01-31
> **PauloVDweller said:**
> David,
I don't really know if the ath9k module works as it should, seeing my problem and yours, but you could try to compile a newer version by following this guide: [http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers) 
That is the guide to install the compat-wireless version of the ath9k driver and kernel module (and many others), directly from the project site. It's easy enough, and if you are unsatisfied by the changes, you can quicly uninstall the thing as explained there. 

As for the nvidia drivers, I will try to uninstall them and post the results, but I'm a bit skeptical on that: I'm not an expert at all, but why the graphic drivers should interfere with the network adapter ones? Still, there are so many things I don't know, so it's worth a try.

Until we meet again, farewell.

Paulo,

I am not sure how the nvidia driver interferes with the ath9k driver but it does.  The difference is night and day when not running the nvidia driver.  Uninstalling the nvidia driver can be done from the hardware drivers configuration program at System->Administration.  Click on the currently active nvidia driver and click the deactivate button.  After a reboot you will know if you and I are indeed having the same problem.

I recently remove the wireless card from that computer.  I am using an old wrt54g access point as a bridge running an open source firmware.  It is slow but reliable.  I am happy to leave it this way until I hear of an option that shows promise.

David

---

