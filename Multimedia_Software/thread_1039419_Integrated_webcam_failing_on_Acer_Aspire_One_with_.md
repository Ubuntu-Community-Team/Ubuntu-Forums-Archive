---
title: "Integrated webcam failing on Acer Aspire One with Ubuntu 8.10"
date: 2009-01-14
forum: Multimedia Software
---

### Post by aceman on 2009-01-14
My first post to the forum...

I installed Ubuntu 8.10 Desktop with UNR according to the [AspireOne guide]("https://help.ubuntu.com/community/AspireOne") below onto a [Acer Aspire One ZG5]("http://en.wikipedia.org/wiki/Acer_Aspire_One"):

Everything is working but the webcam.

On boot up, there was no "/dev/video" and `dmesg | grep uvc` returned:

```
$ ls -l /dev/vid*
ls: cannot access /dev/vid*: No such file or directory
$ 
```

```
$ dmesg | grep vid
[    0.000000] BIOS-provided physical RAM map:
[    2.647789] pci 0000:00:02.0: Boot video device
[   25.617668] Linux video capture interface: v2.00
[   25.643332] usbcore: registered new interface driver uvcvideo
$ 
```

I've tried [the instructions from here](http://ubuntuforums.org/showthread.php?t=929887), and have "uvcvideo" in the /etc/modules file:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath_pci
uvcvideo

```

And already had added and removed the line in /etc/modprobe.d/options without any success:
```
options uvcvideo quirks=2
```

I would get the following before:
```
$ dmesg | grep uvc
[   21.408477] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   22.409173] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -110 (exp. 26).
[   22.409188] uvcvideo: Failed to initialize the device (-5).
[   27.408424] usbcore: registered new interface driver uvcvideo
$ 
```

Now I get don't even get the uvcvideo: lines..

The uvcvideo is installed:
```
$ lsmod | grep uvc
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
usbcore               148848  4 uvcvideo,ehci_hcd,uhci_hcd
$ 
```

Cheese, luvcview, and Camerama all fail to detect the webcam.

What can I do to get the webcam working with Ubuntu 8.10?

I posted the above on an [acer user forum]("http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=9808"), but since this might be more of an Ubuntu issue, (i'm not sure), I'm posting here.

Any help to get the webcam working would be appreciated.

---

### Post by Xyphoid on 2009-04-27
I had exactly the same problem. But after a cold boot, my webcam was detected again....

---

