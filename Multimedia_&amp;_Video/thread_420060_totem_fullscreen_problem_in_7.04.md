---
title: "totem fullscreen problem in 7.04"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by genie on 2007-04-23
I have a problem with playing videos in totem in ubuntu 7.04.The problem occurs when I switch totem  into the fullscreen mode the video resolution stays the same, not streched. i was looking for the solution and I have found it here: [Click_here]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/108411") . However I cannot find the "X11/XShm/Xv" directory and therefore cannot change the values. Anybody could help me? Thanks in advance:)

---

### Post by GeDaMo on 2007-04-24
In a terminal, type 
```
gstreamer-properties
```
You can change the Default Output plugin to X11/XShm/Xv under the Video tab.

---

### Post by genie on 2007-04-24
Yeah! It works:) Thanks GeDaMo :)

---

