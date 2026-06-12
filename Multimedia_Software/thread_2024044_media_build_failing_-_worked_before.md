---
title: "media_build failing - worked before"
date: 2012-07-13
forum: Multimedia Software
---

### Post by Oby on 2012-07-13
**OS:** Ubuntu 12.04, all apt-get updates as of today (including backports).

**Trying to**: Install drivers for the Happauge WinTV-HVR-930C, using these instructions: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C)

at step 3, I execute these command:
```
sudo rm -r media_build
 git clone git://linuxtv.org/media_build.git
 cd media_build
 ./build
```
The last one (./build) fails. Here is the output (excerpt):
```
WARNING: This is the V4L/DVB backport tree, with experimental drivers
	 backported to run on legacy kernels from the development tree at:
		http://git.linuxtv.org/media-tree.git.
	 It is generally safe to use it for testing a new driver or
	 feature, but its usage on production environments is risky.
	 Don't use it in production. You've been warned.
Created default (all yes) .config file
./scripts/fix_kconfig.pl
make[1]: Leaving directory `/home/oby/Desktop/media_build/v4l'
make -C /home/oby/Desktop/media_build/v4l 
make[1]: Entering directory `/home/oby/Desktop/media_build/v4l'
scripts/make_makefile.pl
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/oby/Desktop/media_build/v4l'
make[1]: Entering directory `/home/oby/Desktop/media_build/v4l'
perl scripts/make_config_compat.pl /lib/modules/3.2.0-26-generic-pae/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/oby/Desktop/media_build/v4l/firmware'
make[2]: Leaving directory `/home/oby/Desktop/media_build/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/oby/Desktop/media_build/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/oby/Desktop/media_build/v4l/firmware'
Kernel build directory is /lib/modules/3.2.0-26-generic-pae/build
make -C ../linux apply_patches
make[2]: Entering directory `/home/oby/Desktop/media_build/linux'
Patches for 3.2.0-26-generic-pae already applied.
make[2]: Leaving directory `/home/oby/Desktop/media_build/linux'
make -C /lib/modules/3.2.0-26-generic-pae/build SUBDIRS=/home/oby/Desktop/media_build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
  CC [M]  /home/oby/Desktop/media_build/v4l/altera-lpt.o
  CC [M]  /home/oby/Desktop/media_build/v4l/altera-jtag.o
  CC [M]  /home/oby/Desktop/media_build/v4l/altera-comp.o
  CC [M]  /home/oby/Desktop/media_build/v4l/altera.o
  CC [M]  /home/oby/Desktop/media_build/v4l/au0828-core.o
In file included from /home/oby/Desktop/media_build/v4l/au0828-core.c:24:0:
/home/oby/Desktop/media_build/v4l/../linux/include/linux/videodev2.h:67:31: fatal error: linux/v4l2-common.h: No such file or directory
compilation terminated.
make[3]: *** [/home/oby/Desktop/media_build/v4l/au0828-core.o] Error 1
make[2]: *** [_module_/home/oby/Desktop/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/oby/Desktop/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452.

```

**Notes:**
- About a month ago I succeded using the very same instructions. 
- Now, however, it fails om both this computer (where it worked before) and on another computer (with borth 3.0 and 3.2 kernels).
- I found a patch report that might be relevant to this issue - but I have no idea how to apply the solution proposed: [https://patchwork.kernel.org/patch/1168531/](https://patchwork.kernel.org/patch/1168531/)

Does anyone have a clue about what I can do to get this to build?

---

### Post by narsaw on 2012-07-13
> **Oby said:**
> **OS:** Ubuntu 12.04, all apt-get updates as of today (including backports).

**Trying to**: Install drivers for the Happauge WinTV-HVR-930C, using these instructions: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C)

