---
title: "&quot;Could not connect to video device (/dev/video0)&quot;"
date: 2009-10-24
forum: Multimedia Software
---

### Post by arvevans on 2009-10-24
If one does a search for "could not connect to video device" (in quotes to group all words together for the search), you will find that there are several unanswered and unresolved problem postings relating to inability to open /dev/video0.

I too have this problem when trying to use camorama.  Cheese works, but with poor resolution (I have a 12 MB camera that on Ubuntu only does 320 X 160 resolution).
[INDENT]arv@arv-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse
Bus 003 Device 003: ID 0ac8:3330 Z-Star Microelectronics Corp. 
Bus 003 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
arv@arv-desktop:~$ [/INDENT]

The Z-star device is my camera, a "Sirius USB2.0 Camera (/dev/video0)" unit.

Permissions for the video devices in ls -la /dev/v* look like this:

[INDENT]arv@arv-desktop:~$ ls -la /dev/v*
crw-rw----  1 root tty    7,   0 2009-10-24 10:03 /dev/vcs
crw-rw----  1 root tty    7,   1 2009-10-24 10:04 /dev/vcs1
crw-rw----  1 root tty    7,   2 2009-10-24 10:04 /dev/vcs2
crw-rw----  1 root tty    7,   3 2009-10-24 10:04 /dev/vcs3
crw-rw----  1 root tty    7,   4 2009-10-24 10:04 /dev/vcs4
crw-rw----  1 root tty    7,   5 2009-10-24 10:04 /dev/vcs5
crw-rw----  1 root tty    7,   6 2009-10-24 10:04 /dev/vcs6
crw-rw----  1 root tty    7,   7 2009-10-24 10:04 /dev/vcs7
crw-rw----  1 root tty    7,   8 2009-10-24 10:03 /dev/vcs8
crw-rw----  1 root tty    7, 128 2009-10-24 10:03 /dev/vcsa
crw-rw----  1 root tty    7, 129 2009-10-24 10:04 /dev/vcsa1
crw-rw----  1 root tty    7, 130 2009-10-24 10:04 /dev/vcsa2
crw-rw----  1 root tty    7, 131 2009-10-24 10:04 /dev/vcsa3
crw-rw----  1 root tty    7, 132 2009-10-24 10:04 /dev/vcsa4
crw-rw----  1 root tty    7, 133 2009-10-24 10:04 /dev/vcsa5
crw-rw----  1 root tty    7, 134 2009-10-24 10:04 /dev/vcsa6
crw-rw----  1 root tty    7, 135 2009-10-24 10:04 /dev/vcsa7
crw-rw----  1 root tty    7, 136 2009-10-24 10:03 /dev/vcsa8
crw-rw----+ 1 root video 81,   0 2009-10-24 10:03 /dev/video0

/dev/v4l:
total 0
drwxr-xr-x  4 root root   80 2009-10-24 10:03 .
drwxr-xr-x 17 root root 4160 2009-10-24 11:52 ..
drwxr-xr-x  2 root root   60 2009-10-24 10:03 by-id
drwxr-xr-x  2 root root   60 2009-10-24 10:03 by-path
arv@arv-desktop:~$ 
[/INDENT]

And this is what I get when opening camorama using the "-D" debug option:
[INDENT]arv@arv-desktop:~$ camorama -D

VIDIOCGCAP
device name = Sirius USB2.0 Camera
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 320
max height = 240
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 160
height = 120
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 160
height = 120
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 32768
hue = 0
colour = 26214
contrast = 32768
whiteness = 19661
colour depth = 16
YUYV

[/INDENT]
Along with the pop-up saying "Could not connect to video device (/dev/video0)".

Any idea what is broken, missing, wrongly configured, or what the problem might be?

Seems that I am not the only one with this problem.

Arv
_._

**UPDATE:**
Found this command on another thread, not associated with my problem, and it fixed the "could not open /dev/video0" problem:

[INDENT] export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so [/INDENT]

Resolution still only 320 X 160 for 12 megapixel camera.  I'm still working on that as a separate, probably driver, problem.
_._

_._

---

### Post by davemar on 2009-10-25
I'm having similar problems with my Logitech S7500. It works fine in Skype, but I get the same error in Camorama and no image, or in Cheese. It appears I haven't got any libraries called libv4l* anywhere. I've done a package search in Synaptic for v4l, but nothing appears that seems to be any dev or library packages. Am I missing something?

---

### Post by arvevans on 2009-10-25
Davemar

If you do a Synaptic search for "video" you will find a bunch of video libraries.  I'm not sure how to determine which ones might fix your problem(s).

Arv
_._

---

### Post by davemar on 2009-10-26
I think my problem is that I'm still on 8.04, which hasn't got those libraries in the packages. I'll probably have to upgrade to 9.?? (depending on opinions to which is more stable) to get things working properly for webcam stuff.

---

### Post by no2498 on 2010-05-09
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

try the cam in cheese

---

