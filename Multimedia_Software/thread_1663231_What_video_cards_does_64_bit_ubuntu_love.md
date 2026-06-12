---
title: "What video cards does 64 bit ubuntu love?"
date: 2011-01-09
forum: Multimedia Software
---

### Post by wmgcf on 2011-01-09
I have the curse of NVIDIA  driver -kernel compatibility or configuration or (???) headaches. I consider myself fairly capable  at fixing my ubuntu problems and I give up fixing my  NVIDIA driver headaches.

 I think it will be easier for me to get a new video card.  If you are using 10.04 or higher and have been though several  kernel upgrades, and are still delighted with your  video card, ubuntu, and life in general, please say  something and exactly which card you are using,  and if your machine is 64 bit or 32 bit.

---

### Post by efflandt on 2011-01-09
What sort of problems were you having with nvidia drivers and was it an old card or new card?  Someone kept suggesting nvidia GT 220 or GT 240, so I got my new computer with GT 220 that worked fine with nouveau or nvidia drivers in 64-bit Lucid or Maverick.

I have since upgraded to GT 430 which even Natty development kernels do not know about yet.  The nouveau driver in Lucid or Maverick only do vbe graphics modes with it (I have sent gpu BIOS dumps to nouveau developers), and the nvidia 195 driver in Lucid did not support it.  But it works fine with any of the nvidia 260 drivers.  You can get most recent nvidia drivers for Lucid or Maverick by adding x-swat to your repositories without having to fiddle with manual installation, so they update properly with kernel updates.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```Then if using older drivers older drivers from repositories, just go to Additional Drivers (or Hardware Drivers in Lucid), "remove" nvidia, then "activate" nvidia, and reboot to have most recent driver.

The nouveau driver works full 1080p resolution in Natty with GT 200 series or GT 430, although, Natty will not do Unity with nouveau yet even if you add libgl1-mesa-dri-experimental for glx support (although, that works fine for Kubuntu Natty).  But nvidia drivers (currently 260.19.29) work great.  Although, Natty itself is still being sorted out.  Firefox 4 or 64-bit Hulu Desktop w/real 64-bit flash works fine.

I don't know about the hotter GTS and GTX cards because I think my psu is 375 watts, so I stuck to the best card for not more than 300 watts.  The GT 430 is faster and cooler using less power than the GT 220, so I am happy with it.  Although, a heavy Windows gamer might want something more.

---

### Post by cascade9 on 2011-01-09
> **efflandt said:**
> What sort of problems were you having with nvidia drivers and was it an old card or new card? 

+1. Without that information, all anyone can do is guess. 

> **efflandt said:**
> Someone kept suggesting nvidia GT 220 or GT 240, so I got my new computer with GT 220 that worked fine with nouveau or nvidia drivers in 64-bit Lucid or Maverick.

I have since upgraded to GT 430 which even Natty development kernels do not know about yet.  The nouveau driver in Lucid or Maverick only do vbe graphics modes with it (I have sent gpu BIOS dumps to nouveau developers), and the nvidia 195 driver in Lucid did not support it.  But it works fine with any of the nvidia 260 drivers.  You can get most recent nvidia drivers for Lucid or Maverick by adding x-swat to your repositories without having to fiddle with manual installation, so they update properly with kernel updates.


*blinks* why go from GT220 to GT430?

Kernels dont really 'know' about nvidia cards. Jockey should find the GT430 with 10.10, its got driver that supports it.

---

### Post by Yellow Pasque on 2011-01-10
> Kernels dont really 'know' about nvidia cards.
Not the kernel per se, but the ddx driver needs to know some detail on the card to tell the kernel how to set modes for it.

> Jockey should find the GT430 with 10.10, its got driver that supports it.
Jockey will only find the card if its PCI ID is in nvidia-modaliases package. I don't know if that's a safe assumption to make or not. I can't remember when the GT430 was released and/or if Ubuntu updates the modaliases after release.

---

### Post by wmgcf on 2011-01-11
> **efflandt said:**
> What sort of problems were you having with nvidia drivers and was it an old card or new card?  Someone kept suggesting nvidia GT 220 or GT 240, so I got my new computer with GT 220 that worked fine with nouveau or nvidia drivers in 64-bit Lucid or Maverick. . . .


good questions, let me clarify, my ubuntu video has worked flawlessly for about two years. I am not a gamer. I need a display that does 800X600 flash video well so my wife can watch her chinese serials. That is the main use. My motherboard has onboard nvidia something. Now after a recent kernel upgrade, it only boots to a command line. Searching the ubuntu forums showed me a lot of people with similar problems with nvidia. I don't want to do any tweaking or customization. I want the simplest path to my video working. I don't want to reinstall and block upgrades, but that is an option if I can't get a video card that works. I suppose that there is a video card I can buy (new or used, don't care), stick in there, do a simple setup, and walah, i have video again. Any tips are welcome.

---

### Post by cascade9 on 2011-01-11
Annoying for you wmgcf, but that seems to be some ubuntu problem, not an nvidia driver problem (it could possibly be a combined ubuntu and nvidia problem, but I havent looked into the problem in any depth) 

> **Temüjin said:**
> Jockey will only find the card if its PCI ID is in nvidia-modaliases package. I don't know if that's a safe assumption to make or not. I can't remember when the GT430 was released and/or if Ubuntu updates the modaliases after release.

Thanks, thats a much more concise version of something I read years ago. 

BTW, correction, 10.10 repos dont have a driver that supports the GT430. 11th of october 2010 release, initial linux driver (260.1921) on 11-11-2010, 2nd driver release 13-12-2010. 

The GT430 is far to 'bleeding edge' for me.....I'd prefer to get a mature, sorted card with drivers in repos.

---

### Post by pme 72 on 2011-01-17
I had good results running an HIS Radeon x1550 and the default open source drivers with 64 bit Ubuntu 8.10, 9.04 and 9.10. I never felt the need to install the  proprietary fglrx driver in 8.10 which I believe may have been the last distribution where it was supported. It has always been plug and play with the OS driver. I do not remember ever having an issue with a kernel update. It has 128 MB of 64 bit DDR2 ram with the capacity to borrow up to 512 MB of system ram if available. It was less than $30 at MicroCenter. Never had to fiddle with it. 

For Lucid I switched to the 32 bit version of Ubuntu. The x1550 seemed to work just fine until I tried some of the more demanding tracks in the OpenGL dependent 3D game SuperTuxKart. At times portions of the tracks would just disappear. I had a Sapphire Radeon HD4550, another entry level ATI card, that had good 2D support in previous versions but would not run desktop effects or SuperTuxKart without the proprietary driver. In Lucid it seems to work just fine with the default open source driver so I replaced the x1550. Again, so far, I have had no issues with kernel updates using the OS drivers. It has been plug and play like the x1550. 

This Sapphire version of the HD4550 is passively cooled but could get hot to the touch after extended use. My case may just be poorly ventilated though. Installing a $10 Titan Universal VGA Heat Terminator solved that problem. Even with the fan on the lowest setting the cards cooling fins have stayed cool to the touch.

I do not know what issues you might have switching from Nvidia where you have had success before, to ATI, which has not been without issues for some either. You should post more information about your current card, perhaps someone can help.

If you do not have that information you can run following in a terminal:

sudo lshw -C display

Post the results.

---

