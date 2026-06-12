---
title: "sony DSC W270 not recognized"
date: 2011-06-09
forum: Multimedia Software
---

### Post by onetwothreecool on 2011-06-09
I got a sony DSC W270 digital camera. It is not being detected even when put in PTP mode. gthumb doesn't recognize my camera, and though gtkam shows the cam's name and stuff correctly, it automatically closes when i try to double click on the name listed. Shotwell Photo Manager automatically closes just like gtkam

any help would be highly appreciated

Thanks in advance

---

### Post by eric-yorba on 2011-06-09
By "automatically closes" are we talking about a crash?  I'm not seeing that camera as listed by GPhoto, which is the library used by Gnome-based applications for camera access:
[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

That said, it still shouldn't crash.  This sounds like a GPhoto bug if both Shtowell and gtkam crashed.

Can you pop out the memory card and import directly from there?  (It's usually faster anyway.)

---

