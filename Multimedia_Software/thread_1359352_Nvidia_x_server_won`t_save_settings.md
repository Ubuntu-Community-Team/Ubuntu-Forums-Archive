---
title: "Nvidia x server won`t save settings?"
date: 2009-12-19
forum: Multimedia Software
---

### Post by shawnduncan on 2009-12-19
Just got a new install of Ubuntu set just the way I like it but whenever I click on "Save to X configuration file" I get a window that says "Failed to parse existing X config file '/etc/X11/xorg.conf'!" 

This is on a Wubi install of Ubuntu using Nvidia`s settings program.
I looked at the file and its listed as read only? How do I change this since it tells me I dont have permission.

Any help would be awesome!

---

### Post by HappyFeet on 2009-12-19
Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by shawnduncan on 2009-12-19
HappyFeet,
Thanks! That did the trick!

---

### Post by Tethtibis on 2010-02-14
That Fixed me right up as well, Thanks, HappyFeet. :O)

---

