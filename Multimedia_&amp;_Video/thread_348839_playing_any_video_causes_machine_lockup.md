---
title: "playing any video causes machine lockup"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by shrimphead on 2007-01-29
having a bit of a wierd issue in edgy that's making me ](*,) 

everytime I try and play a DivX an XVid or a WMV encoded video, or a DVD it plays fine for a few minutes (seems to vary between 3 and 10) and then my machine locks up. 

no keyboard input or mouse input is detected, Ctrl-alt backspace doesn't work and my only solution is to hard reset the machine.

I have tried this with many different media files, and players. I have used VLC, totem (with gstreamer-plugins-ugly installed), Xine, mplayer from the repos and a compiled SVN snapshot of mplayer and the results are the same every time.

If anyone has any idea then please let me know. if there is any more information I can provide let me know also :)

thanks in advance all :)

---

### Post by an.echte.trilingue on 2007-01-29
This tends to be my answer to everything, but this has got to be your video card.  What is it?  Have you got the driver installed/working?

---

### Post by shrimphead on 2007-01-29
it's an ati radeon X1600xt, with fglrx drivers installed. seems to work ok, I can run compiz beryl and the like, but good thinking, I am using a custom compiled fglrx, so I'll try reverting to one from the repos :) will let you know

---

### Post by shrimphead on 2007-01-29
that was the exact problem. rolling back to edgy's fglrx driver fixed the problem...I completely forgot I had rolled my own drivers :S

---

