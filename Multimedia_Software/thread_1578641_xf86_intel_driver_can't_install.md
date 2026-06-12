---
title: "xf86 intel driver can't install"
date: 2010-09-20
forum: Multimedia Software
---

### Post by jeti93 on 2010-09-20
Helo
I'm kind of new to Ubuntu, and I've installed 10.04 netbook on an old Fujitsu Amilo L1300 laptop, with an Intel i845 graphic card. As I know, it would run just OK with the 2.11.0 drivers, but i have no idea how to install that. I've downloaded the driver, and every package written on the page: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)
At first I couldn't even ./configure the install, but now the configuration runs smoothly. However I cannot finish the make part, because it gives an error.
> 
sentor@laptop:~/Documents/xf86-video-intel-2.11.0$ make
make  all-recursive
make[1]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0'
Making all in uxa
make[2]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/uxa'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/uxa'
Making all in src
make[2]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src'
Making all in xvmc
make[3]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc'
Making all in shader
make[4]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader'
Making all in mc
make[5]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make  all-am
make[6]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[5]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
Making all in vld
make[5]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make  all-am
make[6]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[5]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[5]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader'
make[4]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc/shader'
make[4]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc'
make[3]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/xvmc'
Making all in render_program
make[3]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/render_program'
make  all-am
make[4]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/render_program'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/render_program'
make[3]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src/render_program'
make[3]: Entering directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src'
  CC     i810_accel.lo
In file included from i810.h:60,
                 from i810_accel.c:41:
/usr/include/GL/glxint.h:36:19: error: GL/gl.h: No such file or directory
In file included from i810.h:60,
                 from i810_accel.c:41:
/usr/include/GL/glxint.h:103: error: expected specifier-qualifier-list before ‘GLboolean’
make[3]: *** [i810_accel.lo] Error 1
make[3]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sentor/Documents/xf86-video-intel-2.11.0'
make: *** [all] Error 2
Could somebody tell me what to do? I've been working on it for four days now, and as much as I'd love to continue it, I've run out of time. 

Or if there's a way to use the 2.12.0 driver, then could somebody tell me how?

Thanks in advance, and sorry if my English is bad.

---

### Post by jeti93 on 2010-09-22
Please, at least tell me some ideas, what should i try to do.

---

### Post by kerry_s on 2010-09-22
stop following guides not made for ubuntu.

intel drivers are already used by default. there's no need to install them.

what version does it say you have in synaptic?

i'm on ubuntu 10.10 which is more up to date.

---

### Post by jeti93 on 2010-09-22
2.9.1, but i had to edit GRUB with i915.modeset=1, to get it working, and it can't even display videos now, because every time i try to start one, the screen goes black (i installed it via synaptic)

---

### Post by jeti93 on 2010-10-01
Turns out all i had to do, was to install the intel driver from the i915.modeset workaround

---

