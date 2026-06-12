---
title: "After upgrading fglrx does not redraw most (see attachmet)"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by TTL on 2006-06-11
Hello,
with Kubuntu Breezy I managed to get 3D with the fglrx module working. I had upgraded to X.org 6.9 under Breezy before.
Now under 6.06 X.org still starts with the fglrx module but the desktop is not redrawn often. In fact I can not work with 3D acceleration any longer. See attachment how it looks like. Note that I did not upgrade the X.org server. So I can not explain me why X.org behaves now different. ](*,) 
The logfile of X.org fist tells me that libglcore could not be loaded but after loading fglrx it seems like libglcore is loaded properly again. Except not founding synaptics no further error messages are in the logfile

Any clues?

---

### Post by TTL on 2006-07-16
Still no idea?
I updated to the last fglrx driver (8.26.18 ) but it does not change anything. Moreover I found out that you can make even screenshots from the wrong screen (if you now where the invisible buttons are).](*,)

Update:
OK, i found out that 3D acceleration works fine if I set Option "OpenGLOverlay" to "off". ;)

---

