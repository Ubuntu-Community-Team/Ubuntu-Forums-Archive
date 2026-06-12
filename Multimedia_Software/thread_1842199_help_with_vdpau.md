---
title: "help with vdpau"
date: 2011-09-10
forum: Multimedia Software
---

### Post by bananagins on 2011-09-10
hello all, i really need help getting vdpau to work. i'm running 10.10 maverick. i have an ATI Radeon HD 4600 Series card. these packages are installed:

libvdpau-dev
libvdpau1
vdpau-va-driver
fglrx
xserver-xorg-video-ati
xserver-xorg-video-radeon
xserver-xorg-video-mach64
xserver-xorg-video-r128

mplayer -vo vdpau -vc ffh264vdpau movie.mkv
gives this error:

...
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
...

do i need xvba instead of vdpau? (or do i need both?) do i need something from:
[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)
?   ... the OSes and models looked outdated

or do i maybe use this PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
?   ... if so, which packages should i get?

yes, i really am this clueless.

---

### Post by papibe on 2011-09-10
I'm afraid VDPAU is only for Nvidia cards.

For video hardware acceleration using ATI/AMD cards there is VAAPI. Try to research about that (I only know Nvidia know hows).

Regards.

---

### Post by bananagins on 2011-09-10
> **papibe said:**
> I'm afraid VDPAU is only for Nvidia cards.

For video hardware acceleration using ATI/AMD cards there is VAAPI. Try to research about that (I only know Nvidia know hows).

Regards.

hmm.. i thought i read in a couple places that vdpau works with ati... namely here:
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)
... of course here, he says to get xvba... i'm still not sure what exactly xvba is. whether its a way to get ati working with vdpau or something completely different... i guess the part where he mentioned it in the thread made it seem like vdpau would work with ati...

also during google searches, i noticed something about gallium drivers or something like that which also made ATI/AMD + VDPAU possible... don't know. can't find it now but will post the link when i find it.

thanks for the reply.

---

### Post by papibe on 2011-09-10
I've seen very good howtos on how to setup VAAPI on the XBMC forums. Just search VAAPI and you'll find lots of information.

For example [this]("http://forum.xbmc.org/showthread.php?t=99154&highlight=vaapi") one.

Good Luck!
Regards.

---

