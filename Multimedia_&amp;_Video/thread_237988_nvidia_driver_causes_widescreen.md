---
title: "nvidia driver causes widescreen"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by cyberb0b on 2006-08-17
So I just upgraded from breezy to dapper.  When I log in my screen appears to be in widescreen mode.  I have a GeForce4 MX 420 video card and Viewsonic VA912B 19 inch monitor running in 1024x768 mode.  

After playing around with packages I found that changing the xorg.conf file from the driver "nv" to "nvidia" causes the screen to go from fullscreen mode to widescreen mode.  Both modes are 1024x768 on the screen, but widescreen is scrunched and has black bars at the top and bottom.

So, how do I use the "nvidia" driver (so I can use 3d acceleration) and use fullscreen mode?  Is there something I should add to xorg.conf to tell the dapper nvidia driver to use fullscreen?

Attached is my xorg.conf file with "nv" instead of "nvidia".

---

### Post by tseliot on 2006-08-17
1) How did you install the driver?

2) To enable the driver, type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo nvidia-xconfig
```

and then if you have problems with the resolution:

Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by cyberb0b on 2006-08-19
1) Installed using synaptics package manager.  Also tried installing with Automatix.

2) Tried that.  Same results.

Basically, just changing "nv" to "nvidia" causes the widescreen effect.

I haven't tried modifying the xorg.conf file by hand yet.  Ugh.

---

