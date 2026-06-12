---
title: "Screen Resolution on Ubuntu 11.10 (nvidia)"
date: 2011-11-24
forum: Multimedia Software
---

### Post by ttr738 on 2011-11-24
Hi!
So, I have a fresh install of 11.10. When I booted from the Live CD, it gave me a screen resolution of 1920x1080 like it's meant to, however when I actually install I only have 1024x768.
I'm using the nVidia proprietary "post-release-updates" drivers, although I've tried all the below with the other ones and still no joy (even less joy actually!).
Hopefully someone can help! :-)

So, I've tried nvidia-settings: nope, few slightly higher resolutions but no 1080p
I've tried disabling both proprietary drivers: highest is still 1024x768
I've done:
```

$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  

```
Hmm... doesn't look like it knows much about my display then!
So, I tried:
```

$ xrandr --addmode default 1920x1080
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1920x1080"

$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default

$ xrandr --addmode default 1920x1080_60.00
xrandr: Failed to get size of gamma for output default

$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1920 x 1080

default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
   1920x1080_60.00   60.0  

```
All seems ok. So lets try it out:
```

$ xrandr --output default --mode 1920x1080_60.00

xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

$ xrandr --output default --mode 1920x1080_60.00 --rate 60
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```
It waits around for a bit, then comes back with that "crtc 0 failed" error, and does nothing to the screen resolution. 
Any idea what I'm doing wrong?
My graphics card:
```

$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)

```
My display: Foehn & Hirsch 37" Full HD Widescreen LCD TV something-or-other :-)

Any help greatly appreciated!

---

### Post by wolfen69 on 2011-11-24
How is it hooked up? VGA, HDMI, or DVI?

---

### Post by ttr738 on 2011-11-24
VGA. From continued fiddling, seems like Nouveau (which is being used on a LiveCD boot) picks up the EDID fine, but Nvidia's own drivers don't. Can't be good!

Had a look at the xorg log while in Live CD mode and found these two bits I figure could be put into xorg.conf somehow:
```

Ranges: V min: 58 V max: 62 Hz, H min: 31 H max: 61 kHz, PixClock max 173 MHz

Modeline "1920x1080"x0.0  172.75  1920 2048 2248 2576  1080 1083 1088 1120 +hsync -vsync (67.1 kHz)

```

Presume they're things the nvidia drivers should be picking up but aren't?

---

### Post by ttr738 on 2011-11-24
Furthest I've got now is adding the below in the "Monitor" section of xorg.conf:
```

HorizSync 31-61
VertRefresh 58-62
Modeline "1920x1080"  172.75  1920 2048 2248 2576  1080 1083 1088 1120 +hsync -vsync

```
Still doesn't work though - it's showing one more mode in nvidia-settings gui I think, but not 1920x1080.
Any ideas please? :-)

---

### Post by rsrini on 2011-11-29
I am having T410 thinkpad laptop with docking station and 24" BenQ external LCD monitor connected to VGA. I am also seeing the same behaviour. Installed Nvidia post release update driver. I am not able to get the 'disper' working with different configuration. Either only external monitor works (by manually editing the xorg.conf) or Laptop screen works. If disper works it will be great help. xrandr -q gives 

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0  
   1680x1050      52.0     53.0  
   1600x900       54.0  
   1440x900       55.0  
   1400x1050      56.0     57.0     58.0  
   1360x768       59.0     60.0  
   1280x1024      61.0     62.0  
   1280x960       63.0  
   1280x800       64.0  
   1280x720       65.0  
   1152x864       66.0     67.0     68.0     69.0  
   1024x768       70.0     71.0     72.0  
   1024x576       73.0  
   960x600        74.0  
   960x540        75.0  
   840x525        76.0     77.0     78.0     79.0  
   832x624        80.0  
   800x600        81.0     82.0     83.0     84.0  
   720x450        85.0  
   700x525        86.0     87.0  
   680x384        88.0     89.0  
   640x480        90.0     91.0     92.0     93.0  
   512x384        94.0     95.0  
   400x300        96.0  
   320x240        97.0     98.0 

Do we have to keep two sets of 'device', 'screen, and 'monitor' sections in the xorg.conf or not. Also if you enable twinview still will i be able to use only external monitor using disper.

---

### Post by ttr738 on 2011-11-29
Not sure about your problem, but I now have my monitor working at full 1920x1080 by upping the maximum HorizSync and VertRefresh values some more in it's "Monitor" section.

Think yours will need something to do with "TwinView" setting in xorg.conf, to have both monitors on at the same time. That's only a guess though - my setup is only single monitor. 
Hope it helps anyway!

---

### Post by ITPhoenix on 2012-05-07
> **wolfen69 said:**
> How is it hooked up? VGA, HDMI, or DVI?For some reason, this avenue has not been researched in any of the posts concerning nvidia and screen resolution problems.

I am pleased to announce after much frustration, unplugging the VGA and going with DVI gave me all the resolutions the card had to offer.

I am using the current version, recommended driver on GeForce 210.

The VGA interface is being deprecated, and eventually we will only have HDMI, IMO.  I also believe optical media will be as useful as a vinyl record within 20 years.

All I need now is to get internet sharing to work with another, patch cord connected 11.10 instance on another box.  Even though it kept going through disconnection cycles, internet was coming through albeit too slow. No solution posted worked so far on my 11.10.

---

### Post by KoolPal on 2012-06-02
Hi,

I stumbled on this thread searching for a way to increase screen resolution for my Thinkpad r52. I am stuck on 1024 x 768. I am on Ubuntu 11.04 . All options available are lower.

Can anyone guide me on how to increase my screen resolution?

---

