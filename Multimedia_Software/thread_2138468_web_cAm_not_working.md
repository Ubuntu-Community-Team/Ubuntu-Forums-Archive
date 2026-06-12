---
title: "web cAm not working"
date: 2013-04-24
forum: Multimedia Software
---

### Post by Nadarasan on 2013-04-24
I AM using zebronics webcAm. it is not working after trying gstreamer properties-multi  mediA selector.I t shows the following error.
Video for Linux 2 (v4l2): Could not get buffers from device '/dev/video0'.
the web cam does not open with cheese ,camorama and webcam.

i do not see any folder video 0 or video1 in /dev

---

### Post by midnightramen on 2013-04-25
I think I had a similar issue a few months back, and what could be happening is that your webcam may be using /dev/video1 or something similar. I think I had ultimately solved it by moving / renaming the /dev/video1 to /dev/video0 : sudo mv /dev/video1 /dev/video0 . I would suggest caution before running this command however, just in case some other device that may be using /dev/video0

You may want to see this post for more info: [http://ubuntuforums.org/showthread.php?t=1995940](http://ubuntuforums.org/showthread.php?t=1995940)

---

### Post by Nadarasan on 2013-04-26
i donot see any folder video o or video1 in/dev

---

