---
title: "(Nvidia Graphics Card) Bouncing Input Not Supported screen"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Huggy on 2006-06-08
I need help. I have tried every manner of installing NVidai graphics as shown in the forums, and none have worked. In fact most crashed my Xserver and I had to re-install because I don't quite know how to get out of those kind of situations yet.

I have a Geforce FX 5200 graphics card, and I have whatever the default kernel is for the latest ubuntu 6.06. Can anyone help me? This bouncing input not supported screen is getting really annoying, and I would love to be able to have 3d acceleration and OpenGL for my UT2004 and Blender.

Please help me... I'm still slightly new to ubuntu and debian systems. So I don't comprehend much yet... but I'm a pretty quick learner.

---

### Post by Huggy on 2006-06-08
How do you kill the Xserver? Like what's the command, because rcxdm restart doesn't work and neither does kill or stopx?

---

### Post by Huggy on 2006-06-09
Also I have a 64bit processer and a ASUS motherboard if that matters
I still can't figure this out. Someone, anyone, please help me...

---

### Post by tseliot on 2006-06-09
[QUOTE=Huggy]How do you kill the Xserver? Like what's the command, because rcxdm restart doesn't work and neither does kill or stopx?[/QUOTE]
```
sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDM)
```

---

### Post by tseliot on 2006-06-09
Are you currently able to boot in the Desktop Environment (the GUI)?

If not:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "vesa" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

then
```
sudo /etc/init.d/gdm restart
```

---

### Post by Huggy on 2006-06-10
Thanks, getting rid of that, makes it easier to work with, but now I just have to figure out how to install NVidia graphics. Everything else I've tried has failed miserably. Is there a trick to installing the 64bit, because I noticed a lot of people having problems.

---

### Post by Huggy on 2006-06-10
Ok It's back! Whenever I install Nvidia glx and get my openGL support, that bouncing screen comes back. Is there any way to get rid of it, and have openGL support and 3d Accell at the same time? PLEASE, I'm desperate here!

---

### Post by Huggy on 2006-06-10
If I set the driver back to vesa instead of NVida, first off will it crash my Xserver, and second will I still have openGL support and 3d accell?

---

### Post by Huggy on 2006-06-10
I did it, but it apperas that I can no longer run half my 3d accel or OpenGl games? I tried using glxgears to see what my output would be, but it wouldn't do it. Right now my driver is sitting at vesa instead of nvidia, and I have no openGL support. Is there any way around this, because I would really like to be able to install and play UT2004.

---

