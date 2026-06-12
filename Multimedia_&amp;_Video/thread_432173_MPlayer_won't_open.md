---
title: "MPlayer won't open"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by onedeep713 on 2007-05-03
Every time I try to open MPlayer it opens and closes right away. How do I fix this?

---

### Post by taurus on 2007-05-03
Try to run it from a terminal to see what the error message is.

Applications -> Accessories -> Terminal
```
mplayer
-or-
gmplayer
```

---

### Post by onedeep713 on 2007-05-03
This is what I get when I try to run gmplayer:


MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
98 audio & 216 video codecs
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

---

### Post by taurus on 2007-05-03
From a terminal, edit ~/.mplayer/gui.conf

```
gedit ~/.mplayer/gui.conf
```
and change the line regarding **gui_skin** from whatever it is to make it looks like this now.

```
gui_skin = "Blue"
```
Save it and run **gmplaye**r again from that terminal and see what happens.

---

### Post by onedeep713 on 2007-05-04
gui_conf is blank

---

### Post by focus1974 on 2007-05-04
I experienced similar problems but strangely, all the gurus here have been dishing out comments about checking your config file and etc.

BUt anyway, after trying out all the methods... I finally found my problem....
I had Desktop Effects Enabled (the wobbly window thingy). 
I Have a intel gm 845 range of graphic card ...so that might be the problem?...
but i dont think i want to delve into the subject anymore.
I'll just permanently turned off the DEsktop EFfects and get my Video back. :)
YOU might want to give it a try.

---

### Post by onedeep713 on 2007-05-05
I love the desktop effects. I just won't use MPlayer. VLC and Totem are working just fine...

---

### Post by speacock on 2007-05-22
I was experiencing this same problem. My gui.conf file had entries, and changing the gui_skin to "Blue" did nothing. 
I finally looked at the contents of the ls /usr/share/mplayer/Skin/ directory and found that I had  three sub directories here: clearplayer, default and mini. 
The default directory was empty, and hence I guess why I was getting the error message, and also there was no Blue.

I changed the gui_skin default to "clearplayer" and now gmplayer works fine. :D


Steve

---

