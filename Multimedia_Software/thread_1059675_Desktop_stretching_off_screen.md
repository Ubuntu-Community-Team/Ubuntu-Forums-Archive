---
title: "Desktop stretching off screen"
date: 2009-02-04
forum: Multimedia Software
---

### Post by dboucher on 2009-02-04
Hi all,

I have a relatively minor problem which I've been scratching my head over for quite a while now. I just bought a Lenovo ThinkPad R400 with the integrated Intel GMA x4500. The out-of-the-box support for the hardware is mostly wonderful, except that I'm having some difficulty with my screen resolution.
I've set my screen resolution to 1280x800 in my xorg.conf and confirmed that my screen was set to the corrrect resolution:

```
dboucher@awesome:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 800, maximum 1360 x 1360
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-2 disconnected (normal left inverted right x axis y axis)
```

However, all of the window managers I have tried think that the screen ends before hitting the bottom of the screen, and the right border of my desktop stretches about 50px past the right side of the screen. Any ideas?

---

### Post by jpeddicord on 2009-02-05
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]
Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

Thanks,
Jacob

---

