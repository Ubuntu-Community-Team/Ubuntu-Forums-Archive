---
title: "Nvidia drivers don't work with upgrade"
date: 2009-10-23
forum: Multimedia Software
---

### Post by hnick on 2009-10-23
I'm using the Hardy (8.04) distribution and upgraded from 2.6.24-24 to  2.6.24-25 with new restricted NVidia video drivers. The new configuration can not get past 800x600 resolution. When I boot the 2.6.24-24 kernel, I get 1280x1024 resolution. The video card has a NVidia GeForce 8500 GT chip set. Does anybody have any suggestions? 
Thanks

---

### Post by vinutux on 2009-10-23
System > Preferences > Display

---

### Post by sleon on 2009-10-24
Same problem here.  Does anyone have any suggestions?

---

### Post by hnick on 2009-10-24
"System > Preferences > Display" does not work. I can now only get 640x480. Anybody have any other suggestions other than write my own drivers?

---

### Post by vinutux on 2009-10-24
Backup then play withxorg.conf
```
gedit /etc/X11/xorg.conf
```
 search forums and try a bit of googling....

---

### Post by izg on 2009-10-24
I have a similar issue with ATI.

After updating Hardy Heron 8.04, my video driver no longer works.  I've downloaded the latest installer from ATI and still no luck.

---

### Post by Kubro on 2009-10-24
I had a problem like this, the system>preferences>display doesn't work, so in terminal sudo nvidia-xconfig
then logout of your session and when you log back in go to system>administration>nvidia X server settings. I've been using this to control my display and for dual monitor display and it's been great. Hope this is helpful.

---

### Post by hnick on 2009-10-25
Some success finally! /etc/X11/xorg.conf was overwritten.

I tried 
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
and it replaced the xorg.conf with one that worked. I'm now back at my usual 1280x1024. I also reinstalled the restricted driver package. You may or may not have to do that. 
Thanks all.

---

