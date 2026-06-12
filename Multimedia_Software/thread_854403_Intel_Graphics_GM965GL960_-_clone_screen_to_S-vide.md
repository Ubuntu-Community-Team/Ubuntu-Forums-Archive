---
title: "Intel Graphics GM965/GL960 - clone screen to S-video"
date: 2008-07-09
forum: Multimedia Software
---

### Post by GNUbee40 on 2008-07-09
Hey Everyone!

I am pretty much Linux Newbie and currently trying to use my laptop for watching movies on the TV.
The clone screen function Under System-->Preferences-->Screen Resolution does not work. The TV does not get detected, when I try to push the "Detect displays".

After trying 
```
lshw -class display
``` 
i get
```
 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

So there is no graphics driver installed. :frown:  
I tried to use displayconfig-gtk and see two graphic adapters (i guess i have a dual graphics adapter), one with no driver one with VESA standard driver. I changed that to Intel 810i drivers for both adapters 
Well this garbled the screen a lot and I was forced to use low resolution plus my keyboard layout suddenly changed to USA :confused: 
I guess the xorg.conf was f... up, so i used the backup to revert the changes - and now I am reluctant to make other changes to it. 

Anyone who has had success in doing what I try to do?

---

### Post by unoodles on 2008-07-09
Are you on Hardy?
Either way, the way I got it working with my Inspiron 1420n with intel 965gm I just plugged in the cable and hit Ctrl+Alt+Backspace, and it worked fine.

---

### Post by GNUbee40 on 2008-07-09
Yep - are on Hardy.

Tried what you suggested - but this only messes up my laptop screen, without producing any picture on the TV

According to the X-window wiki, S-video detection is turned off by default in Ubuntu - but the solutions in the wiki did not work for me...

I guess i have to find a way to configure the drivers right first...

---

### Post by ruggrat on 2008-07-10
Please let me know if you figure it out, I have the same lshw listing!

---

### Post by blackduck on 2008-07-13
**Intel Graphics GM965/GL960 - clone screen to S-video**
I get the same result for lshw except version is 03.
Ctl+Alt + B/S just reboots my Travelmate 6492.

---

### Post by GNUbee40 on 2008-07-14
From what i understand Ctr-Alt-B-space is supposed to log off. As a side X-window gets restarted, and hopefully the TV gets detected. Works for some - but obviously not for all...
Guess i will have to fumble around with the Xorg.conf again...

---

### Post by am15 on 2008-07-22
I have the same exact problem.  Has no one solved this yet.  I want to watch video on the tv not laptop.  I tried Ctrl+Alt+Bkspc.  It just reboots and goes to Unknown clone screen which is for the tv (detected automatically) but nothing comes on the tv screen.  Should i reboot?  Will try.

---

