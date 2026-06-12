---
title: "Improving flash performance."
date: 2009-01-12
forum: Multimedia Software
---

### Post by Unr3a1r00t on 2009-01-12
Hey all.  I was wondering how I could improve the performance of flash based websites like starcraft2.com.  When I go to this site in Ubuntu, the flash intro skips, and does not run smoothly.  However, the same computer in a windows enviroment is able to view the flash intro flawlessly.  I was curious as to how I could improve my ubuntu side.  Thanks in advance.

---

### Post by wolfen69 on 2009-01-12
starcraft2.com works for me. which version of flash are you running? where did you get it? and what are your system specs? an older cpu will have a hard time rendering it.

---

### Post by binbash on 2009-01-12
yup which version of flash are you using?because starcraft2.com plays fine for me.

---

### Post by steveneddy on 2009-01-12
I've been running the 64 bit version of Flash 10 for Linux for a coupla months and it works great.

---

### Post by wolfen69 on 2009-01-12
do "about: plugins" (without quotes and there's no space after the colon. had to put it there so a smiley does not show up) in your browsers address bar to see which version of shockwave flash you are using.

---

### Post by Unr3a1r00t on 2009-01-12
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15


I apologize if I was not clear earlier, but this computer is dual-booted between Windows and Ubuntu.  Windows is able to view the intro at starcraft2.com flawlessly, but Ubuntu doesn't view it flawlessly.  Not in the slightest.  So it is the same hardware between the two OSes, but here are the specs of my machine:


Lenovo IdeaPad S10 423135U

    * Processor Intel Atom Processor N270 Single Core (1.60GHz 533MHz 512KB)
    * Operating System Windows XP Home Edition w/ Service Pack 3
    * Display 10.2" WSVGA AntiGlare TFT with Integrated camera 1024x600
    * Graphics Intel Graphics Media Accelerator 950 (64MB shared)
    * Memory 1GB PC2-5300 DDR2 SDRAM 667MHz
    * Hard Drive 160GB 5400 RPM SATA
    * Networking 10/100 Ethernet & Broadcom 802.11 b/g Wi-Fi
    * Mouse Industry Standard Touchpad
    * Camera 1.3 Mega Pixel Camera
    * Weight 2.64 lbs
    * Battery 3-Cell Lithium-Ion

Hope this helps.  Thanks for the quick replies.

---

### Post by hikaricore on 2009-01-12
**Graphics Intel Graphics Media Accelerator 950 (64MB shared)**

This is likely your problem.
Intel "graphics" hardware is notorius for having aweful Linux support.
You can thank Intel and Mickysoft's DirectX for this issue.

---

### Post by Unr3a1r00t on 2009-01-14
> **hikaricore said:**
> **Graphics Intel Graphics Media Accelerator 950 (64MB shared)**

This is likely your problem.
Intel "graphics" hardware is notorius for having aweful Linux support.
You can thank Intel and Mickysoft's DirectX for this issue.

So there is no way to improve this in linux?

---

### Post by TyTiger on 2011-10-08
> **hikaricore said:**
> **Graphics Intel Graphics Media Accelerator 950 (64MB shared)**

This is likely your problem.
Intel "graphics" hardware is notorius for having aweful Linux support.
You can thank Intel and Mickysoft's DirectX for this issue.

this isn't very helpful. 

Supposedly you can override Flash's GPU Validation, which forces flash to 'trust' your GPU and take some workload off your CPU.. but the results may vary or may not make any difference at all. 
Hope it helps.

```

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true"  > ~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

```

*Source: [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)*

---

