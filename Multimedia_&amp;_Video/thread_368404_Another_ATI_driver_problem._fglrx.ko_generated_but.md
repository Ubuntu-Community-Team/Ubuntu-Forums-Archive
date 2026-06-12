---
title: "Another ATI driver problem. fglrx.ko generated but missing in package"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by TTL on 2007-02-23
Hello,
I am using Kubuntu Dapper and have installed the latest Kernel 2.6.20.1 from source. I followed the howtos described here in the forum, added the patches needed for the new kernel, made the kernel source directory working with the installer and so on...
[I]
ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
dpkg -i *.deb
module-assistant prepare
module-assistant update

@kernel headers directory:
sudo touch arch/i386/Makefile.cpu

extract arcive in usr/src/
tar xjf /usr/src/fglrx.tar.bz2

Make make.sh executable:
chmod +x modules/fglrx/make.sh

@/tmp/scratch/modules/fglrx (since the original ati does not work with the 2.6.20 kernel be default)
patch -p0 < fglrx-8.34.8-for-2.6.20.patch
sudo tar cjf /usr/src/fglrx.tar.bz2 modules
popd
module-assistant build,install fglrx-kernel --kernel-dir=/usr/src/kernel-headers-2.6.20.1
[/I]
I am so far that there is a fglrx.ko module generated in /usr/src/modules/fglrx (needed a half day to figure this out). A /usr/src/fglrx-kernel-_8.34.8-1_i386.deb is generated too. I can install this package but it does ** not ** contain a fglrx.ko file.

Please help... :confused:

---

### Post by skug on 2007-02-23
Hmm... as you describe in the post you seem to be using an older version of the fglrx driver tha what the patch was made for... try using the 8.34.x driver instead.

---

### Post by TTL on 2007-02-24
I tried the the 8.34.8 ddriver too. This did not make any difference.

---

### Post by TTL on 2007-03-08
Ok I did a manual copy
```

cp /usr/src/modules/fglrx/fglrx.ko /lib/modules/2.6.20.1/kernel/drivers/char/drm/fglrx.ko
/sbin/depmod -a

```
The second command was the one I did not know.

Now the 3D acceleration is working again. :) 

But the question why the fglrx.ko module did not found his way in the .deb package remains...

---

