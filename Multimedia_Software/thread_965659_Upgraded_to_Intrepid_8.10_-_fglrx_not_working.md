---
title: "Upgraded to Intrepid 8.10 - fglrx not working"
date: 2008-10-31
forum: Multimedia Software
---

### Post by bjtuna on 2008-10-31
I was running the fglrx Catalyst drivers, installed off the ATI site, on Hardy. I ran the dist-upgrade to Intrepid today and when I rebooted, it told me that it had to throw itself into Low Graphics mode.

The restricted drivers tool shows the FGLRX driver is installed and activated. My xorg.conf hasn't changed. My hardware is a Radion 3650.

Any ideas?

---

### Post by bjtuna on 2008-11-01
bump... any ideas?

---

### Post by bjtuna on 2008-11-01
It looks like I'm getting the following backtrace in Xorg.log:
```

(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.54.3
	ABI class: X.Org Server Extension, version 1.1
(II) fglrx(0): Using adapter: 1:0.0.

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f6b400]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPcsLoadKernelDatabase+0xbc) [0xb770b4cc]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb76e9ffa]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x764) [0xb76e2d44]
5: /usr/X11R6/bin/X(InitOutput+0x96f) [0x80aac9f]
6: /usr/X11R6/bin/X(main+0x279) [0x8071b19]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b6e685]
8: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.

```

---

### Post by jfmacaud on 2008-11-03
Same here on AMD64+HD3200 although the problem started when upgrading to kernel 2.6.24.21 in Hardy. I was hoping Intrepid would fix this. While in failsafe mode, the "hardware drivers" tool tells me that "A different version of this driver is in use", which sounds weird.


(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.54.3
	ABI class: X.Org Server Extension, version 1.1
(II) fglrx(0): Using adapter: 1:5.0.

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x65) [0x480f35]
1: /lib/libc.so.6 [0x7f2df7162060]
2: /lib/libc.so.6(strlen+0x30) [0x7f2df71b16b0]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7f2df5d30cff]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPcsLoadKernelDatabase+0xb4) [0x7f2df5d30884]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7f2df5d12e4a]
6: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x67d) [0x7f2df5d0d11d]
7: /usr/X11R6/bin/X(InitOutput+0x969) [0x46a189]
8: /usr/X11R6/bin/X(main+0x286) [0x433526]
9: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f2df714d466]
10: /usr/X11R6/bin/X [0x432ad9]
Saw signal 11.  Server aborting.

---

### Post by cro on 2008-11-03
I've also been seeing this error after an upgrade to 8.10. I didn't have any problems with the previous release as I installed the ATI drievrs from source.

I run dual monitors so initially I was distracted by thoughts that the driver was failing on dual monitor support, but the Xorg.0.log file shows the exact same X error.

---

### Post by cro on 2008-11-03
I have solved my own problem.

I noticed that this same error was caused by another kernel module in relation to 2.6.27. Checking dkms (dkms status) showed that the fglrx module was installed for 2.6.27, but the vboxdrv module was installed for 2.6.24.

Disabling all kernel modules installed by dkms for other kernels solved the problem entirely.

---

### Post by bjtuna on 2008-11-03
> **cro said:**
> I have solved my own problem.

I noticed that this same error was caused by another kernel module in relation to 2.6.27. Checking dkms (dkms status) showed that the fglrx module was installed for 2.6.27, but the vboxdrv module was installed for 2.6.24.

Disabling all kernel modules installed by dkms for other kernels solved the problem entirely.

cro, my 'dkms status' was also showing some vboxdrv instances for multiple kernels, I uninstalled them all but the problem remains. I'm glad you got yours working, though.

---

### Post by alejandron on 2008-11-03
cro workaround at [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284505/comments/14](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284505/comments/14). did work out for me. Have you removed execution permisions to /etc/init.d/vboxdrv to test whether is this preventing your fglrx to load?

---

### Post by bjtuna on 2008-11-03
cro, alejandron -- please stop marking these bugs and threads as duplicates and/or solved.  Your fix worked for you, which is great, but it did not work for me and I consider the issue still unresolved and in need of attention from the package maintainers.

Cheers, -B

---

### Post by cro on 2008-11-03
> **bjtuna said:**
> cro, alejandron -- please stop marking these bugs and threads as duplicates and/or solved.  Your fix worked for you, which is great, but it did not work for me and I consider the issue still unresolved and in need of attention from the package maintainers.

The bugs (not threads) I marked as dupes were those that appeared to be dupes.

I've also not marked any thread solved, I have simply given as much information about how I managed to resolve the issue that is affecting what appears to be a large number of users, and have tried to explain my thinking behind the steps I took to recreate, diagnose and then fix the issue.

The issue you mentioned in your initial post is an error I have also encountered during the various steps to recreate and fix this issue, so I do think that my experience is relevant to your problem.

In addition, the backtrace you are seeing is also the same one I saw, and my posts have been related to how I stopped X from throwing this error. The additional steps and information I have given have been in an attempt to give the package maintainers an understanding of how I resolved the issue within my hardware setup, and to give them additional information that may be useful in resolving the issue across the board.

You might try this:

Remove fglrx.
Remove all ATI modules.
Disable all non 2.6.27  modules.
Reboot.
Re-install restricted drivers using Jockey.
Reboot.
Run amdcccle as root to set resolution if you don't get the error.

It took me a few fiddles with the ATI drivers to get them installed, but removing the non 2.6.27 modules stopped the X crash, allowing me to go through the normal driver install process. I also used EnvyNG at one point, but that may not be relevant.

The ia32 libraries for ATI will also be needed if you're on x86_64. You might also want to regenerate your xorg.conf to remove all the settings from X1.3.

---

