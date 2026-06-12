---
title: "modprobe nvidia every time I boot"
date: 2008-05-25
forum: Multimedia Software
---

### Post by mor22 on 2008-05-25
Hello All,

I have a problem where by every time I boot I have to 

```

sudo /etc/init.d/gdm stop 
sudo rmmod nvidia
sudo modprobe nvidia
sudo /etc/init.d/gdm start 

```

from a terminal.  I have these errors in from dmesg

```

[  176.432772] NVRM: API mismatch: the client has the version 169.12, but
[  176.432777] NVRM: this kernel module has the version 71.86.04.  Please
[  176.432779] NVRM: make sure that this kernel module and all NVIDIA driver
[  176.432781] NVRM: components have the same version.
[  176.476495] lirc_pvr150: bt878 #0 [sw]: no devices found
[  181.541019] NVRM: API mismatch: the client has the version 169.12, but
[  181.541023] NVRM: this kernel module has the version 71.86.04.  Please
[  181.541025] NVRM: make sure that this kernel module and all NVIDIA driver
[  181.541028] NVRM: components have the same version.
[  186.664642] NVRM: API mismatch: the client has the version 169.12, but
[  186.664646] NVRM: this kernel module has the version 71.86.04.  Please
[  186.664648] NVRM: make sure that this kernel module and all NVIDIA driver
[  186.664650] NVRM: components have the same version.
[ 1199.771097] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[ 1202.607097] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[ 1202.607118] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 1202.607183] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

where the lowest 4 lines apear after I reload the nvidia module.  It looks like it is trying to load the wrong module on boot. How can I get it to load the right one that I load from the command line?


Thanks!

---

### Post by nick_h on 2008-05-25
What video drivers have you installed?

It could be that a residual file has been left behind from a previous installation.  Have a look in /lib/linux-restricted-modules.  Type:
```
ls -al /lib/linux-restricted-modules
```

If you downloaded a driver from the nvidia website then you will have to disable the ubuntu restricted driver.

---

### Post by mor22 on 2008-06-01
Thanks for the advice. It appears to have fixed itself when I upgraded the kernel and modules.

---

