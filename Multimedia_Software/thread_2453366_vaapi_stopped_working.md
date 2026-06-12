---
title: "vaapi stopped working?"
date: 2020-11-09
forum: Multimedia Software
---

### Post by tux-peng on 2020-11-09
[5700XT]("https://pcpartpicker.com/list/g8B63t")

I've been using
```
ffmpeg -i  "./video.mp4"   -vaapi_device /dev/dri/renderD128 -vcodec hevc_vaapi -vf format='vaapi,hwupload'  -vf scale=960x720:flags=lanczos -c:v libx264 -preset slow -crf 21  "./upscaled/vido.mp4"
```

today it gave me an error```


[AVHWDeviceContext @ 0x55b025ed1340] No VA display found for device /dev/dri/renderD128.
Device creation failed: -22.
Failed to set value '/dev/dri/renderD128' for option 'vaapi_device': Invalid argument
Error parsing global options: Invalid argument

```

I can't figure out what update broke this, I use only FOSS drivers
```
$ uname -a
Linux 3900x 5.8.0-7625-generic #26~1604441477~20.10~d41e407-Ubuntu SMP Wed Nov 4 01:25:00 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```
```
$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 11.0.0, 256 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 20.3.0-devel (git-fb1793b 2020-11-08 groovy-oibaf-ppa)
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.1 Mesa 20.3.0-devel (git-fb1793b 2020-11-08 groovy-oibaf-ppa)
OpenGL shading language version string: 1.40
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.3.0-devel (git-fb1793b 2020-11-08 groovy-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```
> $ vainfo
libva info: VA-API version 1.8.0
libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)
vaInitialize failed with error code -1 (unknown libva error),exit


I even installed [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) to try to get it working

---

### Post by wildmanne39 on 2020-11-09
*Thread moved to **Multimedia Software for a more appropriate fit**.*

---