at step 3, I execute these command:
```
sudo rm -r media_build
 git clone git://linuxtv.org/media_build.git
 cd media_build
 ./build
```
The last one (./build) fails. Here is the output (excerpt):
```
WARNING: This is the V4L/DVB backport tree, with experimental drivers
	 backported to run on legacy kernels from the development tree at:
		http://git.linuxtv.org/media-tree.git.
	 It is generally safe to use it for testing a new driver or
	 feature, but its usage on production environments is risky.
	 Don't use it in production. You've been warned.
Created default (all yes) .config file
./scripts/fix_kconfig.pl
make[1]: Leaving directory `/home/oby/Desktop/media_build/v4l'
make -C /home/oby/Desktop/media_build/v4l 
make[1]: Entering directory `/home/oby/Desktop/media_build/v4l'
scripts/make_makefile.pl
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/oby/Desktop/media_build/v4l'
make[1]: Entering directory `/home/oby/Desktop/media_build/v4l'
perl scripts/make_config_compat.pl /lib/modules/3.2.0-26-generic-pae/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/oby/Desktop/media_build/v4l/firmware'
make[2]: Leaving directory `/home/oby/Desktop/media_build/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/oby/Desktop/media_build/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/oby/Desktop/media_build/v4l/firmware'
Kernel build directory is /lib/modules/3.2.0-26-generic-pae/build
make -C ../linux apply_patches
make[2]: Entering directory `/home/oby/Desktop/media_build/linux'
Patches for 3.2.0-26-generic-pae already applied.
make[2]: Leaving directory `/home/oby/Desktop/media_build/linux'
make -C /lib/modules/3.2.0-26-generic-pae/build SUBDIRS=/home/oby/Desktop/media_build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
  CC [M]  /home/oby/Desktop/media_build/v4l/altera-lpt.o
  CC [M]  /home/oby/Desktop/media_build/v4l/altera-jtag.o
  CC [M]  /home/oby/Desktop/media_build/v4l/altera-comp.o
  CC [M]  /home/oby/Desktop/media_build/v4l/altera.o
  CC [M]  /home/oby/Desktop/media_build/v4l/au0828-core.o
In file included from /home/oby/Desktop/media_build/v4l/au0828-core.c:24:0:
/home/oby/Desktop/media_build/v4l/../linux/include/linux/videodev2.h:67:31: fatal error: linux/v4l2-common.h: No such file or directory
compilation terminated.
make[3]: *** [/home/oby/Desktop/media_build/v4l/au0828-core.o] Error 1
make[2]: *** [_module_/home/oby/Desktop/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/oby/Desktop/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452.

```

