---
title: "Enabling nVidia Driver Somewhat Broke Display"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by HarryTruman on 2007-07-21
Last night, I did a routine Ubuntu 7.04 install on a clean drive.  I've installed Ubuntu quite a few times between all my PCs and I've broken things often, so I'm used to enabling nVidia drivers and whatnot.

Last night, however, I rebooted after having enabled the nVidia drivers.  After it shutdown and as it was booting back up, I realized that I was getting no display.  No BIOS display, no nVidia splash screen that I normally see for a second, no nothing.  Until I'm fully booted into an OS, I get no graphical display of any kind.

What could have caused my video card to just...not initialize until I load into an OS?  I've never seen this happen before, and to be honest I wouldn't think something like this would be possible.  I have a GeForce 6800 Ultra.

---

### Post by AlexenderReez on 2007-07-21
check your card system-->
> lspci | grep VGA

check rendering support --->
> glxinfo | grep direct

if no is answer enter--->
> sudo nvidia-xconfig --add-argb-glx-visuals

good luck:)

---

### Post by HarryTruman on 2007-07-21
Well there's a problem with that.  I enabled windows as the primary boot disk in Grub before all of this happened (because until I got Ubuntu setup the way I wanted it, I wanted to boot to Windows by default), so I really have no way to get back into linux now...

---

### Post by HarryTruman on 2007-07-22
I managed to get back in to Ubuntu, and after some updates and settings changes, I've at least somewhat localized the problem.  When I try to reboot/shutdown Ubuntu, it hangs and after turning off my computer, my BIOS give me an error message saying that the CPU frequency has changed and that it is going into safe mode (the CPU frequency is getting throttled down, I've noticed).  If I go in and restore fail-safe settings and reboot, everything displays/loads fine.  If I ignore it and continue to boot, that's when I lose my display.

I don't know what the hell is going on with this, has anyone heard of something like this happening before?

---

### Post by HarryTruman on 2007-07-23
Last bump, I'm at a loss.

---

### Post by Supremacy on 2007-07-23
> **HarryTruman said:**
> Last bump, I'm at a loss.

Your luckily enough my brother had the exact same prob with his AMD x2. It turned out that his GFX card was not Posting (eg, its BIOS was damaged or gone). How new is your GFX card or pc? Also, his RAM was dead also. So, the first thing I woudl say it is the GFX card. Do you have a spare you can try??

Also, dont try and update the BIOS. We did that and had to buy another mobo cause it went wrong and we lost the BIOS altogether.

Regards,
Supremacy

---

### Post by HarryTruman on 2007-07-23
I *have* had to send my video card back twice within six months to get it repaired for overheating, but I've at least managed to get my BIOS display back and have figured out that the problem I'm having is occuring only when Ubuntu attempts to shutdown.  So, unless this is all somehow tied together in some way that I'm missing, I'm thinking that it's not a hardware issue at this point.  My system is two years old: AMD 3600+, GeForce 6800 Ultra, 2GB Corsair XMS, Epox 9-NPA nForce4 Ultra mobo.  

I think at this point I'm going to zero the drive and reinstall, I'm not all too confident that this wasn't doomed from the beginning.

---

### Post by stchman on 2007-07-23
> **HarryTruman said:**
> Last night, I did a routine Ubuntu 7.04 install on a clean drive.  I've installed Ubuntu quite a few times between all my PCs and I've broken things often, so I'm used to enabling nVidia drivers and whatnot.

Last night, however, I rebooted after having enabled the nVidia drivers.  After it shutdown and as it was booting back up, I realized that I was getting no display.  No BIOS display, no nVidia splash screen that I normally see for a second, no nothing.  Until I'm fully booted into an OS, I get no graphical display of any kind.

What could have caused my video card to just...not initialize until I load into an OS?  I've never seen this happen before, and to be honest I wouldn't think something like this would be possible.  I have a GeForce 6800 Ultra.

Do you mean you enabled the Restricted driver?  What kind of nvidia video card do you have?  If so let Ubuntu do its updates first.  There may be a kernel module that needs updating for your card.

---

### Post by Supremacy on 2007-07-24
> **stchman said:**
> Do you mean you enabled the Restricted driver?  What kind of nvidia video card do you have?  If so let Ubuntu do its updates first.  There may be a kernel module that needs updating for your card.

He did say he had a NVidia GeForce 6800 Ultra.

@HarryTruman: Hmm, twice in six months. Thats worse than my old card. (6600GT sent back to Taiwan 2 times under warranty). See how a reinstall goes, and as stchman said, let it update. Also, I would suggest trying the newer drivers. They can be found using the Synaptic Package Manager. **Install the nvidia-glx-new instead of the nvidia-glx ones the Restricted Driver Manager installs.**

Hope it all goes well. Just seems strange that it only happens when you wish to reboot.

Regards,
Supremacy

---

