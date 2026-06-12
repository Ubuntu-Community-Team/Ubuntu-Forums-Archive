---
title: "Broadcom Wireless"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by originalseven on 2010-11-14
Experiencing an issue trying to enable Broadcom Wireless B4318 card in HP Pavilion DV400.

This card ran fine in a previous installation of OpenSuse, but Ubuntu is simply not allowing me to enable it. I have installed the firmware & the b43-fwcutter. When I browse System > Admin > Addition Drivers, it shows up as "Activated and currently in use".

But, the indicator light remains off and the option to "Enable Wireless" from the task bar is blanked out and non functional. I have checked it's status in the BIOS and it is enabled.

Any ideas?

---

### Post by TBABill on 2010-11-14
Try the instructions in this thread...[http://ubuntuforums.org/showthread.php?t=1445782&page=4](http://ubuntuforums.org/showthread.php?t=1445782&page=4)

---

### Post by originalseven on 2010-11-14
Those instructions are a variation on the same instructions I've been following.

I have the drivers showing up in both Administration > Additional drivers  and in Administration > Windows Wireless Drivers.

I have run the firmware update (b43-fwcutter)as well as tried enabling/re-enabling in the task panel. Currently, it say's "Device Not Ready", this followed my recent attempt to "Enable Wireless" by clicking on the task panel. If I reboot, it will be grayed out again, but I can "enable Wireless" and get this same "Device Not Ready" error.

It seems as though it's a software issue, but everything states the drivers are active and in use, but nothing works...

---

### Post by TBABill on 2010-11-14
Very strange. I'll keep looking and post back. The 4318 seems to be a tough one to get going and I only have experience with the 4312. If I find something definitive I'll post here.

---

### Post by TBABill on 2010-11-14
Did you follow the Ubuntu help site directions for the B43? Steps to take are here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by originalseven on 2010-11-14
Yes, again this link is yet another version to the same instructions that I've tried countless times.

I have run the fwcutter, extracted the firmware, the drivers are installed, they say they are activated...BUT....the wireless is inactive and cannot be enabled. The only change I get is "Device not ready".

Could there be some BIOS issue or hard reset on the wifi itself?

---

### Post by TBABill on 2010-11-14
I'm about out of ideas. Perhaps a clean uninstall of the B43 driver in Synaptic and a reinstall of it WHILE connected via ethernet to your router? Or hopefully someone with specific experience with the 4318 will come along soon and be of more assistance.

---

### Post by TBABill on 2010-11-15
Ok, I installed Maverick on my laptop just to try it out and will now keep it there. But what a joy that was. Apparently wireless for Broadcoms is now defaulted to blocked upon installing the driver. So what I had to do was ```
sudo rfkill list
``` to see if it was soft or hard blocked. Both were marked yes. So I had to ```
sudo rfkill unblock all
```
 
Have you tried that already? I was unaware this was an issue and I don't know if it could be for you as well or not. I also could not get the STA driver going and had to uninstall/completely remove/re-install. I even tried the B43, which is not a good choice for my card, then uninstalled it and reinstalled the STA again. It finally started working but seemed like it took 3 or 4 removal/reinstall steps plus as many restarts.

---

