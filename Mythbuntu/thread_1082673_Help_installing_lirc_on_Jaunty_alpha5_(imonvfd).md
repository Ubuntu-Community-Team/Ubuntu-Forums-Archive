---
title: "Help installing lirc on Jaunty alpha5 (imon/vfd)"
date: 2009-02-28
forum: Mythbuntu
---

### Post by Nirro on 2009-02-28
Hi All, I have Antec Micro Fusion Remote 350 case with iMon (0038), I'm trying to follow instructions around the web with no success.

This guide: [http://xbmc.org/forum/showthread.php?t=40290](http://xbmc.org/forum/showthread.php?t=40290) starts with patching the lirc 0.8.3 and compiling to support iMon, but I have 0.8.4a in Jaunty and that should be Ok,

So what I did is :
```
sudo apt-get install lirc lirc-modules source
```

and I get :
```
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build

Error!  Build of lirc_pvr150.ko failed for: 2.6.28-8-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.4a/build/ for more information.
Installing initial module

Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree.
You must run a dkms build for kernel 2.6.28-8-generic (x86_64) first.
Done.

```

Please help me, How should I continue ?

(p.s: I also have the pvr150 IR, but I want to use it only for IR Blaster, but that's for later).

Thanks,
Nir.

---

### Post by Nirro on 2009-02-28
I found this bug that looks similar but with Intrepid kernel

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/306346](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/306346)

---

### Post by Nirro on 2009-03-01
Hi,

I open a parallel thread in Jaunty forum about installing the imon lcd/ir (0038) in Jaunty.

maybe you can help me there ?
[http://ubuntuforums.org/showthread.php?p=6818168](http://ubuntuforums.org/showthread.php?p=6818168)


Thanks,
Nir.

---

