---
title: "broadcomm BCM4322 installing drivers from tarball"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by poltak on 2010-08-01
Hi guys, just a quick question.

I recently installed the Ubuntu 10.04 netbook remix on a friend's netbook (she pretty much killed XP) which has a Broadcom BCM4322 Wireless card according to lspci.

Anyway, the card doesn't want to work out of the box with Ubuntu so I did some googling and came up with the solution that I had to install the Broadcom proprietary drivers from a tarball ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)).

Anyway, I followed the readme on the broadcom site and was stumped after the "# make" command as it didn't want to work. Please note, I've never installed something using a tarball before, but I thought it would be simple enough to follow the readme on the website. Anyway when I run "# make" I get:
```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  LD      /home/sarah/Documents/wireless/built-in.o
/bin/sh: ar: not found
make[2]: *** [/home/sarah/Documents/wireless/built-in.o] Error 127
make[1]: *** [_module_/home/sarah/Documents/wireless] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2

```

I'm still a bit of a linux newbie so go easy :) Thanks for reading and hopefully helping.

Oh also, I tried just connecting it to internet via cat5 cable and downloading the proprietary drivers in "Hardware Drivers" menu. There were two drivers there for the wireless card (proprietary and non-proprietary versions) but they both came up with errors after downloading and installing and did not work :\

---

### Post by kerry_s on 2010-08-01
connect to the internet, go to system-> hardware drivers

oops sorry missed that last part, i see you tried that.

go into synaptic & install "bcmwl-kernel-source"

---

### Post by poltak on 2010-08-02
Sorry for the late reply... got home last night from Uni only to realise my ISP had cut my connection due to insufficient funds... >_> heh...

Anyway, I've moved the netbook to Uni and I tried to do what you instructed. I found the package in synaptic and went to download... but turns out there is a problem with the ethernet connection or something. I tried different cat5 cables, so I don't think it was a problem with an unreliable transfer medium.

Anyway, it kinda works, but also doesn't. What I mean is I pinged google and left it for a bit and I got an average packet loss of %70... :| so everytime I try to download the package it usually times out on half the packages and gets half the others... doesn't really work well...

Anyway, is there a way I can download these packages individually, say on my laptop, then put them on the netbook and install them that way?

Thanks for you help, again.

---

