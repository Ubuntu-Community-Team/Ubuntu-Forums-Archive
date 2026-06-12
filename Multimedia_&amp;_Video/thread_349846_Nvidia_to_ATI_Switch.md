---
title: "Nvidia to ATI Switch"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by EvilMarshmallow on 2007-01-30
Hey all,

I just finished setting up my GeForce3 Ti 200 and now I've acquired an ATI Radeon 9250.  I put the ATI card in the box, removed the GeForce, and of course X no longer works.

Can someone help me uninstall my GeForce3 and install the Radeon?  Obviously I need to do it all from a command line.

---

### Post by Stemp on 2007-01-30
> I need to do it all from a command line.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by EvilMarshmallow on 2007-01-30
Ok, that got me back to a generic driver, but I can't get the ATI driver to install.  I installed the fglrx packages in Synaptic but I can't seem to figure out how to get them to work.  I know the acceleration isn't working because I have a couple opengl apps that won't run.

Any suggestions?

---

### Post by Motoxrdude on 2007-01-30
The generic ati driver doesn't support 3-d acceleration. Try and install the fglrx drivers via the terminal.
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

I think you would be better off with your old card btw.

EDIT: O and remember to configure the card
```
sudo aticonfig --initial
```

---

### Post by CowzRule on 2007-01-30
> **Motoxrdude said:**
> The generic ati driver doesn't support 3-d acceleration. Try and install the fglrx drivers via the terminal.
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

I think you would be better off with your old card btw.

EDIT: O and remember to configure the card
```
sudo aticonfig --initial
```
Add to that```
sudo aticonfig --overlay-type=Xv
```then```
sudo gedit /etc/X11/xorg.conf
```Add the following the the bottom of the file> Section "Extensions"
        Option  "Composite" "Disable"
EndSectionSave and close the file.
Now reboot```
sudo shutdown -r now
```
When you're logged back in, check the driver with```
fglrxinfo
```Now check for Direct Rendering```
glxinfo | grep render
```

---

### Post by EvilMarshmallow on 2007-01-30
Motoxrdude,

Thanks for getting me started... why is it better to stick with the older, smaller GeForce3?

Incidentally, that got everything native working.  However, Call of Duty via WINE does the following:

[INDENT]Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
[/INDENT]

OpenGL apps such as SuperTux work fine, it's just running via wine that's broken right now.

---

### Post by EvilMarshmallow on 2007-01-30
The results of CowzRule's checks for glxinfo and fglxrinfo:

ben@ubuntu:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

ben@ubuntu:~$ glxinfo | grep render
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by Motoxrdude on 2007-01-30
I forgot to add ```
sudo aticonfig --overlay-type=Xv
```, so that may be the problem. Did you already run that command yet?

---

### Post by EvilMarshmallow on 2007-01-31
Yeah, I ran that as I did CowzRule's suggestions.

---

### Post by EvilMarshmallow on 2007-01-31
Could this be a conflict with the nvidia driver that's killing OpenGL?

I noticed I still have the Nvidia X Server Settings app in my Applications menu.

The configurations menu is empty (no settings to change) but the application is still there.  Should I attempt to remove the nvidia stuff now?  Is it even the problem?

OpenGL apps such as Briquolo (native) and Call of Duty (via WINE) don't run at all.  CoD tells me to update my video driver.

---

### Post by jodama on 2007-04-10
Have you found a solution by any chance?  I'm having a similar problem and it's driving me insane.

---

### Post by EvilMarshmallow on 2007-04-10
In the end I found that I had to remove everything with NVidia's name on it before the ATI card would work.  Then I got a better Nvidia card and did it backward because the ATI drivers sucked... a 128MB card would run at half the framerate of a 64 MB Nvidia card I was using.

---

### Post by GoFaster on 2007-04-11
Hi,

I just finished replacing a GeForce3 Ti 200 card with an ATI 9800 Pro in Suse 10.1.  Running glxgears it looks like the Ati card is twice as fast.

After going through many suggestions from various sources found in web searching I still got all the errors posted in other replies, I finally found where the problem exists.  It seems that the latest driver update I installed from Nvidia wiped out the libGLcore.so file and linked libglx.so to libglx.7184.so.  When I reinstalled libGLcore.so and libglx.so files into the /usr/X11R6/lib/modules/extensions directory and rebooted the system, glxinfo and fglrxinfo gave the glx results we are all looking for.  With Suse and YAST/Software Mgt, I reinstalled "xorg-x11-server-glx" to reload the files but I'm not sure how to reinstall the two files in Ubuntu.

Good luck, the results are worth the effort.

---

