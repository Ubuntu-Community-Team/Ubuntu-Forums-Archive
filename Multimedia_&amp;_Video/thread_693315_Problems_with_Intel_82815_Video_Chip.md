---
title: "Problems with Intel 82815 Video Chip"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by vroberts on 2008-02-10
I'm new to Ubuntu.  I just installed 7.10 on a system that has an Intel D815EEA2 board with integrated graphics provided by the Intel 82815 chip.  When used with a Viewsonic V920b 1280x1024 LCD monitor via a KVM switch there are multiple vertical lines on the display and it cannot be set to its native resolution.

A Google search indicates that this is or was a known problem with older versions of Ubuntu. 

Using the same computer, same monitor and same KVM switch I do not have any problems with the board is running Windows.

The lines go away if I use a 1024x768 NEC monito.  When using the NEC monitor I do not use the KVM switch but I think the problem is the resolution I need for the Viewsonic monitor, not the KVM switch.

Does anyone know if the 82815 can be made to work with Ubuntu with some combination of settings? 

Thanks,

Vic Roberts

---

### Post by Michl on 2008-04-08
Yes, you can.  I did it.  What I had to do was to edit 
xorg.conf.  In 
```
Section "Screen"
```
change
```
Defaultdepth        24
```
to
```
Defaultdepth      16
```

don't change anything else and restart.
See if that works.

To edit this file you need to be in root.   In the
terminal enter
sudo gedit /etc/X11/xorg.conf

Also, just in case, save your old xorg.conf file as a backup,
e.g. xorg.conf_backup

Michael

---

