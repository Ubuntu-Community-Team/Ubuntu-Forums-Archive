---
title: "External monitor - HDMI"
date: 2011-06-04
forum: Multimedia Software
---

### Post by uuu2 on 2011-06-04
I'm going to add an external to my notebook. Video processor is Intel i965, so I installed driver xf86-video-intel. Executing xrandr, I get:

```
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 287mm x 180mm
   1280x800       59.8*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
```By the unknown reason, xrandr don't see HDMI port. In addition, these 3 ports have been listed in xrandr output even before I'd install video driver. Maybe, the port called "DVI1" is the HTML port? 

xrandr --verbose gives:

```
...
DVI1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x43
    Timestamp:  26939
    Subpixel:   horizontal rgb
    Clones:     VGA1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 

```

"xrandr --output DVI1 --same-as LVDS1" executed without any error message, but the external monotor shows nothing.

"xrandr --addmode DVI1 1280x800@60" executed with error "cannot find mode 1280x800@60".

---

