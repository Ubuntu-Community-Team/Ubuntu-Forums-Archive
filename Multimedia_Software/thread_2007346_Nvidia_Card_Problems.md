---
title: "Nvidia Card Problems"
date: 2012-06-20
forum: Multimedia Software
---

### Post by mscout2004 on 2012-06-20
I have a GeForce 8500GT 512MB PCIe graphics card in now and everything runs fine when I tried to upgrade to the GeForce 210 1GB PCIe card Ubuntu would not load and gave me the message:

PANIC: early exception 08 rip 246:10 error ffffffff813175e7 cr2 ffffffffff478f64

That is exactly how it showed it onscreen. What happened and will I be able to use this card as it wouldn't even boot an live CD either?

---

### Post by oldfred on 2012-06-20
Fixed typo in title.

Have not seen that error.
What version of Ubuntu? Did you install the nVidia drivers or not?

---

### Post by mscout2004 on 2012-06-20
Sorry about the duplication of the thread. I am using 12.04 and didn't ever have the chance to install the drivers for the card put in the card and went to boot to install them but it stopped loading and gave me that error.

---

### Post by oldfred on 2012-06-20
You have to use nomodeset with nVidia cards. It also may need other boot options?

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mscout2004 on 2012-06-20
I downloaded the 64 bit driver for the card to try to install before putting the card in to see if that works but the install file says you have to shut down the x sever to install and I am not sure how to do that so I will try the nomodeset option first and see if that works

---

### Post by mscout2004 on 2012-06-20
Still not sure exactly what happened but I held shift during boot and it said loading GRUB but never gave the menu, but it did fully boot and I am not having any problems out of it yet. Even did a reboot and left it alone to see if it corrected itself and booted fine the second time also with no intervention from me.

---

### Post by mscout2004 on 2012-06-21
Well that worked for about 24hrs came in from work and went to boot my PC and it started giving me the same error again??? Guess last time it was just a fluke.

---

### Post by oldfred on 2012-06-21
Did you install drivers or change anything before shutting down? Something must have changed.

Can you get to grub menu with shift held down from BIOS until menu appears? Then try nomodeset or recovery mode to boot?

---

### Post by mscout2004 on 2012-06-21
No drivers had to be installed last time it worked. I have tried using nomodeset in both normal and recovery mode but still won't boot as soon as you hit ctrl+x to boot it gives me the error message.

---

### Post by mscout2004 on 2012-06-21
I am going to try and get these new drivers I got from Nvidia and see if they work, does anyone know how to shut down the x server so I can install them?

---

### Post by mscout2004 on 2012-06-21
Got the new Nvidia drivers installed finally but going to wait a few days to mark this as solved to be sure it is fixed. Will be making a how-to document on the Nvidia driver install process if any one is interested just message me.

---

### Post by mscout2004 on 2012-06-22
Just as I had feared turned it off over night and the next morning got up and it gave me the same error message? Does anyone have any other ideas on this????? :-s

---

### Post by oldfred on 2012-06-22
Years ago I tried to use the nVidia drivers from nVidia and had so much touble and could not even houseclean them correctly until nVidia created a script as it had installed all sorts of stuff everywhere.

Since then I only install the Ubuntu versions of nVidia as they have been tested to work with Ubuntu. Some very new cards may need the newest drivers, but everything else should work with the Ubuntu verison. nVidia did have on release recently (.40?) that did not work but was updated within a week or so.

---

### Post by mscout2004 on 2012-06-22
well I got the .59 driver and it seems to work but when the computer is off for more then a couple hours I have to put back in my old card boot to text mode and re-install the drivers then I can use my new card again. Not sure why a few hours of being off makes me run back into the same error message????

---

### Post by oldfred on 2012-06-23
Before changing cards have you tried booting into recovery mode? And trying to reconfigure video from that?

Is this the nVidia version or the version from Ubuntu that you have installed?

---

### Post by mscout2004 on 2012-06-23
I have tried to do the reconfigure of the video from recovery mode but with the new card in it wont boot recovery mode gives same error as when try to normal boot. 

The .59 is the driver version I got from the NVIDIA website.

---

### Post by mscout2004 on 2012-07-27
Well I finally figured it out my graphics card wants a power supply with 2 18Amp rails and mine only has 1 18Amp and 1 12Amp rail so I cant get enough power to the card. I will upgrade later and will post again if that fixes it. I will go ahead and mark this as solved for now.

---

