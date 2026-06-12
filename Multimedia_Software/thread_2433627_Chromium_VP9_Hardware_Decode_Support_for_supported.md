---
title: "Chromium VP9 Hardware Decode Support for supported NVIDIA VDPAU cards [experimental]"
date: 2019-12-22
forum: Multimedia Software
---

### Post by xtknight on 2019-12-22
I hope this is the right place to post this. This has been an ongoing issue for those with NVIDIA cards, so I've attempted to add VP9 support to the VDPAU/VA-API wrapper for NVIDIA here: [https://github.com/xtknight/vdpau-va-driver-vp9](https://github.com/xtknight/vdpau-va-driver-vp9)

It's still experimental, but this allows hardware accelerated viewing of YouTube videos tested up to 4k.

Testers are welcome. I've used it successfully on 19.10 with chromium-vaapi.

---

### Post by User-007 on 2020-01-03
I went through the installation. No VP9 support is presented in VDPAU info, though.

Using Mint 19 (18.04).

Edit: noticed that my GPU is not VP9-compliant.

---

### Post by Yellow Pasque on 2020-01-06
I tried this on the latest KDE Neon (forget the version number, but it's based off Ubuntu 18.04).
vainfo now shows vp9 support, but it doesn't show in the Nvidia Settings page:
```
$ vainfo 
libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.4
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG4Simple            : VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    : VAEntrypointVLD
      <unknown profile>               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
      VAProfileVP9Profile0            : VAEntrypointVLD
```

I am using:
- Nvidia driver 440.44 and libvdpau 1.3 from: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
- chromium and the vdpau-va-driver from: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Do I really need to build libvdpau from git? It looks like 1.3 should have the latest VP9 commit.
Thanks. This is badly needed and I hope chromium and Firefox can get their acts together.

Edit: I'm using a GTX950, which should support VP9: [https://en.wikipedia.org/wiki/Nvidia_PureVideo#Feature_Set_F](https://en.wikipedia.org/wiki/Nvidia_PureVideo#Feature_Set_F)

---

### Post by Yellow Pasque on 2020-01-06
It also seems odd that your build finds libvdpau headers, but doesn't report a version:
```
checking for LIBVA_DEPS... yes
checking for LIBVA_X11_DEPS... yes
checking for LIBVA_GLX_DEPS... yes
checking for VA drivers path... /usr/lib/x86_64-linux-gnu/dri
checking for VDPAU... yes
checking for VDPAU/MPEG-4 support... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating debian.upstream/Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing libtool commands

libva-vdpau-driver configuration summary:

VA-API version ................... : 1.1.0
VA-API drivers path .............. : /usr/lib/x86_64-linux-gnu/dri
VDPAU version .................... :
VDPAU/MPEG-4 support ............. : yes
GLX support ...................... : yes
```

---

