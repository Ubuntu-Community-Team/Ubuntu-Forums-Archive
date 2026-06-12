---
title: "Graphics not displaying correctly, help!"
date: 2009-04-24
forum: Multimedia Software
---

### Post by Tj218 on 2009-04-24
I'm relatively new about (2 weeks xp) to Ubuntu, I am a fan and installed it on an old computer. I liked it so I just installed 9.04 on my old Toshiba Satellite S100 (1.06 GHZ Celeron, 256mb RAM) and am having some issues with the graphics (Intel 82830 Graphics chipset)

Straight out of install I had issues with the fonts found a fix with this website: [http://bbs.archlinux.org/viewtopic.php?id=61433](http://bbs.archlinux.org/viewtopic.php?id=61433)

However, now I am having issues with scrolling. If I scroll down (or hit page down on a website or in Open Office, the top of the active window stays the same, and only the bottom few inches of the screen scrolls. If I use the oppsoite direction going up, the bottom half remains static, the top half moves.... However, if I switch tabs in Firefox, and go back to the original tab the screen will be where it should be after scrolling down...This was not the case prior to the edit of my xorg.conf file to fix the font issue.

Any thoughts on how to get this graphics chipset to work properly? Thanks again!!!

Here is my xorg.conf file: 

Section "Device"
    Identifier    "Configured Video Device"
    Option          "AccelMethod"   "XAA" (this was line for the fix for the font issue)
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


***UPDATE*** I eliminated the Accelmethod line and added the following line ""NoAccel" "true"  (I am not sure what these commands are doing besides enabling or disabling acceleration.. it is now working, but now I have slow scroll speeds (but if I hit pg. up/down it is fine, just if I try to scroll with the arrows on the side...any thoughts on this...very frustrating.

---

### Post by Tj218 on 2009-04-24
bump, still looking for a better edit of the xorg.conf

Thanks!

---

### Post by ibattison on 2009-04-25
I have a different laptop, which has the same graphics card. I have exactly the same problem and have gone through the same process as yourself. I am still hunting around on the net for the solution and as soon as I find, I will post on here. I know it will simply be something missing from the Xorg.conf. I know this, as I have tried several other versions of Linux on this same laptop, that can auto detect the card and set up the system correctly. Namely DSL and also Puppy Linux and some of its puplets.

I am off now to do some searching. Hopefully, will be back shortly.

---

### Post by Tj218 on 2009-04-26
Thanks for searching, I have settled for the slow scrolling for now :(

I want to like Ubuntu, but I am becoming convinced that it isn't the be all end all for some laptops....


If you find anything please let me know!!!


Thanks!

---

