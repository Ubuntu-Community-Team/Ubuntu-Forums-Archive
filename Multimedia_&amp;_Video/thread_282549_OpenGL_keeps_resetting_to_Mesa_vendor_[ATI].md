---
title: "OpenGL keeps resetting to Mesa vendor [ATI]"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by Sehnsucht on 2006-10-22
Here's the problem:

After installing the ATI FGLRX drivers and running and configuring the following:

```
sudo dpkg-reconfigure xserver-xorg
```

I reboot and 3d works fine. glxinfo | grep OpenGL and glxinfo | grep direct return the correct answers (OpenGL vendor is ATI, correct driver version, direct rendering is a yes).

However, after a while it resets to how it was before I installed the ATI drivers -- Mesa is the OpenGL vendor and Direct rendering is disabled. To get it running, I must sudo dpkg-reconfigure xserver-xorg and reboot. Also, every time I try to run an XGL/Compiz session, it resets. Other things that trigger it is running games with Cedega and simply leaving my computer idle. I left it on, and a few hours video playback became choppy and it reset itself to Mesa.

Here's my fglrxinfo output post-changing to Mesa:

```
jordan@jordan-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

After running the xorg configuration command and rebooting, it goes back to ATI for a while. Rebooting, idling for too long, running 3d games in Cedega, etc change it back to Mesa without rebooting.

---

### Post by Sievo on 2006-10-26
I have the EXACT same problem!  furthermore, my xorg.conf still has "fglrx" as the driver for my ATI Radeon 9600.

---

### Post by frenkel on 2006-10-27
[http://ubuntuforums.org/showthread.php?t=285614](http://ubuntuforums.org/showthread.php?t=285614)

---

