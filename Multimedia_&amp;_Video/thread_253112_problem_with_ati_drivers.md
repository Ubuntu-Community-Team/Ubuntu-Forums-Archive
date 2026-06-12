---
title: "problem with ati drivers"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by lime4x4 on 2006-09-07
I had the lastest ati drivers installed and running and now they don't seem to be working so i reinstalled the drivers and i'm still getting the same error

john@ubuntu:~$ fglrxinfo
Error: unable to open display :0
john@ubuntu:~$
Edit/Delete Message 

But when i change the following line to this in xorg.conf
Identifier "aticonfig-Screen[0]"
Xserver crashes and i have to reboot into recovery mode and then with nano change it back to "default screen"

---

