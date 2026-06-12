---
title: "How to UNinstall ATI binary drivers?"
date: 2006-10-08
forum: Multimedia &amp; Video
---

### Post by Mastus on 2006-10-08
I had a Radeon 9550, with drivers installed as [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

section "Using the drivers from ati.com" describes...

Unfortunately I blew up the tv-out from the card (Do NOT hotplug scart wires...), so I bought an Club 3d FX5200 card.

Now if I try to install the nvidia drivers, I get this error message:

```
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8762+2.6.15.11-5_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So how do I uninstall the ati driver? Apt-get won't help because I didn't install the ati drivers from there.

---

### Post by pay on 2006-10-08
I think the syntax is ```
sudo apt-get remove --purge fglrx-*
```
You can remove them this way because you made .deb files and then installed them. The code I told you might be wrong though (I'm not currently on Ubuntu to verify). But when you do that things will probably go wrong. change /etc/X11/xorg.conf so that it uses a driver that nvidia can handle (I can't help you here since i don't have an Nvidia card).

---

### Post by Mastus on 2006-10-08
Won't work...

Apt-get says that no fglrx-packages are installed.

Would it be safe just to delete the symlink from /usr/lib/fglrx ??

---

### Post by pay on 2006-10-09
I think so if you change the xorg.conf script to another driver. but I might be wrong.

---

### Post by IoCaster on 2006-10-09
Check this post [http://ubuntuforums.org/showthread.php?t=273934]("http://ubuntuforums.org/showthread.php?t=273934") and see if that helps you remove the residual ATI related stuff.

---

