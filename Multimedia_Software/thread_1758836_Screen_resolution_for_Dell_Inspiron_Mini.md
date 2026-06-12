---
title: "Screen resolution for Dell Inspiron Mini"
date: 2011-05-15
forum: Multimedia Software
---

### Post by phillip4672 on 2011-05-15
Hi,

Please help!

I am stuck in 800x576 resolution and don't know how to escape. I've tried changing xorg.conf but that caused my machine to grind to a halt and I had to copy the original .conf file back over before I could launch GNOME again. I've run lspci | grep VGA, and this is what I get:

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

When I run xrandr --verbose, I get:

Screen 0: minimum 800 x 576, current 800 x 576, maximum 800 x 576
default connected 800x576+0+0 (0x108) normal (normal) 0mm x 0mm
    Identifier: 0x107
    Timestamp:  30685
    Subpixel:   horizontal rgb
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  800x576 (0x108)    0.0MHz *current
        h: width   800 start    0 end    0 total  800 skew    0 clock    0.0KHz
        v: height  576 start    0 end    0 total  576           clock    0.0Hz

The display GUI is useless!

Does anyone know how I can progress?

I'm trying to install Photran for Eclipse 3.6. I've managed to get 3.6 and it works but the next step involves choosing a package that I just can't see because my screen resolution is too small.

Kind regards,

Phillip

---

### Post by phillip4672 on 2011-05-29
Hi,

I've updated my story on a different post. You can find it here:

[http://ubuntuforums.org/showthread.php?t=1758850](http://ubuntuforums.org/showthread.php?t=1758850)

...Still not getting anywhere though!

Kind regards,

Phillip

---

### Post by RutRow on 2011-06-12
Any update on getting the Dell Mini 10 to work with Natty Narwhal?

I have it working only at 800x600 and it would be great to get back to full resolution.

[COLOR=#000000][FONT=Ubuntu][COLOR=#1A1A1A]**




[/COLOR][/FONT][/COLOR]

---

