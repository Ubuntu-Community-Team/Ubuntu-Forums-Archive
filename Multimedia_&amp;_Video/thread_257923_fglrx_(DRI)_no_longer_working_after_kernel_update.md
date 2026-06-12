---
title: "fglrx (DRI) no longer working after kernel update"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by ltmon on 2006-09-15
It seems the latest kernel update has destroyed my fglrx drivers in some manner.

I have tried reinstalling and just about every different way of installing and configuring the drivers that have been suggested in these forums, but always with the same result and the same error message.

I am now back to just the standard drivers from the dapper repositories.

Firstly, when the fglrx module tries to load (or I force it with "modprobe") dmesg shows the following error:
```

fglrx: disagrees about version of symbol boot_cpu_data
fglrx: Unknown symbol boot_cpu_data

```

Whilst in Xorg.0.log:
```

(EE) fglrx(0): Fail to initialize ASIC in kernel.
...
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

I hope somebody can help, because after a few hours of Googling I've run out of different things to try: nothing I've tried seems to make a difference to these errors.

L.

---

### Post by detectiveinspekta on 2006-09-15
If you reload your drivers from scratch it will work. There is a easy solution but I forgot.

---

### Post by elettronicha on 2006-09-15
If you built them from source, I think you should first uninstall the old fglrx-kernel-2.6.15-26-686 package, remove the old .deb contained in /usr/src/ and then rebuild the package with the usual procedure described in some wiki-page.

---

### Post by KabalS on 2006-09-15
Same problem here.. 
I'm using seveas repository because i can't compile the drivers from scratch.
Any other solution is appreciated.
Thanks

---

### Post by Stemp on 2006-09-15
+1

---

### Post by ephman on 2006-09-15
hi,

i'm pretty sure you just have to recompile the kernel module after each kernel update.  

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

and then to confirm that it worked just 

fglrxinfo

and i'm pretty sure that should do the trick.

good luck,
ephman

---

### Post by Stemp on 2006-09-15
Thanks, it's working for me ;)

---

### Post by KabalS on 2006-09-15
Didin't worked for me. probably this is because i cannot compile the drivers from scratch and i have to install the saveas drivers.

dmesg:
```

[17179599.960000] fglrx: disagrees about version of symbol boot_cpu_data
[17179599.960000] fglrx: Unknown symbol boot_cpu_data

```
Xorg.0.log:
```

[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
Is there another way?

---

### Post by ltmon on 2006-09-16
Hi All,

Thanks for the replies, but I am actually using the drivers in the repository.

I have tried compiling from scratch also, but that resulted in exactly the same problem.  So I have currently reverted to the standard repository drivers.

Any more ideas?


Thanks,

L.

---

### Post by tseliot on 2006-09-16
If you want to use my testing repository and see if it works you can have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

---

### Post by ltmon on 2006-09-16
Thanks all for the help, I've found the culprit.

One repository or another that I had added to my sources.list had a weird kernel version in it.  I removed all the various repositories I had collected and downgraded the kernel to the latest one in the Ubuntu official repositories and rebooted.

The new ati drivers are also working very well thanks tseliot.

L.

---

### Post by AquaFox90 on 2006-09-16
Could you please tell me what that is cause I am experiencing the same problem.

---

### Post by AquaFox90 on 2006-09-16
I really need help guys I've been up all night for this simple problem. I never knew ATi would bring this many problems :frown: .

---

### Post by ltmon on 2006-09-16
@AquaFox90

To tell if you have the same problem as myself, type this into a terminal:
```

> dpkg-query -l linux-image-`uname -r`

```

There's a column in the output called "Version", take note of this.

It should be (for my architecture anyway) 2.6.15-26.47.

If it isn't this version then post it here, and I'll let you know how to fix it.

L.

---

### Post by prvul on 2006-10-07
I have same problem. My output is:

linux-image-2. 2.6.15-26.46

---

