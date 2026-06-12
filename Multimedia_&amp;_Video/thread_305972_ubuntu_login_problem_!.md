---
title: "ubuntu login problem !"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by happyweb on 2006-11-24
hi there,

i have a 32 MB nvidia Riva TNT2 Model 64, graphic card with intel 845 HVWN motherboard with pentimun 4 , 1.7 GHz
with 512 SD RAM.

i successfully install nvidia drivers using automatix2 on Ubuntu 
6.10 edgy ,and it asked to restart.

ans since then , it only shows me a grey screen with nothing happening ...

please help

either to change some settings or restore previous default login

thanks in advance

---

### Post by spd106 on 2006-11-25
To restore the old settings their should be a backup copy of the xorg.conf file created by automatix during install.

Press **Ctrl + Alt + F1** or otherwise get to a terminal login. 
Enter your details then navigate to the X11 folder, **cd /etc/X11/**. 
Type **ls** to see if there is a backup xorg.conf file. If there is then type **sudo cp -v xorg.conf.??? xorg.conf** to restore the old settings. 
Now type **sudo /etc/init.d/gdm restart**.

Otherwise you could try **sudo dpkg-reconfigure xserver-xorg**.

---

