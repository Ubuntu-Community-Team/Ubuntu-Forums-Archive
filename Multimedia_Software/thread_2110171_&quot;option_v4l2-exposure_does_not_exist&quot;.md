---
title: "&quot;option v4l2-exposure does not exist&quot;"
date: 2013-01-29
forum: Multimedia Software
---

### Post by grey1beard on 2013-01-29
I'm using VLC to grab a time lapse sequence, which is currently running OK on another laptop.
At the end of the code instructions, Terminal posted

> VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
0x8ed83a0: dummy interface: using dummy interface...
option v4l2-exposure does not exist

The jpegs are being saved as demanded, but I'd like to know what the option that doesn't exist is, and should I do something about it ?

John

---

### Post by tgalati4 on 2013-01-29
If this is a webcam or laptop camera then the camera probably has autoexposure and video-4-linux is telling you that you can't pass an exposure value.

If you want to fine-tune your video captures, there are some tools you can load:

```
apt-cache search v4l2
apt-cache search vole
```

Which brings up a list including:

qv4l2 - Graphical Qt v4l2 control panel
uvcdynctrl - Command line tool to control v4l2 device

Apparently no voles are in the repository.

---

### Post by grey1beard on 2013-01-30
Hi tigalati, and thanks for the heads up on the absence of any vole infestation in the repositories :)

Managed to get a rather poor quality video set up this morning that shows us the mouse, for it is he - not the vole - who is gathering.

So I'll stop worrying about what hasn't actually had any impact on getting the information we need at the first attempt. First we know it's a mouse, and secondly the time it appears, and also has naps in the bag !
I think I also messed up the frame size and it might have gone to a default setting

All very curious behaviour, but I shall continue, and when we've got a decent short vid, I'll post it at the watercooler, perhaps ?

Thanks for your help. I'm now looking at rigging up my canon G2 for a higher resolution sequence, rather than the logitech quickcam, and will start researching how to time delay the start and finish of the capture.
regards
John

---

