---
title: "Catalyst 9.5 Ruined X.org | Can't Fix!"
date: 2009-05-20
forum: Multimedia Software
---

### Post by Literati on 2009-05-20
Alright, so I upgraded my ATI Catalyst to the newest version, and went to do some "tweaking" in the Catalyst Control Center. As soon as I clicked it my screen went black and my computer hung. No TTY, no nothing.

So I tried to reboot normally, nada, no mouse, no anything.

So into the Live CD I go, I tried mounting my hdd and going to it's /usr/share/ati folder to run sh ./fglrx-uninstall.sh but I get the following

```
[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run fglrx-uninstall.sh (this is not recommended).
```

And I don't know how to set an "environment variable" (I tried ```
export FORCE_ATI_UNINSTALL=1
``` and then re-running the command, but nada)

So then I thought "Hey, I'll just steal the Xorg.conf file from my Live CD and pop it on my HDD and hope for the best.

Well, that didn't work either, with all generic drivers, or the vesa driver, I just get a bucnh of colours on my screen.

So I tried going into recovery mode and using xfix and continuing my boot, but even STILL I get nothing.

So I tried going into a root shell in recovery mode and running ```
sudo dpkg-reconfigure -phigh xorg-xserver
``` but it says that it can't find the package. :/

I'm very literally at my wits end about this, and could really use some help. So, thanks in advance for any tips :)

**EDIT:** I figured it out. Since I was using a live CD, it wanted to go to IT'S /etc/ati folder, not /media/disk/etc/ati, so with a quick switcheroo in the ./fglrx-uninstall.sh file, it uninstalled perfectly, and now I was able to (properly) install Catalyst 9.5 and everything is hunky-dory :)

---

