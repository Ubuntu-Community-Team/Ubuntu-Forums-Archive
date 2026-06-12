---
title: "how to disable sound card and touchpad"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by FISH on 2006-06-22
I have two sound cards in my laptop HDA intel and Realtek ALC2600. I would like to disable one because I think that one of the software I use, chooses realtek as its sound card, and the sound it horrid. Also I use a usb mouse, in the last ubuntu I didnt have problems but now my cursor jumps all over the place and my best guess is because my fingers hit the touch pad, so where would I comment out the touchpad?

---

### Post by warbread on 2006-06-22
Go into xorg.conf and your touchpad should be listed under "InputDevices".  There should be more than one such section, and the one you want (I think) will be listed as "Synaptics Touchpad".  That's mine, anyways.  I'm sure you can just comment that whole section out.

---

### Post by jonathantneal on 2006-06-23
Any help disabling the soundcard?  We're having the same problem @ [http://www.ubuntuforums.org/showthread.php?t=200452](http://www.ubuntuforums.org/showthread.php?t=200452)

---

