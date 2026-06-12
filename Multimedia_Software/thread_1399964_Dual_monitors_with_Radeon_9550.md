---
title: "Dual monitors with Radeon 9550"
date: 2010-02-06
forum: Multimedia Software
---

### Post by taximorph on 2010-02-06
Hi.

After a while of being very impressed with Kubuntu on my laptop, I decided to install Kubuntu 9.10 on my PC. All's working fine except dual monitors. I have an oldish Radeon 9550 graphics card which has both a VGA and DVI output. The System Settings > Display screen acknowledges the presence of VGA-0 and DVI-0, but the Multiple Monitors tab says "This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration."

Here's the output from xrandr 

```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     60.0*
   1152x864       75.0
   1024x768       75.0     60.0
   832x624        74.6
   800x600        75.0     60.3
   640x480        75.0     59.9
   720x400        70.1
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     60.0*
   1152x864       75.0
   1024x768       75.0     60.0
   800x600        75.0     60.3
   640x480        75.0     59.9
   720x400        70.1
S-video disconnected (normal left inverted right x axis y axis)
```

Having googled around for a solution, I've tried things like
```
xrandr --output VGA-0 --pos 0x0 --mode 1280x1024 --output DVI-0 --pos 1280x0 --mode 1280x1024
```
only to receive
```
xrandr: screen cannot be larger than 1280x1280 (desired size 2560x1024)
```
Other suggestions were to edit xorg.conf, which doesn't exist, so tutorials suggesting modifications to the odd line aren't useful.

Any suggestions on how to get dual monitors working? I don't necessarily care if there's no fancy graphics acceleration - I just want the extra screen space that 2 monitors side by side brings.

Many thanks.

---

