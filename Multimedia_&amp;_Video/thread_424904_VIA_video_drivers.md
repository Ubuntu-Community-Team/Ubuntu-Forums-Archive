---
title: "VIA video drivers?"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Vorstvingers on 2007-04-27
Hi guys,

Ubuntu is running quite well on my computer, except for the fact that it does not perform graphical tasks very well. Full screen playing of movies or of, for example, a screen saver results in a quite slow refresh rate.

```
glxinfo|grep direct
```results in```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```so I figure it has something to do with not properly installed video drivers or something like that. 

Furthermore,```
lspci | grep VGA
```results in```
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3230 (rev 11)
```so the (on board) video card chipset seems to be VIA.

After consulting another forum I already tried to edit /etc/X11/xorg.conf by changing *Driver         "vesa"* into *Driver         "via"* but after rebooting this only resulted in X not being able to launch anymore, so I changed it back to its original value.

Anyone here any suggestions how to fix this? Thanks in advance!

---

### Post by Vorstvingers on 2007-05-01
I have also tried```
sudo dpkg-reconfigure xserver-xorg
``` with default settings (except that I entered 'via' instead of 'vesa' for chipset) but this also caused X to fail to start up. 

Any suggestions?

---

