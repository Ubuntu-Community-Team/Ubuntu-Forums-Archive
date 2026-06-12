---
title: "ALSA 1.0.16 compiling problem"
date: 2008-04-30
forum: Multimedia Software
---

### Post by musty on 2008-04-30
Hi,

I'm trying to install alsa 1.0.16 from source in ubuntu studio 8.04 (because my echo gina 3g sound card is not detected at all). Working in the directory

/usr/src/alsa/alsa-driver-1.0.16

I try to configure (sudo ./configure) and get the following error:

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I checked the 'config.log' only to find the same error "cannot create executables."

I was wondering if anyone knows how to solve this problem or alternatively if anyone knows how to install alsa 1.0.16 in ubuntu studio 8.04 or if anyone knows how to get the echo gina 3g sound card working in ubuntu studio 8.04 (i.e. the newest ubuntu studio release)

Thanks,
mike musty

---

### Post by warp99 on 2008-04-30
> **musty said:**
> Hi,

I'm trying to install alsa 1.0.16 from source in ubuntu studio 8.04 (because my echo gina 3g sound card is not detected at all). Working in the directory

/usr/src/alsa/alsa-driver-1.0.16

I try to configure (sudo ./configure) and get the following error:

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I checked the 'config.log' only to find the same error "cannot create executables."

I was wondering if anyone knows how to solve this problem or alternatively if anyone knows how to install alsa 1.0.16 in ubuntu studio 8.04 or if anyone knows how to get the echo gina 3g sound card working in ubuntu studio 8.04 (i.e. the newest ubuntu studio release)

Thanks,
mike musty
Run the following:
```
sudo apt-get build-dep alsa-source
```
this should download the dependencies to build the ALSA source package. You also need to install the following if not installed:
```
sudo apt-get install fakeroot kernel-package module-assistant linux-headers-$(uname -r)
```
then you have all of the correct components to build the ALSA modules.

---

### Post by musty on 2008-04-30
Thank you for your help. Everything is working great. Your help is very much appreciated.

---

