---
title: "Tried fglrx, now I cant get to an accelerated desktop"
date: 2010-07-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by orlox on 2010-07-13
Hi! I have an updated 64 bit maverick, and today I tried to see what happened if I tried to install the fglrx drivers. This ended with DKMS failing to build the module:

```

DKMS make.log for fglrx-8.723.1 for kernel 2.6.35-7-generic (x86_64)
mar jul 13 22:03:57 CLT 2010
AMD kernel module generator version 2.1
cat: /lib/modules/2.6.35-7-generic/build/include/linux/utsrelease.h: No existe el archivo o directorio
Error:
kernel includes at /lib/modules/2.6.35-7-generic/build/include do not match current kernel.
they are versioned as ""
instead of "2.6.35-7-generic".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux

```
I'm not sure if fglrx is supossed to work in maverick anyways, so I just thought i'd keep using the open source drivers. The problem is that I can only access a workable desktop by entering recovery mode->failsafeX.

So, now I have an unnaccelerated an unpractical situation, and I was wondering how to revert to the old situation, or actually getting catalyst to work.

By the way, my video card is a 512MB ATI Mobility Radeon HD4330.

Cheers!

---

### Post by jfernyhough on 2010-07-14
Search...

[http://ubuntuforums.org/showthread.php?t=1510376](http://ubuntuforums.org/showthread.php?t=1510376)

Essentially, use the x-swat PPA for the moment.

---

### Post by orlox on 2010-07-14
Just installed through the x-swat ppa and it managed to go through the installation. However, I cannot activate compiz...fglrx appears as activated in hardware controllers. Should it just work with the x-swat ppa?

---

### Post by jfernyhough on 2010-07-14
You might need to run $ sudo aticonfig --initial

---

### Post by orlox on 2010-07-14
thanks jfernyhough, that did it. I'm kind a newb when it comes to catalyst, have been an intel an nvidia man for quite a while...

---

### Post by cariboo on 2010-07-14
I marked this thread **solved** for you

---

### Post by orlox on 2010-07-18
Marking it as unsolved, cause I'm still unable to go back to the open source ati drivers (sorry for leaving it open before cariboo907)...
Just disabling catalyst (through the hardware controllers app) doesn't do it, X doesn't load correctly, and I'm currently loading it through failsafeX. Checked my Xorg.1.log.old file (that, if I remember well, should correspond to the previous unsuccesfull boot I tried), and it's flooded with this messages:
> 
[ 14521.690] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument


---

### Post by Universal344 on 2010-07-18
not entirely sure if this would work, but you could try uninstalling the open source driver (called radeon or radeonhd I believe) and reinstalling.  If that fails, you could try reconfiguring X, but I believe that can cause other issues so backup your previous configuration first.

---

### Post by jfernyhough on 2010-07-18
Did you recreate (or just plain delete) the /etc/X11/xorg.conf ? If not it will still be trying to load fglrx. Either:

$ sudo rm /etc/X11/xorg.conf

or

$ sudo dpkg -phigh xserver-xorg

> have been an intel an nvidia man for quite a while...Same here. It was quite a learning curve... plus I miss having mipmap-based window blur in Compiz...

---

### Post by orlox on 2010-07-18
I already tried deleting xorg.conf, and I also did sudo dpkg-reconfigure -phigh xserver-xorg. Still, can't get ati working again...

Actually thinking about doing a fresh reinstall.

---

### Post by jfernyhough on 2010-07-18
Apparently "Those error messages only happen when you're using fbdev with KMS, and they are harmless." from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-fbdev/+bug/573668](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-fbdev/+bug/573668)

It sounds as though it's using fbdev and not radeondrmfb which is IIRC what mine was using before I installed fglrx (as much as I love high resolution console I find Compiz a little more appealing).

Have a look in your xorg.conf and see if there is Driver "fbdev" entry. If there is, change it back to Driver "radeondrmfb" and see if that makes a difference.

---

### Post by orlox on 2010-07-18
I did not have a xorg.conf, but I checked that the xorg.conf.failsafe file had fbdev. I created this xorg.conf file:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeondrmfb"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
Yet, I still have no success...

---

### Post by clhsharky on 2010-07-18
orlox

Remove xorg.conf file and use this 
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Always works for me.

Sharky

---

### Post by orlox on 2010-07-19
The fglrx purging methods described in the wiki didn't help my cause clhsharky. I think I will go the "easy" way, and just take this as an opportunity to try arch...

Thanks for all the advice!

---

### Post by grege on 2010-07-30
You have to uninstall fglrx. When it installs it creates all sorts of symlinks to it's bits and pieces. Those symlinks are still active and point the ati driver to the wrong places. Depending on what you have done you may have to reinstall fglrx, then ubinstall it.

Just use Synaptic and uninstall fglrx and remove or rename /etc/X11/xorg.conf then restart and let the system reconfigure itself.

---

