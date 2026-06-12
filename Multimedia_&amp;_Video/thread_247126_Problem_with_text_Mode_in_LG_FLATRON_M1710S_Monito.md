---
title: "Problem with text Mode in LG FLATRON M1710S Monitor"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by blixy on 2006-08-30
I faced a problem during Ubuntu 6.06 boot up and also when I switch to text mode with LG FLATRON M1710S Monitor. This monitor doesn't show anything in text mode. Fedora Core 5 has no problem with it.
System's graphic card is nVidia GeForce 6600. any comment? :-|

---

### Post by blixy on 2006-09-02
By editing /boot/grub/menu.lst I solved the problem.
I just added "vga=0" to the end of kernel line.
The only downside is that usplash won't load this way.

---

