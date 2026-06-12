---
title: "Fresh Install Doesn't Give Driver Options!!!"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Topher88 on 2009-11-11
Hi!  I've been running Ubuntu Studio for the past three or four months, and I decided that I just wanted regular Ubuntu, so I totally deleted the Studio partition (and backed up my files, of coarse) and did a fresh install of regular Ubuntu 9.10.  After the installation was complete, I found that it did not give me the option to use a proprietary wireless card driver like both my previous version of Ubuntu and the LiveCD version does, so I am left without internet until I can attain said driver(s) and get Ubuntu to recognize them and let me use them.  What do I need to do?  (I'm online in my Vista partition at the moment).

Thanks!

---

### Post by efflandt on 2009-11-11
What type of wireless device (make/model or sudo lspci -v info related to it).  If System, Administration, Hardware Drivers does not show a driver for it (which you may need to Enable), you may need to install a restricted package that supports your device with proprietary driver.

Even on a live 8.10 install iso being run from USB, I had to go go Hardware Drivers, Enable the driver, reboot, and then figure out which module to modprobe, for Broadcom wireless on a Dell laptop.  Not sure if that is more automatic on an installed system.

---

### Post by Topher88 on 2009-11-11
> **efflandt said:**
> What type of wireless device (make/model or sudo lspci -v info related to it).  If System, Administration, Hardware Drivers does not show a driver for it (which you may need to Enable), you may need to install a restricted package that supports your device with proprietary driver.

Even on a live 8.10 install iso being run from USB, I had to go go Hardware Drivers, Enable the driver, reboot, and then figure out which module to modprobe, for Broadcom wireless on a Dell laptop.  Not sure if that is more automatic on an installed system.

Thanks for responding.  Here is a screenshot:

[ATTACH]135695[/ATTACH]

The left shows the section of text (I think) that corresponds to the make, model, etc. of my wireless card from running the lspci -v command, and the right shows the empty proprietary drivers box that used to display the appropriate driver for me to use, but now doesn't after the fresh install, for whatever reason.

Thanks!

---

### Post by Topher88 on 2009-11-11
Hey!  Thanks for your help, but I found [this thread]("http://ubuntuforums.org/showthread.php?p=8296060#post8296060") which said to try running the command sudo apt-get install bcmwl-kernel-source, and that seems to have given me back my drivers in Hardware Drivers!  Thanks anyway, though.

---

### Post by Bob33 on 2009-11-12
Hi Guys,

I've got a similar problem with an Inspiron Mini 12. The liveCD enabled me to activate the broadcom driver for the wireless (Broadcom TSA driver) and everything worked fine. Then 
I installed it along windowsXp on the hard drive. 
When booted up from the hard drive I don't have the proprietary driver any more. Then I've tried to plug an ethernet cable but it doesn't work either. 
Now I cannot connect to the Internet and can't get any driver. I'm a bit stuck. 
Thanks for your help! :D

---

