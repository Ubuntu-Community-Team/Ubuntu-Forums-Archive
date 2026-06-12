---
title: "DivX Problem when switching into full screen..."
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by tool666 on 2007-10-04
Hallo!!! i have a problem when switching into full screen (with totem and VLC). At the black boarders i see weard lines and colours... Has anyone a solution for this issue? By the way i'm using Ubuntu 6.06 dapper and Compiz. I am pretty new into this so please if it is a stupid question don't laugh at me. Thank's.

---

### Post by distroman on 2007-10-04
Hi I don't think anyone are going to laugh. ;-)
Try to run without compiz (switch to metacity) see if it makes a difference. 
If it does there might be fixes though the easy one would be don't run compiz. :-)

---

### Post by Jive Turkey on 2007-10-04
I find that Mplayer works better divX than the others, this may not be the problem however.  looking at you video driver config settings might be helpful.

---

### Post by Gremlinzzz on 2007-10-04
How to fix black windows during video playback

    * There is a workaround to this bug by changing the video output device on your video player. 

    * For gstreamer-dependent players (Totem, etc.): 

gstreamer-properties
Video-->Default Video Plugin: X Window System (No Xv)

Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).

    * For VLC player(if installed): 

VLC-->Settings-->Preferences
Video-->Output modules-->Advanced: X11

    * For MPlayer (if installed): 

Mplayer-->Right-click on the screen-->Preferences
Video-->Available Drivers: X11 (XImage/Shm)

Some users report that MPlayer may not be able to show videos in full screen.

    * For Xine player (if installed): 

Xine-->File-->Configure-->Preferences
experience_level: Master Of The Known Universe
Video-->Driver: xshm 

    * For RealPlayer (if installed): 

RealPlayer-->Tools-->Preferences
Hardware-->Deselect: Use XVideo

---

### Post by tool666 on 2007-10-05
Thanks to you all. You helped me out. Hope some day i will be able to help help others too!!!
UBUNTU forever...

---

