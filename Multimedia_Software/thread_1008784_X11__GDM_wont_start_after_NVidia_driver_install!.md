---
title: "X11 / GDM wont start after NVidia driver install!"
date: 2008-12-11
forum: Multimedia Software
---

### Post by ikehack on 2008-12-11
I wanted to install drivers from nvidia so I could play with WoW in Wine. X needed to be killed so I did: Ctrl+Alt+F1, logged in, sudo killall gdm then proceeded to install the driver. I told the installation to make a new xorg.conf file (generates one) then X kind of started again? The screen was all distorted, so I restarted. Now when the Ubuntu loading screen goes away, I'm stuck at a black screen and nothing happens until hit Ctrl+Alt+F1. I restored the xorg.conf file back to the original, did sudo /etc/init.d/gdm start, startx and it still bring me to that black screen where nothing happens until I Ctrl+Alt+F1. Am I beat? What can I do? Please help! :(

EDIT:

After I do startx, I let it sit for a bit then Ctrl+Alt+F1 back out to this backtrace:

```

waiting for X server to begin accepting connections
giving up.
xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

EDIT 2:

Sorry again, but above that backtrace are, uhhh, a crap load of errors...

```

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 11 22:06:18 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
Error: API mismatch: the NVIDIA kernel module has version 169.12, but this NVIDIA driver component has version 177.82. Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Faile to initialize the NVIDIA kernel module! Please ensure there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a useable configuration.

```

then followed by the backtrace above this.

---

### Post by ikehack on 2008-12-11
Forget everything I said. Compiz, Avant, none of that stuff works anymore. I tried tutorials on how to uninstall all nvidia stuff and install new stuff, when I tried that, I don't get my 1680x1050 resolution even when adding it to the xorg.conf file. Can someone please help! I need this for school tomorrow!

EDIT:

For the most part everythings fixed. I went through Synaptic and just installed all nvidia stuff (don't ask I dont remember) and my resolutions back, but in that process my sound doesn't work anymore? I don't care, I'll fix that. But desktop effects, I don't have them and can't enable them. What now? D:

---

