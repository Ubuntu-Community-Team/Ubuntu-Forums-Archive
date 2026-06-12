---
title: "ATi driver's not working properly"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by Kobra on 2006-08-19
Ok, I'm on a fresh install of Dapper, and I tried playing a video game.  Doesn't work, because I haven't installed my ATi drivers.  So I install them, and then in games I have major framerate problems (like 1 FPS, on good times), so I traced the problem to that Ubuntu was still using Mesa.  Upon asking my friend for help, he tells me to try reinstalling them.  I do, and nothing happens.  So then I try installing with some HOWTO's off the forums, and they're no goes as well.  The ATi card that I'm using is a Radion 9600 SE, please help.  All help is appreciated

---

### Post by moma on 2006-08-19
This is how I installed "fglrx" driver for ATI Radeon 9800 card in Ubuntu.

$ [COLOR="Green"]sudo apt-get -y remove xorg-common[/COLOR]

$ [COLOR="Green"]sudo apt-get install --reinstall linux-restricted-modules-$(uname -r)[/COLOR]

$ [COLOR="Green"]sudo apt-get install --reinstall xserver-xorg-driver-ati xorg-driver-fglrx[/COLOR]

$ [COLOR="Green"]sudo apt-get install --reinstall libgl1-mesa libgl1-mesa-dri[/COLOR]
-----

$ [COLOR="Green"]sudo depmod -a[/COLOR]
$ [COLOR="Green"]sudo ldconfig -vv[/COLOR]

$ [COLOR="Green"]sudo modprobe -r fglrx[/COLOR]
$ [COLOR="Green"]sudo modprobe -vv fglrx[/COLOR]

# Add "fglrx" driver into /etc/modules
$ [COLOR="Green"]sudo egrep "^fglrx" /etc/modules || echo fglrx | sudo tee -a /etc/modules[/COLOR]

# Configure xorg.conf
$ [COLOR="Green"]sudo aticonfig --initial[/COLOR]

# Configurer xorg.conf manually 
$ [COLOR="Green"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
* Select "fglrx" as video hardware.
* Say "NO" to question about "Use kernel framebuffer device interface".


This is a model of /etc/X11/xorg.conf. Take a backup-copy of yours first.
[http://www.futuredesktop.org/tmp/xorg.conf.ATI](http://www.futuredesktop.org/tmp/xorg.conf.ATI)
Check espesialmente **Section "Module"** and **Section "Device"** ! 
----

Reboot your Ubuntu.

Test ATI's "fglrx" driver

$ [COLOR="Green"]glxgears -info[/COLOR]
GL_RENDERER = RADEON 9800 Pro Generic   <----
GL_VERSION = 2.0.5814 ( 8.25.18 )    <----
GL_VENDOR = ATI Technologies Inc.    <----
.....

If it reports "Mesa" in GL_RENDERER or GL_VENDOR fields then it still uses Mesa software library, not the graphic hardware.

FPS numbers  should be over 1000 (most likely over 3 - 4000) when the gear wheel window is visible.
21046 frames in 5.0 seconds = 4209.193 FPS
32940 frames in 5.0 seconds = 6579.226 FPS
39940 frames in 5.0 seconds = 7987.821 FPS
-------

Other test methods
[COLOR="Green"]$ fglrxinfo[/COLOR]
Or if you run eg. Xgl/Compiz on display :1
[COLOR="Green"]$ fglrxinfo -display :1[/COLOR]

display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))
----

$ [COLOR="Green"]glxheads[/COLOR]
or 
$ [COLOR="Green"]glxheads :1[/COLOR]

---

### Post by Kobra on 2006-08-20
Ok, I looked around, and turns out that fglrx was blacklisted for some reason, so after taking it off the blacklist, I now get this error after installing ATi drivers and running:
```

aticonfig --initial

```

```

spaceace@Cliff-Desktop:~/Downloads$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

```

---

### Post by moma on 2006-08-21
Try to run it with sudo.
$ [COLOR="Green"]sudo aticonfig --initial[/COLOR]

If it fails again, then it's probably an internal error in "aticonfig".  Do not worry abbot it.
aticonfig --initial does not do much. It just writes "fglrx" and some other basic values to /etc/X11/xorg.conf.

Move on and run 
$ [COLOR="Green"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by barney_1 on 2006-08-21
@moma

I followed your guide in this thread and everything seemed to install correctly.  Unfortunately, as with my other attempts, I get a hard freeze at a blank screen just before the login screen comes up.

I'm running an ATI 9800 All-In-Wonder card.  Any thoughts on a way to correct this?

Thanks!

---

### Post by moma on 2006-08-21
@barney_1:
Prepare for the final trial:

1) Download the latest ATI driver from
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=3380](https://support.ati.com/ics/support/KBAnswer.asp?questionID=3380)

Read the install instructions
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html)

You must stop X before installing the driver.

2) Stop graphical GUI. Do this
Press CNTR + ALT + F1  (any of F1...F6 will do)
and login to the text console.

Stop X:
$ sudo /etc/init.d/gdm stop 
or 
$ sudo /etc/init.d/kdm stop  # if you run KDE

3) Install the driver.

4) Restart X
$ sudo /etc/init.d/gdm restart

---

### Post by barney_1 on 2006-08-22
Thanks for the help but the same hard freeze at a blank screen resulted.

---

### Post by moma on 2006-08-22
> **barney_1 said:**
> Thanks for the help but the same hard freeze at a blank screen resulted.

Sorry pal, that's a hard case.

What about the Ubuntu CD.
Do you get a graphical screen when you boot up with it?

Have you considered to re-install?

---

### Post by Kobra on 2006-08-22
Even after installing ATi drivers, running aticonfig --initial under sudo, and reconfiguring xserver-xorg, I'm still getting MESA under fglrxinfo

---

### Post by Kobra on 2006-08-24
Sorry for the double post, but not I have something called "atieventsd" taking up all of my CPU, and a new line is in my xorg.conf called:
```
Option		"UseFBDev"		"true"
```

Please, this is starting to drive me insane, to the point of buying a nVidia card...

---

