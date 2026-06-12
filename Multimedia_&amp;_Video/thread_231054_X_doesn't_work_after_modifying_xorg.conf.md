---
title: "X doesn't work after modifying xorg.conf"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Phantom784 on 2006-08-06
Everything was working fine, except I couldn't get direct hardware access to my ATI Rage 128.  Based on advice from irc, I went in xorg.conf and chaged the driver line under section "Device" from vesa to ati.  I then restarted X, but it wouldn't come up.  I fixed the line, but X still won't come up.  Whenever I start my machine, it goes through the loading screen, but when it is done, the loading bar jumps to empty and it just sits there.

---

### Post by mogwai on 2006-08-06
Restore your backup of xorg.conf (you did make a backup didn't you?) or you can go to a virtual console (Ctrl+Alt+F1), login and type "sudo dpkg-reconfigure xserver-xorg" (without the quotes).
This should re-create your xorg.conf
Then see [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) or [http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320) to see how to install the ATI driver.

---

### Post by mogwai on 2006-08-06
I just came across this link:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Phantom784 on 2006-08-06
dpkg-reconfigure told me that xserver-xorg isn't fully installed (maybe this is because i'm using kubuntu).  i changed the line back, so I don't see how xorg.conf could be the problem.

---

### Post by tseliot on 2006-08-07
Type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```


and make sure that you don't have a xorg.conf in your home folder:
```
cd $HOME
```

```
sudo rm xorg.conf
```


Then restart the Xserver:
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)

---

