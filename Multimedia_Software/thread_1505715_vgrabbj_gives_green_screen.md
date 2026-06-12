---
title: "vgrabbj gives green screen"
date: 2010-06-09
forum: Multimedia Software
---

### Post by enuckon on 2010-06-09
Hello,

Could anyone suggest how to get vgrabbj to start feeding images from a webcam to stopmotion?  What I get now is all green screen, both in stopmotion and vgrabbj:

"
tam:~$ vgrabbj -f test.jpg -d /dev/video0 -i vga -F 1 && eog test.jpg
Unable to set palette
Unable to set palette
Unable to set palette
Reading image from /dev/video0
There was no map allocated to be freed...
"  
--  Gives a green window.

This is Logitech Quickcam 3000 RT.  Is there a better suiting grabber for this camera?  

Would appreciate any suggestion.
E.

---

### Post by ripat on 2010-08-13
Hi,

I just had the same problem and found a solution here:
[https://bugs.launchpad.net/ubuntu/+source/vgrabbj/+bug/364744](https://bugs.launchpad.net/ubuntu/+source/vgrabbj/+bug/364744)

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vgrabbj -d /dev/video0 -f outputfile.jpg
```

---

