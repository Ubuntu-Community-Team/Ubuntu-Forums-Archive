---
title: "Utilizing compat-wireless and ath9k"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by cjwescott on 2010-01-01
I installed a D-Link DWA-652 wireless adapter on my Toshiba laptop.

I first tried loading the driver that came with the disk using ndisgtk.  This recognized the card, picked up my wireless connection but I could not get any connectivity through Firefox or through the synaptic package manager.

So...I found the link to ath9k and downloaded the zipped package.  Now this is where I struggled greatly since it required downloading, unpacking, building and installing. I believe I successfully made the files.

I checked the modprobe -l to see that the ath9k.ko files are in the update list as described here: [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) , I reboot and nothing happens.  My wireless adapter is not recognized.  I don't think the driver installed.

There is a section in the above link which indicates some Prerequisites as follows:

*"You need kernel headers to compile compat-wireless. Ensure /lib/modules/$(uname -r)/build/ exists and points to the location where the kernel headers are installed. If you do not have them, read your distribution's documentation on getting help."*

Perhaps this is where I am missing some steps.  For instance I am not sure that the contents of the modprobe is pointing to the location where the .ko files are located.

Has anyone gone through this process and provide some assistance?

---

### Post by cjwescott on 2010-01-02
Well I figured I would try installing the windows driver using ndisgtk again.

Just like the first time, I am able to get a connection but I am not able to browse the web or download any packages.

So I went into the Ubuntu documentation for wireless trouble shooting.  In it one of the things it tells you to do is type iwconfig at the prompt.  In the list it states that EESID: with my router wireless network name. The troubleshooting guide states the following:

*"If the ESSID for your router is shown there may be a problem with ACPI support. Boot the kernel with the pci=noacpi option."*

So I am gathering that I need to add this to my kernel.  This is where they are now talking a different language.  I did some searching on the web and it appears that I need to edit the file menu.lst in my /boot/grub/ directory, however I have no menu.lst file in that directory. 

I ran across this same issue with an Ubuntu Tip which required me to edit that file and could not find that file either. Is the file hidden?  I'm lost.

Chris

---

