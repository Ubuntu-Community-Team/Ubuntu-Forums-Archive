---
title: "Unbuntu 12.04 with MSI motherboard"
date: 2013-01-08
forum: Multimedia Software
---

### Post by jim1112 on 2013-01-08
I am running Ubuntu 12.04. My computer has a MSI K8MM-V motherboard, which supports 1600x1200, 1280x1024, 1280x800, 1280x768, 1024x768, 800x600 and 640x480 resolution (from vbeinfo). I have a Viewsonic monitor which looks best at 1280x1024 resolution. I have updated grub to allow this resolution. When I go to System Settings > Displays the only resolution choices are 1024x768 and 800x600. When I go to Terminal > xrandr I get:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0     56.0  
   640x480        60.0  

I suspect the problem has something to do with the graphics drivers not fully syncing with the MSI onboard graphics card. Does anyone have any suggestions?

---

### Post by Yellow Pasque on 2013-01-08
You have the misfortune of owning a VIA/UniChrome graphics chip, and these things aren't supported well under Linux at all: [http://www.phoronix.com/scan.php?page=news_item&px=MTIyNjM](http://www.phoronix.com/scan.php?page=news_item&px=MTIyNjM)

---

### Post by tgalati4 on 2013-01-08
Go through the log files:  /var/log/Xorg.0.log and see what specifically is happening.  Try reducing colors to 16-bit.  It might be a video RAM problem.

use a modeline statement in your /etc/X11/xorg.conf file:

tgalati4@Dell600m-mint14 ~ $ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

Reboot and see if you get the desired resolution.  You have to run gtf on your system to get the correct numbers.

---

### Post by Yellow Pasque on 2013-01-08
I guess I should have read more closely (thought you wanted 1600x900). It should be possible to get 1280x1024, even with the generic VESA driver. See: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by jim1112 on 2013-01-09
> **Temüjin said:**
> I guess I should have read more closely (thought you wanted 1600x900). It should be possible to get 1280x1024, even with the generic VESA driver. See: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)
Do you think a VIA driver will be available in the near future, or should I get an inexpensive video card? Which video card manufacturers are most compatible with Ubuntu? Thanks for your help. Jim

---

### Post by tgalati4 on 2013-01-09
My understanding is that the OpenChrome drivers are pretty good.  Via processors and graphics chipsets are low-power and low-performance, so graphics expectations should be low as well.  You are not going to be playing high-end games on this machine.

However, you should be able to get that resolution, as long as you not exceeding some resource (like video RAM) in the machine.  Does the machine use RAM sharing for the video in the BIOS?  If it does, bump up the RAM available for sharing.  It could be as simple as that.

---

### Post by Yellow Pasque on 2013-01-09
From what I can tell, Ubuntu defaults to VESA driver for VIA chipsets nowadays (because kernel modesetting hasn't been merged in the kernel yet as in the article I linked to above).

---

### Post by dannyboy79 on 2013-01-09
it depends on what your needs are, if you want to game and want a better resolution you could pick up a Nvidia 8400 GS for $29 from newegg. I just got one and it pushes my samsung 22" monitor at 1680x1050 awesomely! I am using the nvidia driver 304.64

---

