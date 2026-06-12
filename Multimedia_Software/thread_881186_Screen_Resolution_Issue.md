---
title: "Screen Resolution Issue"
date: 2008-08-05
forum: Multimedia Software
---

### Post by KLRWLF on 2008-08-05
Dell XPS M1210 laptop
NVIDIA GeForce Go 7400
Dell 21in 2001 FP Monitor
Ubuntu Hardy Heron

I have been having screen and video card issues for the past day or so. I was working on my laptop when I decided to connect to my Dell 2001 Flat Panel monitor. It would not work at first but somehow it managed to work itself out after fiddling with everything.

I had messed with the xorg.conf more than enough times to realize that no matter what I add to it, nothing changes. I had manually changed it as well as during the start up when I can choose the card and monitor  within the low-resolution safe startup. No changes.

NVIDIA Xserver Settings seem to be disabled.
```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

Administration -> hardware drivers, is installed, enabled and in use for NVIDIA accelerated graphics driver (latest cards).

Monitor Resolution only shows 800x600, 640x480 and does not detect display.

xgl is not installed. I installed it and removed it to see if that worked, restarted x and rebooted. No change.
```
ubuntu1@ubuntu1-laptop:/etc/X11$ apt-cache policy xserver-xgl
xserver-xgl:
  Installed: (none)
  Candidate: 1:1.1.99.1~git20080115-0ubuntu1
  Version table:
     1:1.1.99.1~git20080115-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/universe Packages
ubuntu1@ubuntu1-laptop:/etc/X11$
``` 


Packages currently installed in Synaptic under NVIDIA:
jockey-common
jockey-gtk
linux-restricted-modules-2.6.24-19-generic
nvidia-glx-new
nvidia-kernel-common
nvidia-new-kernel-source-envy
nvidia-settings
smartdimmer
xserver-xorg-video-nv

I had also completed all of the methods within this solved thread with no results. 
[http://ubuntuforums.org/showthread.php?t=656093]("http://ubuntuforums.org/showthread.php?t=656093")

I am out of ideas. Any one else have any ideas or luck. Do you see something wrong with my packages installed? One that should not be there or one that is missing or maybe conflicting?

Thanks in advance.

---

### Post by tuxxy on 2008-08-05
If you are finished using the monitor now, have you tried reconfiguring the xorg back to normal?

```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by KLRWLF on 2008-08-05
I have reverted back to the original xorg.conf a couple of times but not with the command you use. I would like to keep both monitors in use but not at the same time. The laptop has a bit less than 12 inches or 30.48 centimeters viewable. So, it is good for the road with minor work but right now, I have many windows open multi-tasking, so I need the flat panel monitor.

However, I can try what you suggest later tonight when complete with my work.

Thanks

---

