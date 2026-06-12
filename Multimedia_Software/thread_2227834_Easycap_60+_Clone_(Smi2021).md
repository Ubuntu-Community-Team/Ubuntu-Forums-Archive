---
title: "Easycap 60+ Clone (Smi2021)"
date: 2014-06-04
forum: Multimedia Software
---

### Post by icloudthemes on 2014-06-04
Hi,

I have been trying to compile the kernel along with the kernel modules for the easycap smi2021 chipset and i get everything correct execpt for the module compile. 

Here are the steps i took and my system information 

#lsb_release -a 

```

#lsb_release -a
Distributor ID:    Ubuntu 
Description:    Ubuntu 12.04.4 LTS 
Release:    12.04 
Codename:    precise
arch: 64bit
```

Now I followed these instructions foudn on this link [here]("https://code.google.com/p/easycap-somagic-linux/wiki/BuildingKernelModule")

```

git clone git://github.com/torvalds/linux.git v4l-dvb

cd v4l-dvbgit remote add linuxtv git://linuxtv.org/media_tree.gitgit remote update  

git checkout -b media-master remotes/linuxtv/master   wget --no-check-certificate https://patchwork.linuxtv.org/patch/20010/mbox/ -O smi2021v3.patchgit checkout -b smi2021v3

git am smi2021v3.patch

make oldconfig

make prepare

make modules_prepare

make M=drivers/media/i2c modules

make M=drivers/media/usb/smi2021 modules

```


Now my goal to to compile the entire kernel but before I start compiling i test the modules i require.

Now the problem is when i come to compile the smi2021 modules I get this error.

```

root@e:/usr/src/v4l-dvb# make M=drivers/media/usb/smi2021 modules\

>     WARNING: Symbol version dump /usr/src/v4l-dvb/Module.symvers            
                       is missing; modules will have no dependencies and modversions.    

     CC [M]  drivers/media/usb/smi2021/smi2021_main.o 
drivers/media/usb/smi2021/smi2021_main.c: In function `smi2021_usb_probe`: 
drivers/media/usb/smi2021/smi2021_main.c:882:2: error: `const struct v4l2_subdev_core_ops` has no member named `s_std` 
drivers/media/usb/smi2021/smi2021_main.c:882:2: error: `const struct v4l2_subdev_core_ops` has no member named `s_std` 
make[1]: *** [drivers/media/usb/smi2021/smi2021_main.o] Error 1 
make: *** [_module_drivers/media/usb/smi2021] Error 2
```



Any insight and or help will be appreciated.

---

