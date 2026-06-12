---
title: "mplayer/vlc vaapi+xvba strange problem"
date: 2011-06-14
forum: Multimedia Software
---

### Post by mony87 on 2011-06-14
Hi. Currently running kubuntu 11.04 with latest catalyst from amd.com (also tried the one in the repo before with the same result).
Long story short. I've installed last libva and vlc from [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
After that i've installed the latest xvba and vlc segfaults. I have also compiled mplayer-vaapi and it doesnt work either. I dont get it why, because i had the exact same setup at opensuse 11.4 and had no problems whatsoever.

Here is output from vaainfo

```
vainfo
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
```

From what i see everything should be ok. Fglrx is working for sure:

```
fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6570M/5700 Series
OpenGL version string: 4.1.10750 Compatibility Profile Context
```

Here is the output from vlc with enabled hardware acceleration:

```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x17d8120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x265c230] dts decoder: DTS channels:6 samplerate:48000 bitrate:1536000
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
Segmentation fault

```

I've also tried to use the .debs from [http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/amd64/](http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/amd64/) and its all the same. Also with older version of xvba that i used with suse (0.7.8) its the same. Please give me some advice because i'm pretty stuck atm :(

---

### Post by mony87 on 2011-06-20
*bump*

---

### Post by pagemaker on 2011-07-12
Exact same problem here... I'm using Catalyst 11.6 with the hacked files from catalysthacks but I get the same "segmentation fault" as mony87 above...

When I check "GPU Acceleration" inside VLC, the program just exits when I try to open a 720p/1080p mkv file. But when I double-click on the same file, the video plays just fine. If I uncheck "GPU acceleration" all is good.

How can I check if I indeed have hardware acceleration when checking "GPU Acceleration"?

---

### Post by finomeno on 2011-07-25
Same problem with all the latest files.

vlc -vv outputs
```
[0x92b9bac] avcodec decoder debug: trying to use direct rendering
[0x92b9bac] avcodec decoder debug: Available decoder output format 61 (Unknown)
[0x92b9bac] avcodec decoder debug: Available decoder output format 53 (PIX_FMT_VAAPI_VLD)
[0x92b9bac] avcodec decoder debug: Trying VA API
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
Segmentation fault
```

DRI was written automatically into xorg.conf, so should be loading... apparently.

I thought my VLC was segfaulting either way - with overlay enabled or disabled - so I was wondering whether there was a way I could make VLC work at least without overlay. I found that the the 'Accelerated video output (Overlay)' option in the 'Video' section of VLC settings is not the one responsible for direct rendering, but the 'Use GPU acceleration (experimental)' option under 'Input & Codecs'.
This is a bit confusing.
What is the difference between accelerated video output and GPU acceleration?

---

### Post by .... on 2011-07-25
Unfortunately, I think the answer comes down to rebuilding libav/ffmpeg with the new libva. I'm really hoping that the libva changes from Splitted Desktop get merged upstream and this won't be a problem from Oneiric onward. I'm going to see if the catalyst hacks PPA maintainer will upload libav and maybe VLC again.

---

### Post by Tarmael on 2011-09-19
I had the EXACT SAME ISSUE!!


If you are also using 64bit, here's how to solve it:

VLC uses the libva in /usr/lib32
Just link what ever version of libva from /usr/lib/ to /usr/lib32

e.g.
```
sudo ln -s /usr/lib/libva.so.1 /usr/lib32/libva.so.1.0.8
```
May as well put in the libva-x11.so.1 into /usr/lib32, too.

Hope this is it!

---

