---
title: "Verification of LIRC and USB-UIRT on Hardy"
date: 2008-09-18
forum: Multimedia Software
---

### Post by HalNineThousand on 2008-09-18
I'm currently trying to test LIRC with a USB-UIRT on two different computers, one is running Gutsy and one is running Debian Sarge (which will be upgraded to Etch eventually).

On Gutsy, I ran into an error with the LIRC driver when I wanted to transmit that is discussed here ([http://www.nabble.com/USB-UIRT:-uirt2_raw:-checksum-error-td12988910s15552.html](http://www.nabble.com/USB-UIRT:-uirt2_raw:-checksum-error-td12988910s15552.html)) among other places.

I don't like altering things that can be wiped out with a new update from apt or doing things I'll have to redo with each new update (I had to go through that with each kernel update with nVidia drivers for too long!).  I'd much rather stick with a stock kernel and stock modules so I don't have to worry about updates.

I've seen posts by people using the USB-UIRT on Hardy and using it as part of MythTV and just with LIRC and no special project.

Can anyone confirm that the bug ftdi_sio.c  and ftdi_sio.h that has caused problems with some Debian kernels and the kernels in Gutsy has been fixed so there is no problem like his in Hardy?  If so, it's worth me updating my workstation now instead of waiting.  I had planned to skip Hardy due to timing issues with my schedule, but it'd be worth taking the extra time if it fixes this bug so I don't have to do all that tedious mucking about in non-standard packages to get LIRC to work with the USB-UIRT.

Actually, I guess I should also put it this way: Is anyone using the USB-UIRT with LIRC on Hardy without any evidence of driver issues?

Thanks!

---

### Post by HalNineThousand on 2008-09-18
I've seen posts in other threads from a while back, so someone's got to be using LIRC and the USB-UIRT on Hardy, so I know there are people who can answer this.

To get the USB-UIRT to work was there any need to do anything like changing kernel modules, or did it work without that kind of stuff?

Thanks for any insight on this!

---

### Post by paulg on 2008-09-19
I've seen a few posts around on this as well but sorry, I don't know the answer. Try asking your question on the [LIRC mailing list]("http://lists.sourceforge.net/lists/listinfo/lirc-list").

Rather than upgrade Sarge->Etch you might wait a couple months and go Sarge->[Lenny]("http://lists.debian.org/debian-devel-announce/2008/07/msg00007.html") when it hits the stable branch. Of course, a couple months easily becomes a couple years on the Debian release cycle ;) 

Good luck!

---

