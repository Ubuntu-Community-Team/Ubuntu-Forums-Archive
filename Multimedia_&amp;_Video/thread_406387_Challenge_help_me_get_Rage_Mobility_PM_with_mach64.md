---
title: "Challenge: help me get Rage Mobility P/M with mach64 chip set DRI Working"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by narnie on 2007-04-10
I've been working several nights to get my video card DRI working so that I can ultimately install Beryl.

I was a dos diehard, and am familiar with cmd line in that. Compiling, as long as I have detail instruction, is fine with me, but I need that step-by-step.

My card reads:
00:14.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M (rev 64)

Seems this should use the mach64 driver

I've read this forum link:

[http://ubuntuforums.org/showthread.p...bility+p%2F](http://ubuntuforums.org/showthread.p...bility+p%2F) m

Down toward the bottom, it says:

"btw, depending on your kernel version, the names in step 1 & 2 may vary"

I don't know how to change to what my kernal needs

I'm using ubuntu edgy 2.6.17-11-generic or 2.6.17-10-generic. Sorry, I don't now which.

When I try to follow the steps on the above link, I get this error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-2.6-686

When I look at Synaptic, I see several headers already marked as installed.

The next step is the wget step, but I don't now what snapshots I need for my kernal version. Perhaps I just need to use the most current.

Thanks in advance for any help.

Addendum:

I went on ahead and made sure I had all the apt-get stuff (just needed the linux-686 added).

I then compiled common without problems

Then I got an error with compiling mach64 that said something like "DRI drivers cannot be installed without the latest kernel modules" and told me to check out the error file as below:

make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
CC [M] /tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.o
/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c: In function ‘drm_ati_free_pcigart_table’:
/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c:87: error: ‘struct page’ has no member named ‘count’
make[3]: *** [/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.o] Error 1
make[2]: *** [_module_/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2

How do I get the "latest kernel modules?" Is the error log any help in helping me?

Thanks again

---

