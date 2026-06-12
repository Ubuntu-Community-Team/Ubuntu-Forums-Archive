---
title: "Wireless in 8.10"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by cptaszek on 2009-10-21
I've always been trying to figure out how to set up a wireless internet connection in Ubuntu 8.10. Can someone help out?:confused:

---

### Post by matyd on 2009-10-21
You will probably need to give alittle more information than that... Do you have a wireless router?

---

### Post by jward3010 on 2009-10-21
And more importantly a wireless card in your laptop, do a:
```
sudo lshw -C network
```
Post what you get.

---

### Post by Sylslay on 2009-10-21
[http://ubuntuforums.org/showthread.php?t=488779](http://ubuntuforums.org/showthread.php?t=488779) , good answers

hit alt-f2 and type:
nm-applet --sm-disable

[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)
:guitar:

in terminal : what command do?
ifconfig:

show wlan0, or 
if no wirless-extention, than no drivers for Yours wi-fi, in kernel

---

