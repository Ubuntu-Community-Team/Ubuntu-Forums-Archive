---
title: "reserving  /dev/video0"
date: 2011-12-01
forum: Multimedia Software
---

### Post by Dilutu on 2011-12-01
Hi there
Running 10.04 on my desktop with 2 video devices. one is a tv card configured as /dev/video0, the other a usb webcam as /dev/video1 .But sometimes they get mixed at startup , and tvtime does not work. How could I reserve /dev/video0 for my tv card?
Th.

---

### Post by azmyth on 2011-12-01
You can set a udev rule that will assign each video device to a symbolic link that you create in the udev file. No matter what it changes to video0 or video1 it will assign to the link.

---

### Post by Dilutu on 2011-12-01
Thank you.I looked at my udev rules, but could not figure out how to make my own.(any examples ....?)
Th.

---

### Post by Dilutu on 2011-12-01
Well I found a lot of info about writing my own rules. Got to read and learn smore . will report back....
Th

---

### Post by Dilutu on 2011-12-02
well, made some headway:I wrote a couple of udev rules that work good when tested with vlc. But tvtime still wants to open the wrong device, even though I edited its config file "/etc/tvtime/tvtime.xml" to point to the symlink created in   /dev.
Th.

---

### Post by timsdeepsky on 2011-12-02
Maybe this could help....
[http://ubuntuforums.org/showthread.php?t=1390061]("http://ubuntuforums.org/showthread.php?t=1390061")

---

### Post by Dilutu on 2011-12-02
Yep thanx thats one of the threads I used to create my udev rules. Now I narrowed the trouble  to tvtime since vlc work good with the symlinks created.If I unplug my webcam ,then tvtimes starts ok...
Th.

---

