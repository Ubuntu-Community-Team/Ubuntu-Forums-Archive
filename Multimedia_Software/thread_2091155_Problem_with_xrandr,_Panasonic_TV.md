---
title: "Problem with xrandr, Panasonic TV"
date: 2012-12-04
forum: Multimedia Software
---

### Post by walkietaki on 2012-12-04
I'm having a somewhat similar problem but have had trouble using xrandr to hard-set the correct parameters for my tv. 

My TV is 1080p 96, 60hz Panasonic TC-P55GT50...would like to setup mythtv box but can't seem to get the resolution to set properly and/or add the proper modes?  I also wonder if it has to do with the intel hardware? 

Edid fails w/output...any help would be appreciated!  

I have copied data below: 

xrandr -q
```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 8192 x 8192
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3*    56.2  
   848x480        60.0  
   640x480        59.9  

```

lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```



> **Grenage said:**
> You can 'hard-set' the resolution in /etc/X11/xorg.conf.  If the file exists, could you post its contents?  It's also worth posting your desired TV res, and the output of:

```
xrandr -q
```
and
```
lspci | grep VGA
```

---

### Post by oldos2er on 2012-12-04
Post moved to its own thread.

---

### Post by BicyclerBoy on 2012-12-04
Very nice TV..

VGA connection is not likely to result in a optimum solution.
VGA is the "analog hole" & most (all) TVs only support std vesa video modes & not native resolution.

That said, should be able to do better than 800x600..

Post your file /var/log/Xorg.0.log

You don't list your distro/kernel version but..
The intel iCPU/iGFX devices work a lot better with latest kernel/drivers from xorg-edgers ppa.

I might like to try VA-API (need to use openGL painter in MythTV).
VA-API is not as complete as VDPAU yet, post decode processing (adv de-interlace) is lacking.
Could find openGL rendering & CPU decode is still better.

Test VA-API install with:
vainfo
& the video playback test in MythTV

---

