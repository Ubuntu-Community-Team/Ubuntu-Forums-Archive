---
title: "How can I get VAAPI to work with mesa 19 driver on AMD Raven Ridge?"
date: 2019-06-12
forum: Multimedia Software
---

### Post by boast on 2019-06-12
I am trying to get VAAPI working for my AMD Ryzen 2400G. 

VAAPI support seems to be there for ffmpeg:

```
$ ffmpeg -encoders|grep -i vaapi
Error: unable to open display 
ffmpeg version n4.1 Copyright (c) 2000-2018 the FFmpeg developers
...
 V..... h264_vaapi           H.264/AVC (VAAPI) (codec h264)
 V..... hevc_vaapi           H.265/HEVC (VAAPI) (codec hevc)
 V..... mjpeg_vaapi          MJPEG (VAAPI) (codec mjpeg)
 V..... mpeg2_vaapi          MPEG-2 (VAAPI) (codec mpeg2video)
 V..... vp8_vaapi            VP8 (VAAPI) (codec vp8)
```

But when running ffmpeg, I get the following:

```
    $ ffmpeg -threads 1 -i input.mkv -vaapi_device /dev/dri/renderD128 -vcodec h264_vaapi -vf format='nv12|vaapi,hwupload' output.mp4
    Error: unable to open display
    ffmpeg version n4.1 Copyright (c) 2000-2018 the FFmpeg developers
    ...
    libva info: VA-API version 0.39.0
    libva info: va_getDriverName() returns -1
    libva error: va_getDriverName() failed with unknown libva error,driver_name=(null)
    [AVHWDeviceContext @ 0xd12c80] Failed to initialise VAAPI connection: -1 (unknown libva error).
    Device creation failed: -5.
    Failed to set value '/dev/dri/renderD128' for option 'vaapi_device': Input/output error
    Error parsing global options: Input/output error
```

Which makes it look like my drivers are not working, but vainfo seems good:

```
    $ vainfo
    error: can't connect to X server!
    libva info: VA-API version 1.4.0
    libva info: va_getDriverName() returns 0
    libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
    libva info: Found init function __vaDriverInit_1_4
    libva info: va_openDriver() returns 0
    vainfo: VA-API version: 1.4 (libva 2.4.0)
    vainfo: Driver version: Mesa Gallium driver 19.0.2 for AMD RAVEN (DRM 3.27.0, 5.0.0-16-generic, LLVM 8.0.0)
    vainfo: Supported profile and entrypoints
          VAProfileMPEG2Simple            : VAEntrypointVLD
          VAProfileMPEG2Main              : VAEntrypointVLD
          VAProfileVC1Simple              : VAEntrypointVLD
          VAProfileVC1Main                : VAEntrypointVLD
          VAProfileVC1Advanced            : VAEntrypointVLD
          VAProfileH264ConstrainedBaseline: VAEntrypointVLD
          VAProfileH264ConstrainedBaseline: VAEntrypointEncSlice
          VAProfileH264Main               : VAEntrypointVLD
          VAProfileH264Main               : VAEntrypointEncSlice
          VAProfileH264High               : VAEntrypointVLD
          VAProfileH264High               : VAEntrypointEncSlice
          VAProfileHEVCMain               : VAEntrypointVLD
          VAProfileHEVCMain               : VAEntrypointEncSlice
          VAProfileHEVCMain10             : VAEntrypointVLD
          VAProfileJPEGBaseline           : VAEntrypointVLD
          VAProfileVP9Profile0            : VAEntrypointVLD
          VAProfileVP9Profile2            : VAEntrypointVLD
          VAProfileNone                   : VAEntrypointVideoProc
```

Device detected:

```
    $ lspci
    ...
    04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c6)
```

Driver loaded:

```
    $ dmesg|grep -i drm
    [    1.522225] [drm] amdgpu kernel modesetting enabled.
    [    1.522753] [drm] initializing kernel modesetting (RAVEN 0x1002:0x15DD 0x1002:0x15DD 0xC6).
    ...
    [    1.523212] [drm] amdgpu: 2048M of VRAM memory ready
    [    1.523213] [drm] amdgpu: 3072M of GTT memory ready.
    ...
    [    1.819246] [drm] Initialized amdgpu 3.27.0 20150101 for 0000:04:00.0 on minor 0
```

Any suggestions what I could be missing?

Edit: Installed kernel 5.1.9 and mesa-va-drivers 19.0.5 from dev but that didn't help.

---

### Post by mc4man on 2019-06-12
Are you using the snap version of ffmpeg? Seems likely, if so then vaapi hw encoding will not work, use the .deb version instead..

---

### Post by boast on 2019-06-12
> **mc4man said:**
> Are you using the snap version of ffmpeg? Seems likely, if so then vaapi hw encoding will not work, use the .deb version instead..

That was it. Thanks!

---

