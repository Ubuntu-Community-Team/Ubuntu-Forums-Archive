---
title: "New to Ubuntu *replaced video card*"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by Roc327 on 2007-07-17
I installed Ubuntu with an ATI x1300 pci card.  Now I have an Nvidia GeForce 7900 GT PCie card installed but of course the x server will not start.  I ran envy from terminal to install nvidia drivers and no go still not able to start xserver.  Is there a way to get ubuntu to reuse generic drivers to load xserver?

Thanks

---

### Post by RomeReactor on 2007-07-17
Hi. Maybe this will help: from the command line enter:
```
sudo apt-get install xserver-xorg-video-nv
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
if it asks you what driver to use, choose **nv**; and
```
sudo /etc/init.d/gdm start
```
if that doesn't take you to your desktop, try:
```
sudo reboot
```

---

### Post by Roc327 on 2007-07-17
Thanks a ton. That fixed the problem.

---

