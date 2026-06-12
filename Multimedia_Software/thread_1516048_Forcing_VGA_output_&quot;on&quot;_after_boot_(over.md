---
title: "Forcing VGA output &quot;on&quot; after boot (overhead projector)"
date: 2010-06-23
forum: Multimedia Software
---

### Post by r_mano on 2010-06-23
I am posting this in the hope that it can save some hour to other ubunteros, and to pose a question. 

Yesterday I was trying to connect the overhead projector to the VGA output of my laptop. The problem was that the device was connected by way of a VGA video splitter, which evidently missed some signal, and made the projector invisible to the laptop: "xrandr -v -q" told me "VGA1 disconnected". 

The solution is: boot with 
```
video=VGA-1:e
```
kernel boot parameter, found [in the wiki]("https://wiki.ubuntu.com/X/KernelModeSetting/") and in [intel linux FAQ]("http://intellinuxgraphics.org/documentation.html").

It works, but it is a bit awkward to have to *reboot* to switch on or off the VGA output. So I suppose there is some user-space trick or utility to do this which I was unable to find. Could please anyone point me to it? 

Thanks a lot!

---

### Post by efflandt on 2010-06-24
X usually looks for video hardware when it starts.  So have you tried just logging out of X and back in.

When I switched to a totally different DVI display while in suspend (from 19" 1280x1024 monitor to 27" 1280x720 HDTV), my computer woke at the same resolution it was in when it went into suspend (1280x1024, but vertically compressed so things were fat).  But when I logged out of X and logged back in, it recognized the 1280x720 native resolution and proper aspect ratio of the HDTV.

---

### Post by r_mano on 2010-06-24
Yes, I tried restarting X and even rebooting with the projector connected and switched on, to no avail. 

The problem is that the laptop *cannot* say the monitor is connected. The splitter box blocks the signals that the driver uses to detect something is connected. Now, under windows XP I can force the output on using the appropriate key combo, and the output go on even if it *seems* no CRT is connected. Linux simply ignores me, unless I boot with the aforementioned magic in the boot line.

I still think that having to reboot (or even restart X) to simply switch an output on is unfortunate.

---

