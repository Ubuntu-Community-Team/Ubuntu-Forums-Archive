---
title: "Two nvidia driver versions for two cards: GT240 &amp; FX5200"
date: 2010-09-07
forum: Multimedia Software
---

### Post by formaldehyde_spoon on 2010-09-07
I have two nvidia cards in my computer, in the hope of running three screens. 

A GT 240 running 2 screens, and an FX 5200 running the third.

 I think I'm ok on the xorg.conf front: I've merged xorg.conf files for each card into a larger one. 

I think my problem is now the drivers.  If  I install the latest version (through Sys > Admin > HardwareDrivers) and reboot the GT 240 screens are used (all three screens are plugged in).
If I then change the driver version to 173 (which is recommended for the FX 5200) when I reboot everything up to the login screen happens on a GT 240 screen, then the desktop is shown on the FX 5200 and the GT 240 screen freezes at the Ubuntu load screen with 5 red/white progress dots.  
So it seems to me drivers are my problem.  

Before I got to the point I'm at now I have had a message when X starts telling me that the driver I had installed (ver 173) could not run the GT 240, and I've been able to make the FX 5200 stop working by changing the driver version from 173 to the latest (without the GT 240 in the motherboard), so I'm pretty sure...  

How can I have two different versions of the nvidia drivers installed?  

And how can I use them in xorg.conf? 
As far as I know the values for drivers in xorg.conf are all taken from /usr/lib/xorg/modules/drivers

---

### Post by formaldehyde_spoon on 2010-09-07
No-one knows anything about this?

 Is the question just too weird?  
Or is it not possible to have two versions of the nvidia drivers installed?

---

### Post by tommcd on 2010-09-07
So are you able to use the FX 5200 along with the GT 240 with the latest drivers?
In any case I think you would be better off just sticking with the latest drivers. The 173 driver will not support the GT 240, as you have obviously discovered.
I don't believe you can have 2 different nvidia drivers installed and in use at the same time. When you install the driver from nvidia.com it will detect if there is already a nvidia driver on your system and it will remove the old driver before installing the new driver. I don't believe there is anyway around this.

---

### Post by formaldehyde_spoon on 2010-09-07
> **tommcd said:**
> So are you able to use the FX 5200 along with the GT 240 with the latest drivers?
In any case I think you would be better off just sticking with the latest drivers. The 173 driver will not support the GT 240, as you have obviously discovered.
I don't believe you can have 2 different nvidia drivers installed and in use at the same time. When you install the driver from nvidia.com it will detect if there is already a nvidia driver on your system and it will remove the old driver before installing the new driver. I don't believe there is anyway around this.

No, my current setup has both cards in xorg.conf, but I can only use one card or the other (I switch between cards by changing the driver from 173 to latest, or vice versa, and rebooting). 

I've previously removed the GT 240 from the motherboard, and had the FX 5200 working with the 173 drivers, then stop working as soon as I change to latest - so although I haven't been told explicitly, and I can't be 100% sure, I am almost certain that the FX 5200 is incompatible with the latest driver.

---

### Post by tommcd on 2010-09-07
Well then, unless anyone else has a better suggestion, you may have to just stick with the newer driver for the GT 240. I don't believe it is possible to run 2 different nvidia drivers simultaneously.

---

### Post by formaldehyde_spoon on 2010-09-08
I've found out from nvidias website that the drivers for these two cards are definitely incompatible, and I can only have one nvidia driver installed.

So I'm going to have to use some other driver alongside nvidia: nvidia for one card (preferably the GT240) and another driver for the FX5200. 

 Nouveau is not an option, because it overwrites nvidia.

I read that someone successfully ran a card with nv alongside a card with nvidia, so I though I'd try that.  Unfortunately when I did, it just went ahead and used nouveau! 

I thought I'd try vesa (is that possible?) but the FX5200 won't work with it, and the GT240 manages to default itself back to whatever nvidia driver is installed! 

This is incredibly frustrating. 

Some questions:
1. How do I ensure nv is used when I specify it in xorg.conf, and not nouveau? 
2. Any tips for running one card on nv and the other on nvidia? 
3. Can I use vesa drivers?  How?

EDIT: I just tried both cards on nouveau, and then both cards on nv.  Nouveau failed (why, oh whyyyyyy...), 
but nv (despite using nouveau in some fashion) actually managed to have all three screens receiving a signal, which I haven't been able to do with any other drivers.
Unfortunately they were just blank (black)...
So even though nv uses nouveau, it is not the same as specifying nouveau.

---

