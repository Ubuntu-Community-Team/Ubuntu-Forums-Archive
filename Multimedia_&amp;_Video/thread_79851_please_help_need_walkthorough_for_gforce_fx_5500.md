---
title: "please help need walkthorough for gforce fx 5500"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by nal on 2005-10-21
I have the gforce fx 5500 and every time i try to install the video drivers i cant seem to do it.  Either it says Im still in x windows or something. Or when i do apt-get install nividaglx Think thats the command, it install but then when I boot all i get is a black screen.  If someone could help me please get this working right It would be very helpfull indeed and I will be very thankfull.  I love linux, and cant wait to get this fixed so i can play games  :)

---

### Post by yage on 2005-10-21
As stated on ubuntuguide.org:
```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```
Reboot....
Hope this helps

---

### Post by SparkyDawg on 2005-10-22
I have had the same problem with the black screen and I am sure I have installed the drivers in correctly.

---

### Post by ben-g on 2006-08-02
I'm having trouble installing my gforce fx 5500, also. I folowed the guide, but for some reason I can't install nvidia-glx without uninstalling nvidia-settings and vice versa. If you could help I would be very thankful.

---

