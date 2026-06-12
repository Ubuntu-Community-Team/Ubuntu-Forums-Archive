---
title: "Display settings destroyed after today's kernel update"
date: 2008-08-26
forum: Multimedia Software
---

### Post by sashi3 on 2008-08-26
I have an AMD based setup using nvidia 8800GT running Ubuntu 8.0.4. Everything was working great and I had compiz effects enabled via the restricted nvidia driver. My display resolution is 1920x1200 and screen resolution was set at that.

This morning I saw update notifications from Update Manager and downloaded 4 updates which I guess made changes to the kernel. After the update happened by resolution got set to 640x480 without any other resolution options for me to choose from. So I was looking around the forum posts and tried a number of things.

I noticed my xorg.conf file was really short without any resolution modes specified. Unfortunately I had not created a backup of the previous xorgs.conf file. I set the monitor size using displayconfig-gtk. 


Then I noticed I was only allowed to go upto 1600x resolution.
I also noticed the nvidia restricted driver was not enabled. I then enabled it. Even then it was not giving me the 1900 resolution. But at some point I was able to get that choice, may be after using displayconfig-gtk again. I dont remember exactly. But choosing 1900 would cause the desktop to extend beyond the monitor screen! 


So after reading some threads here I took an attempt at using the latest linux drivers from NVIDIA and went through the "sudo sh NVIDIA***" command. 

Did not help anything. I still get the low resolution monitor dialog prompt after system boot and  if i change the monitor resolution to high during that prompt then it seems to boot ok in high res. But as soon as I log in things go haywire I get bunch horizontal stipes across the screen that prevents me from seeing anything.

desperately looking for some suggestions about how to revert back to working configuration.


d

---

### Post by sashi3 on 2008-08-27
Wanted to give an update. I have been having difficulty understanding the relationship between the restricted nvidia driver that comes from repository and the one that I downloaded from nvidia (version 173.14.12).

I did a reinstall of the the driver from Nvidia and tried this

DISABLED_MODULES="nv"

setting in /etc/default/linux-restricted-modules-common

which disabled the restricted module. So now I do get the full
resolution. However, I cannot enable compiz with the Nvidia
driver. I ran the sanity check test with the Nvidia installer
and it says everything is ok.

Can somebody explain me (or point me a post) about what are the
difference between these two drivers and whether compiz should
be working with the driver from Nvidia?

As I said earlier, till yesterday I was just using the restricted 
module that came from repository and everything was working fine.

many thanks

---

### Post by sashi3 on 2008-08-27
Based on something I saw on compiz-fusion forum applied these

nvidia-xconfig --composite
nvidia-xconfig --allow-glx-with-composite
nvidia-xconfig --render-accel
nvidia-xconfig --add-argb-glx-visuals

compiz seems to be enabled. But the 1920x1200 desktop setting now extends beyond the monitor screen! 

:-(

---

### Post by sashi3 on 2008-08-27
Sorry for continuing to talk to myself. May be it will help sombody to save some lost time :) 

It seems after I changed the scan frequency to 58Hz from 50Hz (which it was set at) in the screen resolution preference dialog, things are looking much better. I have an Acer P241W monitor.

thanks

---

### Post by markbuntu on 2008-08-27
Some kernel updates do not load the kernel modules for nvidia and ati drivers on some machines so the drivers fail. This is especially true for those who have the latest drivers directly from nvidia and ati. You can try reloading the correct kernel modules when this happens... but you may have to remove the driver completely and reinstall it.

---

### Post by slanbarn on 2008-08-27
Have the same problem...

after a reboot, the xorg log says that the nvidia glx extension can not be loaded(can not be found) wich results in a low screen desktop, however a reinstall of the driver fixes the problem, and everything works as it should...

Guess these issues are related, even tho the thread-starter seemed to have slightly different issues, but same result...

---

### Post by sashi3 on 2008-08-27
Hi slanbarn

what did you do to reinstall the driver ? did you download and install from NVIDIA's web site ? Or did you disable/enable the restricted module in the HW driver control panel ? or something else ?

I tried the latter approach first since before now I had not used any driver directly from Nvidia. and did not seem to help.

---

### Post by slanbarn on 2008-08-28
> **sashi3 said:**
> Hi slanbarn

what did you do to reinstall the driver ? did you download and install from NVIDIA's web site ? Or did you disable/enable the restricted module in the HW driver control panel ? or something else ?

I tried the latter approach first since before now I had not used any driver directly from Nvidia. and did not seem to help.

I use the NVIDIA-***.run shell script from nvidias site, the installer removes and reinstalls the driver if it is existent, wich it is! the nvidia install scripts see that the driver is already installed, but xorg.log says "cant find nvidia glx extension"....

---

