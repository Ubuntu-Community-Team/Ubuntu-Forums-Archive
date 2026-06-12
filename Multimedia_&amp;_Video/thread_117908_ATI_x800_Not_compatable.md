---
title: "ATI x800 Not compatable?"
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by Kieffer87 on 2006-01-15
Just wondering, it would cause xserver not to load. I took it out, put my old x300 in and it booted right up. Any work arounds for this?

---

### Post by Zimmer on 2006-01-15
[QUOTE=Kieffer87]Just wondering, it would cause xserver not to load. I took it out, put my old x300 in and it booted right up. Any work arounds for this?[/QUOTE]
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)
According to the How-to the X800 is a supported card.
Old advice here
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)
for the X700Pro mentions changing the Device in xorg.conf to vesa to get X to start, then loading the binary drivers.
What is the rest of your machine spec?
Regards

---

### Post by Kieffer87 on 2006-01-15
P4 3.0 w/HT, 1GB ram, 40GB and 200GB drives, Its a Dell Dimension 4700. Ill have to check out that thread later on tonight.

---

### Post by Kieffer87 on 2006-01-22
Thanks alot that fixed my problem!

---

### Post by daradib on 2006-10-21
Try this:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

---

