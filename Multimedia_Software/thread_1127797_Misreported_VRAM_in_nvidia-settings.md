---
title: "Misreported VRAM in nvidia-settings"
date: 2009-04-16
forum: Multimedia Software
---

### Post by Aintaer on 2009-04-16
I seem to have come across an interesting problem with the NVIDIA binary drivers.  My Dell XPS M1530 has a Geforce 8600M GT with 256MB VRAM.  However, nvidia-settings consistently reports that the card has 512MB.

At first I thought this was because of the 4GB addressable memory limitation in the generic 32-bit Linux kernel, since I noticed that at the same time, the system reports only 3.5GB total system RAM, whereas I have 4GB physically installed.  So I installed the server kernel package, which increased the amount of system RAM to more or less 4GB, but nvidia-settings still reported the graphics card having 512MB.

lspci reports 256M prefetchable 64-bit memory for the card at 0xe0000000, so I know Linux sees the right amount physically.  However, I would like to know if there is some way to find out which segment of memory the card is using, whether it is actually using its dedicated GDDR3 VRAM or relying on the slower system RAM.

As a tack-on question, should I try to see if the 64-bit Ubuntu solves these problems?

---

### Post by Svensk023 on 2009-04-16
I found that switching to 64-bit ubuntu fixed several annoyances with my hardware's performance. But that is just my personal experience. I am not sure what the correct solution to you video card's memory output problem is. I have ATI card's in my tower, and lets just say they don't play nice with Linux...

---

### Post by Aintaer on 2009-04-16
I just tried 64-bit live cd, and it looks like it works fine.  The Xorg log shows loading the NV driver properly detected 256M video RAM.  So curious about this, I tried loading the nv driver in my current setup instead of the nvidia binary... 256M.

The fault, it seems, is entirely within NVidia's driver.  To be extra sure, I tried their latest binary blob (180.44).  Not only did the driver still report 512M VRAM, it also ran glxgears *slower* by almost 2000 FPS, and caused graphical bugs in the menus.

I think I will change to the 64-bit Hardy sometime next week.  I just hope all the hardware will still work.

---

