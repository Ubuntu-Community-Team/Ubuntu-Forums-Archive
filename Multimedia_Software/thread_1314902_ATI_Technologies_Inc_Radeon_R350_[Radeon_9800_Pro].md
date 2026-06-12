---
title: "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
date: 2009-11-04
forum: Multimedia Software
---

### Post by mebcs on 2009-11-04
I have searched and searched.  I can't get the TVtime viewer to detect my card.

lspci -nn| grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] [1002:4e48]

glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

I just switched the system from Windows XP Pro to Ubuntu 9.10....Best Move Ever.

sudo nano /etc/X11/xorg.conf
This produces a new file. As I understand my research this file no longer exist.

sudo aticonfig --initial
sudo: aticonfig: command not found
This should also be normal since the xorg-driver-fglrx, old driver, is not present.

Any help would be great.  I am a newbe so details would help.

---

