---
title: "Webcam - X crash"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Xmister on 2007-03-27
Hi all
I'm trying to get my webcam working on feisty beta(but it was doing the same on edgy)
When I'm trying to start a webcam program(eg. xawtv) X crashes and give me a full black screen, I have to Ctrl+Alt+Bkspace to restart X, v4l-conf doing the same.
xawtv hwscan: > $ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-13-386)
looking for available devices
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : SN9C10x PC Camera
    flags:  capture

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : BT878 video (Leadtek WinFast 20
    flags: overlay capture tuner


I tried it with another cam, the same thing.

---

### Post by Xmister on 2007-04-06
I figured out, that's only happens when the fglrx driver loaded. Are there any option about v4l in fglrx which can do this?

---

