---
title: "Ubuntu 10.04 Hangs While Trying to Transfer Photos and Videos From Digital Camera"
date: 2010-09-10
forum: Multimedia Software
---

### Post by shinkaide on 2010-09-10
Ubuntu Hangs While Trying to Transfer Photos and Videos From Digital Camera

Hi, I have a Canon Powershot S3 IS and I've been trying to transfer photos and videos (13 gigs worth) from it to a local folder (I'm currently using Ubuntu 10.04) via USB cable.

I've had very little success - I've only transferred one video file, everything else failed, including a single photo transfer attempt!

First it would take really long for the actual transfer to start after I've dragged and dropped files from the camera to a local folder (or even doing ctrl+c and ctrl+v). The progress bar would appear, but then it would take forever before the file transfer would start. 

In the case of the single video transfer, it started and finished after a while. But when I selected all of the videos on the camera and tried to transfer it all, it would just take a really long time, slow down gnome to the point of hanging, and then eventually just show me an error message indicating nothing could be transferred. 

Help, please?

---

### Post by Mary B on 2010-09-10
Powershot A450 transfer also does not work.

---

### Post by Mary B on 2010-09-10
More specifically, F-Spot can be launched, however, when selecting import, F-Spot immediately closes. I simply don't know how to get photos from my camera since updating to 10.04. Help appreciated.

---

### Post by rg_stephens on 2010-09-10
This only happens to this computer? The first thing that comes to mind is a defective cable. F-Spot might have a problem. I usually drag-and-drop within windows. Does this work?

---

### Post by MaskedMarauder on 2011-10-26
no, the problem is that it tries to copy the file into memory before it transforms it.  In the case of videos, at least, that can be sever gigs.  Watch your memory when you try to copy or move a video.  It goes to zero and then devours the swap space.  Unless you have a humungous swap file or ridiculous amounts of memory, it won't work.

---

