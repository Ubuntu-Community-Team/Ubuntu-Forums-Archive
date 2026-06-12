---
title: "Blank Screen [ATi x700]"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by Frolicated on 2006-06-14
First off, I'm an absolute Linux novice.  That said, I've installed Dapper Drake 6.06 in safe graphics mode and after following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) to install the drivers I have no luck.  When I reboot I hear the startup sounds, but cannot get to a GUI.  Any help is greatly appreciated.

---

### Post by halcyon-life on 2006-06-14
[QUOTE=Frolicated]First off, I'm an absolute Linux novice.  That said, I've installed Dapper Drake 6.06 in safe graphics mode and after following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) to install the drivers I have no luck.  When I reboot I hear the startup sounds, but cannot get to a GUI.  Any help is greatly appreciated.[/QUOTE]

try [this]("http://www.ubuntuforums.org/showthread.php?t=187177") or [this]("http://www.ubuntuforums.org/showthread.php?t=195108") thread.


sounds like it might be a problem with Xorg.conf in /ect/X11

check out the settings in xorg.conf with the code:
sudo nano /etc/X11/xorg.conf
and check resolution and refresh rates. save, exit and type startx to restart the xserver

---

### Post by Frolicated on 2006-06-14
[QUOTE=halcyon-life]try [this]("http://www.ubuntuforums.org/showthread.php?t=187177") or [this]("http://www.ubuntuforums.org/showthread.php?t=195108") thread.


sounds like it might be a problem with Xorg.conf in /ect/X11

check out the settings in xorg.conf with the code:
sudo nano /etc/X11/xorg.conf
and check resolution and refresh rates. save, exit and type startx to restart the xserver[/QUOTE]
I solved my problem, thank you very much.

---

