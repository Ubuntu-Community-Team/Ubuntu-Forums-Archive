---
title: "Two graphics cards, two monitors"
date: 2011-08-08
forum: Multimedia Software
---

### Post by sdpope@gmail.com on 2011-08-08
I'm currently just booting Ubuntu live, wondering if I can get it to use both my displays. Here's the issue:

I have two graphics cards, one PCI-E and one onboard.
[QUOTE="lspci"]00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7100 / nForce 630i] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce G100] (rev a1)
[/QUOTE]

With a monitor plugged in to each. Windows recognises them and makes them one screen, Ubuntu is having less luck. When booting up, the desktop and stuff all happens on the left display, hooked up to the PCI-E card. All the "* Starting ...... [OK]" stuff and the Ubuntu splash screen happen on the right monitor. 

xrandr says this: [QUOTE=xrandr]ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA-2 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      75.0*+   60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)
[/QUOTE]

Does anybody know if there's any way to get them working as one screen? On Arch Linux, I have both displays working with separate X servers, which is not at all ideal.

---

