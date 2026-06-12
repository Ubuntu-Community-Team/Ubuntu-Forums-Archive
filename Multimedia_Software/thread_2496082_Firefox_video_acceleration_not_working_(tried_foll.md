---
title: "Firefox video acceleration not working (tried following all relevant guides)"
date: 2024-03-13
forum: Multimedia Software
---

### Post by graur777 on 2024-03-13
Hi all,

I know this has been discussed over and over again - however, I can't seem to be able to get the results needed after following most of the relevant guides I've found on Google. Let's take for instance [**this one**]("https://amigotechnotes.wordpress.com/2022/07/20/enable-firefox-hardware-video-acceleration-on-ubuntu/").

intel_gpu_top is reporting 0% on Video when I play any youtube video.

```
$ uname -a
Linux loonix 6.5.0-25-generic #25~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Feb 20 16:09:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```
```
$ firefox -v
Mozilla Firefox 123.0.1
```
```
$ vainfo
libva info: VA-API version 1.14.0
libva info: User environment variable requested driver 'iHD'
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_14
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.14 (libva 2.12.0)
vainfo: Driver version: Intel iHD driver for Intel(R) Gen Graphics - 22.3.1 ()
vainfo: Supported profile and entrypoints
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileNone                   :    VAEntrypointStats
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSliceLP
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSliceLP
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSliceLP
      VAProfileVP8Version0_3          :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointEncSliceLP
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileHEVCMain10             :    VAEntrypointEncSliceLP
      VAProfileVP9Profile0            :    VAEntrypointVLD
      VAProfileVP9Profile1            :    VAEntrypointVLD
      VAProfileVP9Profile2            :    VAEntrypointVLD
      VAProfileVP9Profile3            :    VAEntrypointVLD
      VAProfileHEVCMain12             :    VAEntrypointVLD
      VAProfileHEVCMain422_10         :    VAEntrypointVLD
      VAProfileHEVCMain422_12         :    VAEntrypointVLD
      VAProfileHEVCMain444            :    VAEntrypointVLD
      VAProfileHEVCMain444            :    VAEntrypointEncSliceLP
      VAProfileHEVCMain444_10         :    VAEntrypointVLD
      VAProfileHEVCMain444_10         :    VAEntrypointEncSliceLP
      VAProfileHEVCMain444_12         :    VAEntrypointVLD
      VAProfileHEVCSccMain            :    VAEntrypointVLD
      VAProfileHEVCSccMain            :    VAEntrypointEncSliceLP
      VAProfileHEVCSccMain10          :    VAEntrypointVLD
      VAProfileHEVCSccMain10          :    VAEntrypointEncSliceLP
      VAProfileHEVCSccMain444         :    VAEntrypointVLD
      VAProfileHEVCSccMain444         :    VAEntrypointEncSliceLP
      VAProfileAV1Profile0            :    VAEntrypointVLD
      VAProfileHEVCSccMain444_10      :    VAEntrypointVLD
      VAProfileHEVCSccMain444_10      :    VAEntrypointEncSliceLP
```
```
$ cat .profile 
#[...]
export LIBVA_DRIVER_NAME=iHD
export MOZ_DISABLE_RDD_SANDBOX=1
export MOZ_ENABLE_WAYLAND=1
```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293487&stc=1[/IMG]

I don't know if the above blocklist strings have anything to do with it, but any help is much appreciated.

System specs:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293488&stc=1[/IMG]

---

### Post by TheFu on 2024-03-13
[https://www.phoronix.com/review/linux-68-features](https://www.phoronix.com/review/linux-68-features)  and
[https://www.phoronix.com/news/Intel-Xe-KMD-Mesa-24.1-Default](https://www.phoronix.com/news/Intel-Xe-KMD-Mesa-24.1-Default)
Don't know if this means anything to you.

> This doesn't change the fact that the Intel Xe driver is opt-in for supported Intel graphics hardware (Tiger Lake and newer) but just means that if/when you do switch over to the Xe kernel driver, Mesa 24.1+ will jive just fine without having to worry about rebuilding Mesa or taking any extra steps. 

Please post text, not inline images. More efficient and this isn't an MS-Windows forum.

---

### Post by Yellow Pasque on 2024-03-14
Are you using a real Firefox package or the snap version?

> **TheFu said:**
> [https://www.phoronix.com/review/linux-68-features](https://www.phoronix.com/review/linux-68-features)  and
[https://www.phoronix.com/news/Intel-Xe-KMD-Mesa-24.1-Default](https://www.phoronix.com/news/Intel-Xe-KMD-Mesa-24.1-Default)
Don't know if this means anything to you.

It's not relevant here. The old 'i915' kernel module still works and is what Ubuntu 22.04 users will be running (I don't know if 24.04 will use the new 'xe' module by default or not). Anyway, the vainfo looks good, so probably best not to confuse the OP with "driver" issues here.

---

