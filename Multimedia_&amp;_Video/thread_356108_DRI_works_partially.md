---
title: "DRI works partially"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by jaywhy13 on 2007-02-08
Here's what I had to do to get DRI working...

Perform modprobe -r fglrx

I copied /lib/modules/fglrx/build_mod/fglrx.ko to both places reported in modues.dep
jay@orberec:~$ cat /lib/modules/2.6.17-10-386/modules.dep | grep fglrx
/lib/modules/2.6.17-10-386/volatile/fglrx.ko: /lib/modules/2.6.17-10-386/kernel/drivers/char/agp/agpgart.ko
/lib/modules/2.6.17-10-386/misc/fglrx.ko: /lib/modules/2.6.17-10-386/kernel/drivers/char/agp/agpgart.ko

Then I put fglrx.ko in volatile and misc, THENNNN I modprobe fglrx so it loads back fglrx...
 (I  have fglrx blacklisted in /etc/default/linux-restricted-common) It works like that

Except.. when I reboot, the file fglrx.ko disappears from volatile. And when it does disappear I get errors that are either saying that the old driver is being loaded or apparently none is being loaded at all... ATI x1400 that is


PLEASE HELP me 2 regularize this... not too sure what's happening. 

I used the BinaryHowTo ATI install Wiki and followed the "harder" instructions because the xorg-driver-fglrx driver is tooooo old for my card. That one would work perfectly on an older card but my card is too new, as Xorg log complains about the driver being incompatibile if I try using it

---

### Post by kubla on 2007-03-09
I have the same problem.

If I link fglrx.ko from misc to volatile:

ln /lib/modules/2.6.17-11-386/misc/fglrx.ko /lib/modules/2.6.17-11-386/volatile/fglrx.ko -s

then restart gdm, all is fine:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700
OpenGL version string: 2.0.6334 (8.34.8)

otherwise, I'm stuck with MESA.

Has anyone got a permanent solution for this?

Like the original poster, after reboot I've lost the symlink to misc from volatile.

---

