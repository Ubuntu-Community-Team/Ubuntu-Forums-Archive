---
title: "User/Graphics issue"
date: 2010-04-06
forum: Multimedia Software
---

### Post by yahalimu on 2010-04-06
Hi y'all.
I recently installed ubuntu 9.10 dual boot.
All went well until I upgraded the video drivers for the nvidia chipset on my motherboard.

If I leave Gnome to start with the single user i created i get a black screen and 'mode not supported ' message on the monitor.

BUT if i drop to root and 'startx' all is well and i can adjust the various screen resolutions and they all work well.

At this point i created another user name to check, and that works fine also, but if i drop back to the original user i get no screen unless i select 800x600, although all the other resolutions work fine with root and the other user name.

Im stumped as I presume there's only one xorg.conf file for all users.

Any suggestions?

---

### Post by lidex on 2010-04-06
Did you make a custom xorg.conf? Try renaming it:
```
sudo mv /etc/X11/xorg.conf xorg.conf.old
```
Restart and see how it goes. Problems?
```
sudo nvidia-xconfig
```

---

