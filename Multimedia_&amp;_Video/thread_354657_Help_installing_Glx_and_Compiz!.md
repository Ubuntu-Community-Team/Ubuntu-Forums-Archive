---
title: "Help installing Glx and Compiz!"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by estebancs on 2007-02-06
I intalled the nvidia's driver usind thw wiki how to... My card is a Nvidia Geforce2 MX/MX 400 so I installed the nvidia-glx-legacy drivers, I already edited the xorg.conf file as the guide tells me to, I think it is installed because after installing and rebooting 2 new boot options appeared (kernel generic and kernel generic recovery mode) and when I start, before the login screen a nvidia screen comes up, nvidia settings has more options than before but I don't know if glx is running.

when I try to check with

```
sudo glxinfo | grep rendering
```

the terminal gives me this output:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
...
Xlib:  extension "GLX" missing on display ":0.0".
```

and when I try to enable glx with

```
sudo nvidia-glx-config enable
```

the terminal gives me this error:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
```

although I've already changed from "nv" to "nvidia" in the xorg.conf

any idea on what should I do?

also when I try to install compiz it gives me this error:

Error: Conflicts with the installed package 'libmetacity0'

---

### Post by Sqwishy on 2007-02-06
Looks like you have a problem! First of, IMO you shouldn't be using compiz, probobly beryl instead. But if you want compiz sure?
Looky in xorg.conf and under your Module Section look for Load "glx" it's probobly commented out and make sure it's not.

---

### Post by estebancs on 2007-02-07
> **Sqwishy said:**
> Looks like you have a problem! First of, IMO you shouldn't be using compiz, probobly beryl instead. But if you want compiz sure?
Looky in xorg.conf and under your Module Section look for Load "glx" it's probobly commented out and make sure it's not.

Ok glx fixed, I just added ```
Option "AllowGLXWithComposite" "1"
```
to the "device" section of xorg.conf.

So now hardware acceleration is working, it runs smoothly the matrix screensavers that before were way too slow and I can play tux racer, but I'm still unable to install compiz...

I'm installing compiz instead of beryl cuz it seems a lot easier to install than beryl (considering I'm new to linux and i don't have a broadband connection to install stuff from repositories so I'm downloading .deb packages and even compiling from source) I would install any of them, as long as they offer cool visual effects... does anyone knows where I can find an OFFLINE HOW TO Install beryl or compiz?

---

### Post by tgmaster on 2007-02-07
> **estebancs said:**
> ... does anyone knows where I can find an OFFLINE HOW TO Install beryl or compiz?

It is very hard to find OFFLINE howtos you need. The only way is to find and to buy some Linux-papers...

---

### Post by estebancs on 2007-02-08
Yeah I know it's hard to find OFFLINE HOWTOS, anyway I'm going to try to install from .deb packages, I've already downloaded all packages(and their dependencies), one ob them is compiz-gtk, when I try to install it, the installer gives me this error:

[COLOR="Red"]Error: Conflicts with the installed package 'libmetacity0'[/COLOR]

What I'm supossed to do? Should I uninstall libmetacity0 and then try to instal compiz-gtk?

---

### Post by estebancs on 2007-02-11
Ok I got tired and I installed beryl instead, It's working great, cheack out

[http://www.ubuntuforums.org/showthread.php?p=2139369#post2139369](http://www.ubuntuforums.org/showthread.php?p=2139369#post2139369)

---

