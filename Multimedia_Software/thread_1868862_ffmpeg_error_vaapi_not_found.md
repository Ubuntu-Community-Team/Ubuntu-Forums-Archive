---
title: "ffmpeg error: vaapi not found"
date: 2011-10-24
forum: Multimedia Software
---

### Post by 10robinho on 2011-10-24
Hi guys,

I'm trying to compile ffmpeg with --enable-vaapi option, but with no success.

here is my vainfo:

```

libva: libva version 0.32.0-sds-2
libva: User requested driver 'fglrx'
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
VAProfileH264High : VAEntrypointVLD
VAProfileVC1Advanded : VAEntrypointVLD

```and when i try in ffmpeg git dir

```

./configure --enable-vaapi

```I get
```

ERROR: vaapi not found

```in conf.log I have va/va.h: No such file or directory

Please, help!:(

---

### Post by FakeOutdoorsman on 2011-10-25
What is your version of Ubuntu? Are you compiling FFmpeg from Git or a release version?

---

### Post by 10robinho on 2011-10-28
I'm using 11.04, and ffmpeg form git.

Sorry for the late reply, I didn't noticed

---

### Post by FakeOutdoorsman on 2011-10-28
You probably need to install **libva-dev**. FFmpeg should then autodetect VAAPI so the *--enable-vaapi* is unnecessary. More more detailed instructions see:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

