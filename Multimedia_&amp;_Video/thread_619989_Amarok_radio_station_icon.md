---
title: "Amarok radio station icon?"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Romanus81 on 2007-11-22
Is there any way I can create a desktop icon that will run an online radio stream in amarok?

---

### Post by guziec on 2007-11-22
Create file on your desktop:
```
cd ~/Desktop
gedit radio.desktop
```
and paste this
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Radio kpan.com
Type=Application
Terminal=false
Exec=amarok mms://64.92.199.74/KPAM-AM
Icon=amarok.png
```

---

