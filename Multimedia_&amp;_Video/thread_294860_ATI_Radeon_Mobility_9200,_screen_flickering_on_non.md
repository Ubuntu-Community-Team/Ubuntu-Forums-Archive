---
title: "ATI Radeon Mobility 9200, screen flickering on non-native LCD resolutions."
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by panxer on 2006-11-07
Hello, 
I am using Ubuntu Edgy on a HP nx7000 laptop.

When using the fglrx driver for the ati radeon mobility 9200, i get a flickering screen on *every* resolution except my LCD screen's native resolution ( 1680x1050 ).

The "ati" driver works perfect on every resolution, but there is no 3d DRI on that driver.

Info about my VGA.

```

panxer@gryppas:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
panxer@gryppas:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9200 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

```

glxgears output.

```

panxer@gryppas:~$ glxgears 
10910 frames in 5.0 seconds = 2181.849 FPS
10853 frames in 5.0 seconds = 2170.519 FPS
10844 frames in 5.0 seconds = 2167.417 FPS

```

My xorg.conf.
[http://ubuntuforums.org/attachment.php?attachmentid=19036&stc=1&d=1162908987](http://ubuntuforums.org/attachment.php?attachmentid=19036&stc=1&d=1162908987)

xvidtune output.
```
panxer@gryppas:~$ xvidtune -show
"1680x1050"   121.50   1680 1712 1800 1872   1050 1051 1054 1065


```

As you can see from my xorg.conf i have manually inserted the ModeLines for 1680x1050 (the resolution i use the most, and is my laptop's native) and 1024x768 (that i use for specific applications).

I get mass screen distortion when i use 1024x768 or *any* other resolution.

It gets *very* annoying especially when i try to use my S-video-out in clone-mode. My Xorg server can only work @ 1024x768 to give signal in that mode. The output on the device attached to the S-video is perfect but the laptop's screen @ 1024x768 is unusable due to the flickering.

Any thoughts on how to solve this problem?

---

### Post by panxer on 2006-11-12
Still no solution.

---

### Post by panxer on 2006-11-20
* up *

---

### Post by panxer on 2006-12-04
Another bump.
I ve tried everything, but still i get the flick.

---

### Post by Racerdog on 2007-02-21
Some screen flickering problem are due to RFI (Radio Frequency Interferrence).  Check if there are other hi-frequency devices located near your display. Things like Routers, switches, Electrical Cables, even Wireless communication devices. If so, take a piece of aluminim foil and place it at various locations around the devices and/or screen. Check to see if the screen flickering goes away. The alum foil acts as a shield by bouncing off the random radio waves and allows the screen to do it's job. Remember, the inteferring devices don't have to be right next to the screen. They are usually located somewhere in the same room but can be as far away as out in the street depending on the frequency bursts.

---

