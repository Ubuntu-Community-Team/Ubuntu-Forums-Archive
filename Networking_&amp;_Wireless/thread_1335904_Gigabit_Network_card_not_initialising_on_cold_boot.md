---
title: "Gigabit Network card not initialising on cold boot"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by Thaimite on 2009-11-23
HELP
I am fairly new to Linux, but very experienced with Windows.
My machine has 2 network cards. One on board 1oo/Mb and a PCI gigabit ethernet card.
My problem is that the Gigabit card fails to initialise from a cold boot.  

After the power has been removed from the power socket I have to boot in to windows to initialise the card, and then reboot in to Ubuntu 9.10 where the card is detected and works fine with great transfer speeds.  
I can shut down and restart any number of times without problem until the power cord is removed from the power supply and I have to go through the 'boot to windows' procedure first to intialise the card again.
Being fairly new to Linux I have no idea how to even start to diagnose this problem
According to lifw (when the card is working) the card is detected as a RTL-8169 Gigabit Ethernet. which seems to be correct.
I am using the standard drivers.
Please help as this machine is intended to be a remote operated headless server for remote access while I am away.

---

### Post by chili555 on 2009-11-24
I noticed this: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448) and, especially:> As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

Second edit: Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again.I hope this may solve your issue.

---

### Post by Thaimite on 2009-11-24
Thank you for your reply, and I will try your suggestion, However my problem seems to be the opposite.
I need to boot windows before the card will work.  If I unplug the power cord it will not work again until I boot windows and then do a shutdown and restart without removing the power cord
Edit
By the way I am dual booting with a trial version of Windows 7 which I intend to remove as soon as this issue is sorted

---

### Post by Thaimite on 2009-11-24
I have spent all morning trying fixes and looking for similar users with similar issues but with no luck.
when doing a cold boot in to Ubuntu the card lights flash as if it is trying to negotiate a connection and then fails and all goes black. No link light or anything.  Rebooting does not help UNTIL I boot in to windows and the card is then initialised and connects.  At this stage I can then do a shutdown /restart to Ubuntu 9.10 and all is OK until next time the power cord is disconnected, when I need to repeat the process.
Can anybody goive me some simple tips on how to diagnose this (what log / configuration files etc to check)
Thanks
The Motherboard is a Biostar MCP6P and the onboard 100Mb NIC works fine. I did try disabling this in the BIOS but that did not help.

---

