---
title: "New mobo - Ubuntu no longer recognizes graphics card?"
date: 2014-04-19
forum: Multimedia Software
---

### Post by matt95 on 2014-04-19
Hello,

Setup: i5-4670K
Gigabyte GA-Z87X-UD4H
Ubuntu 12.04 LTS
ASUS GTX 770 2GB (Nvidia)

So I was previously using an Asrock z87 Extreme4 and yesterday upgraded to a Gigabyte GA-Z87X-UD4H. After getting everything together, my HDD with Windows on it boots up just fine, but when I try to boot my Ubuntu HDD I just get a black screen with a blinking white line. If I plug the the DVI into the mobo, everything shows up, but plugging it back into the GPU causes the same black screen. I assume this is a driver issue but I'm not sure how the new mobo caused it. 

Note that a few weeks ago when I got the GPU I installed the Nvidia proprietary drivers but something went wrong&#8212;causing a similar blank screen issue&#8212;and I had to purge the nvidia drivers, reinstall the nouveau drivers, and reconfigure x server. Ever since then my boot up has been a little weird (blank screen with line for a few seconds, then a bunch of lines of white and red text scrolling, then log in screen, and then after log in the screen would flash grey for a few seconds before the desktop would show up&#8212;I don't recall this happening before the proprietary drivers). I recall being about to get to a TTY from the blank screen and do all the fixing (I don't know how else i would have done it), however this time I am not able to get to a TTY (tried F1, Alt + F1, Ctrl + Alt + F1, and Ctrl + F1) when the screen comes up. I can type for a few seconds but then the font changes and the computer locks up and restarts. Also, before the new mobo if I went to additional drivers it would show the available Nvidia drivers and the ones being used, however now there is nothing in the window (I assume it's because I am using integrated graphics, but I am not sure). I am pretty sure I didn't entirely correct the issue that caused the original problem, and this may be causing the new problem, though I'm not sure. 

Lastly, when booting recovery mode from grub, as the text flys by it will stop and hang on

```
[     2.639957] [drm:drm_pci_agp_init] *ERROR* Cannot initialize the agpgart module.
[     2.639961] DRM: Fill_in_dev failed.
```

and requires a reset to get back to grub. 

I am about to try and boot from a 14.04 Live USB (Don't have a CD or CD drive) and see if it works with the graphics card, and if all else fails  try putting the old mobo in (ugh) to see if it is in fact related to the mobo, but wanted to get your guys' take on it first. Note that I am very new to linux and have only been using it for about 4 months now. 

Thanks

edit: Okay so a 14.04 LTS USB stick is picked up by the GPU. So my 12.04 is definitely messed up. Any ideas on how fix it?

---

### Post by mörgæs on 2014-04-20
> **matt95 said:**
> Okay so a 14.04 LTS USB stick is picked up by the GPU. So my 12.04 is definitely messed up. Any ideas on how fix it?

Go for a fresh install of 14.04. I don't think it's worth the effort to troubleshoot the old system.

---