**Notes:**
- About a month ago I succeded using the very same instructions. 
- Now, however, it fails om both this computer (where it worked before) and on another computer (with borth 3.0 and 3.2 kernels).
- I found a patch report that might be relevant to this issue - but I have no idea how to apply the solution proposed: [https://patchwork.kernel.org/patch/1168531/](https://patchwork.kernel.org/patch/1168531/)

Does anyone have a clue about what I can do to get this to build?


Same problem here. Anyone can explain how to apply the solution from the patch?

---

### Post by davidea on 2012-07-13
the patch , tell you to add the file (how if it need, do you have it , but you don't use it!)

```
+header-y += v4l2-common.h

```

but the problem is that make search for it and dont find it!!!

the file on my pc is located at,


/usr/src/linux-headers-3.0.0-23/include/media/v4l2-common.h

but suppling this path to the file 
```
davide@phenom:~/as102/media_build$ nano ./linux/include/linux/videodev2.h
```
don't resolve the problem

```
/home/davide/as102/media_build/v4l/../linux/include/media/v4l2-dev.h:127:2: error: unknown type name 'v4l2_std_id'
/home/davide/as102/media_build/v4l/../linux/include/media/v4l2-dev.h:128:2: error: unknown type name 'v4l2_std_id'

```

---

### Post by Oby on 2012-07-14
**Davidaea**: I think you are on to something. I was also able to identify the file, but I am unsure about how to tell media_build where it is... (Nano seems to be a wrong command, since its just a text teditor.)

**Alternatively**, it would be nice if someone could provide us with instructions on how to (manually) download and compile an older version of v4l. I knoiw for sure that the package that is about 1-1,5 months old will compile without issues on this computer.

---

### Post by pavelf on 2012-07-14
Save it as media_build/linux/include/linux/v4l2-common.h

```
#ifndef V4L2_COMMON_H
#define V4L2_COMMON_H

/* Hints for adjustments of selection rectangle */
#define V4L2_SEL_FLAG_GE        0x00000001
#define V4L2_SEL_FLAG_LE        0x00000002

/* Selection targets */

/* Current cropping area */
#define V4L2_SEL_TGT_CROP        0x0000
#define V4L2_SEL_TGT_CROP_ACTIVE        0x0000
/* Default cropping area */
#define V4L2_SEL_TGT_CROP_DEFAULT       0x0001
/* Cropping bounds */
#define V4L2_SEL_TGT_CROP_BOUNDS        0x0002
/* Current composing area */
#define V4L2_SEL_TGT_COMPOSE        0x0100
#define V4L2_SEL_TGT_COMPOSE_ACTIVE     0x0100
/* Default composing area */
#define V4L2_SEL_TGT_COMPOSE_DEFAULT    0x0101
/* Composing bounds */
#define V4L2_SEL_TGT_COMPOSE_BOUNDS     0x0102
/* Current composing area plus all padding pixels */
#define V4L2_SEL_TGT_COMPOSE_PADDED     0x0103

#endif //V4L2_COMMON_H

```

---

### Post by Oby on 2012-07-14
**YES - that seemed to do it!**

Thank you so very much!


EDIT: How do I mark the thread as solved?

---

### Post by fixitdude on 2012-07-14
Wow! Thanks pavelf !

Just do what he says and it works!

The question is why is there just a patch when all they have to do is put it in git and then all we would have to do is a "git clone" again?

It looks like someone moved a file and shouldn't have.

---

### Post by davidea on 2012-07-16
> **Oby said:**
> **YES - that seemed to do it!**

Thank you so very much!


EDIT: How do I mark the thread as solved?


hi, now it's work for me too, without patch , just git again!

edit the first post and change the title adding [solved]

---

### Post by grekpg on 2012-10-06
> **pavelf said:**
> Save it as media_build/linux/include/linux/v4l2-common.h

```
#ifndef V4L2_COMMON_H
#define V4L2_COMMON_H

/* Hints for adjustments of selection rectangle */
#define V4L2_SEL_FLAG_GE        0x00000001
#define V4L2_SEL_FLAG_LE        0x00000002

/* Selection targets */

/* Current cropping area */
#define V4L2_SEL_TGT_CROP        0x0000
#define V4L2_SEL_TGT_CROP_ACTIVE        0x0000
/* Default cropping area */
#define V4L2_SEL_TGT_CROP_DEFAULT       0x0001
/* Cropping bounds */
#define V4L2_SEL_TGT_CROP_BOUNDS        0x0002
/* Current composing area */
#define V4L2_SEL_TGT_COMPOSE        0x0100
#define V4L2_SEL_TGT_COMPOSE_ACTIVE     0x0100
/* Default composing area */
#define V4L2_SEL_TGT_COMPOSE_DEFAULT    0x0101
/* Composing bounds */
#define V4L2_SEL_TGT_COMPOSE_BOUNDS     0x0102
/* Current composing area plus all padding pixels */
#define V4L2_SEL_TGT_COMPOSE_PADDED     0x0103

#endif //V4L2_COMMON_H

```

i save this file and still have error 

```
CC [M]  /tmp/v4l/media_build/v4l/ivtv-yuv.o
  CC [M]  /tmp/v4l/media_build/v4l/m5mols_core.o
/tmp/v4l/media_build/v4l/m5mols_core.c: In function 'm5mols_set_frame_desc':
/tmp/v4l/media_build/v4l/m5mols_core.c:636:24: error: 'SZ_1M' undeclared (first use in this function)
/tmp/v4l/media_build/v4l/m5mols_core.c:636:24: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/tmp/v4l/media_build/v4l/m5mols_core.o] B&#322;&#261;d 1
make[2]: *** [_module_/tmp/v4l/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make[1]: *** [default] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/tmp/v4l/media_build/v4l'
make: *** [all] B&#322;&#261;d 2
build failed at ./build line 452.

```

---

### Post by sfilipow on 2012-12-13
Hi

I added v4l2-common.h but also found this file in:
linux/include/media/v4l2-common.h
linux/include/uapi/linux/v4l2-common.h

I got another error saying that dma-buf.h is missing.
Can not find it in the system. Where can I get it from if it is required? 
  
  CC [M]  /home/pundit/v4l/media_build/v4l/v4l2-dev.o
  CC [M]  /home/pundit/v4l/media_build/v4l/v4l2-ioctl.o
In file included from /home/pundit/v4l/media_build/v4l/v4l2-ioctl.c:30:0:
/home/pundit/v4l/media_build/v4l/../linux/include/media/videobuf2-core.h:19:27: fatal error: linux/dma-buf.h: No such file or directory
compilation terminated.
make[3]: *** [/home/pundit/v4l/media_build/v4l/v4l2-ioctl.o] Error 1
make[2]: *** [_module_/home/pundit/v4l/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/pundit/v4l/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452.

---

### Post by gangr33n on 2012-12-14
> **sfilipow said:**
> Hi

I added v4l2-common.h but also found this file in:
linux/include/media/v4l2-common.h
linux/include/uapi/linux/v4l2-common.h

I got another error saying that dma-buf.h is missing.
Can not find it in the system. Where can I get it from if it is required? 
  
  CC [M]  /home/pundit/v4l/media_build/v4l/v4l2-dev.o
  CC [M]  /home/pundit/v4l/media_build/v4l/v4l2-ioctl.o
In file included from /home/pundit/v4l/media_build/v4l/v4l2-ioctl.c:30:0:
/home/pundit/v4l/media_build/v4l/../linux/include/media/videobuf2-core.h:19:27: fatal error: linux/dma-buf.h: No such file or directory
compilation terminated.
make[3]: *** [/home/pundit/v4l/media_build/v4l/v4l2-ioctl.o] Error 1
make[2]: *** [_module_/home/pundit/v4l/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/pundit/v4l/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452.

I came looking with the same issue, it looks like the DMA Buffer structure was introduced in the Linux 3.3 kernel - is it possible you are using an older version of the kernel? If so you will need to update.

---

