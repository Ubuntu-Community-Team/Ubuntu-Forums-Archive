---
title: "gnome &quot;Screen Resolution&quot; - no correct resolution for second monitor, Intel GM965"
date: 2008-10-19
forum: Multimedia Software
---

### Post by snitko on 2008-10-19
I've just bought a laptop with IntelGM965 on board and installed Ubuntu 8.10.

I wanted to connect it to my NEC LCD1970NX monitor, so I just plugged it in and it wokred, but with a wrong resolution. Here's a screenshot from "System ->  Preferences -> Screen Resolution":

[IMG]http://dl.getdropbox.com/u/113891/pics/screen_resolution_ubuntu.png[/IMG]

1024&#1093;768 is the largest resolution on the list, while the monitor's standart is 1280&#1093;1024.

Adding "Display" subsection to "Screen" section of xorg.conf and specifying "Modes" didn't help, as if it was reading it's conf from somewhere else.

I ran this:

```
$ xrandr

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1360 x 1360
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0 +
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9 
``` 

As you can see, the monitor's standart 1280&#1093;1024 resolution is not present in the list. I don't know why, but I think it's the key.

Then I ran this:

```
$ ddcprobe

vbe: VESA 3.0 detected.
oem: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)GM965/PM965/GL960 Graphics Controller Hardware Version 0.0
memory: 7616kb
[B]mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m[/B]
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 3714
eisa: AUO3714
serial: 00000000
manufacture: 1 2007
input: analog signal.
screensize: 26 16
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@60
monitorid: AUO
monitorid: B121EW03 V7
```

So, this resolution is supported by hardware and probably it's a settings issue. Anyone knows how to add 1280x1024 resolution to the GNOME "Screen Resolution"?

---

