---
title: "ndiswrapper stuck in infinate loop trying to install wnda3100v2"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by T.Rebel on 2010-06-22
ok, so im trying to get my wireless up using a netgear wnda3100v2 dual band. ive followed the directions here: [http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708) and when i install the inf file ndisgtk stops responding. when i go to the terminal and try to list the drivers installed ndiswrapper appears to be stuck in an infinate loop ( i must press control-z to kill process). even more confusing, when i try to remove the driver using ndiswrapper, i get a message saying it is not installed. this is where its confusing, if i try to install the driver from the terminal, i get a message saying its already installed.... what gives? 

from this point out ndiswrapper becomes completely useless and the only way i have been able to get it to work again is by formatting my HD and reinstall my distro.

the distro i am using is ubuntu 10.04 64 bit 
ndiswrapper-1.56

any ideas on how to get this working?

---

### Post by jwferk on 2010-08-25
Identical problem here.  WNDA3100v2 on Mint 9 Ubuntu version (I'm on Mint because I thought it might be a problem specific to Ubuntu 10.04 so I deleted that OS and install Mint as a trial).

Makes no difference if I use the Synaptic ndiswrapper package or build the more current version (1.56) from source.

It has been driving me absolutely nuts for a couple of days.

I've tried installing software versions 1.0, 1.1, 1.2, 1.6 and 1.7 for the WNDA3100v2.  bcmwlhigh5 installs with ndis but not bcmwkhigh6.  ndis tells me the driver bc-5 installed properly and correctly identifies the USB wireless.  If I reboot the system crashes and I need to open in failsafe and blacklist the ndiswrapper kernel module so it won't load at boot. Then I can reboot with no problem

---

### Post by step5 on 2011-01-29
Few minutes ago i tried to install my wnda3100v2 with 
- ndiswrapper 1.56-3 
and 
- kernel 2.6.35-23-generic in maverick.
I used the driver v.1.0 because all success stories i read are based on this version.

didn't work for me :-(

i opened up ndisgtk and chose the inf file. 
install success.
closed ndisgtk. 
connected the wnda3100v2 stick.
tried to open up ndisgtk again - no chance it stuck
killed the process and tried lsusb - no chance - it stuck
removed the stick and tried to open ndisgtk - it stuck again

finally i removed ndiswrapper via 
sudo apt-get purge ndisgtk ndiswrapper-common ndiswrapper-utils-1.9 -f
because a restart without removing it would kill the system...

i hope it will work someday...

---

