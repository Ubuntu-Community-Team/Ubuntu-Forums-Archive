---
title: "Eyetoy USB webcam - ERROR &quot;cannot open device (No space left on device)&quot;"
date: 2008-05-26
forum: Multimedia Software
---

### Post by Larir on 2008-05-26
Hello,

I just bought a new USB headset and it seems that I can not use my Eyetoy as a webcam anymore, or at least cannot use it at the same time with the headset. I'm using the hacked ov51x-jpeg driver from rastageeks.org (version 1.5.7), installed with the instructions from help.ubuntu.com.

I'd like to be able to use this headset and my webcam to call people on Skype and let them see me. Running vlc from command line and opening the camera that way gives me this error:

```
[00000294] v4l demuxer error: cannot open device (No space left on device)
```

This only happens when I plug in the headset and the camera at the same time... I tried moving them around the USB ports but it doesn't help, I also moved my MX500 mouse from an USB port to a ps/2 port so now I have 2 free ones. 

Other USB devices I have are my printer and a Huawei 220E 3G modem. Does anyone know how I can get some space free for the camera or make it work with the space it has? I've already tried taking out everything else except the camera and the headset, still no go. :(

Any help is appreciated. Thank you. :|

---

### Post by Larir on 2008-06-01
*bump*

Still have this problem... noone knows any solution?

---

### Post by gmfood4 on 2009-09-30
The problem is that Linux command **df -i** shows that there are too many files on the filesystem and **all the "inodes" are used.**

Look at en.wikipedia.org/wiki/Inode

This problems usually occurs with tar, because this is one of the greatest file creating programs :D

Check the solutions for your filesystem what to do when out of inodes.

Hope this helps.

---

