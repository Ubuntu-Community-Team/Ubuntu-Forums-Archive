---
title: "Mplayer which hardware accelleration type to use? Intel Nuc 'hd graphics'"
date: 2016-09-17
forum: Multimedia Software
---

### Post by ultragamer2 on 2016-09-17
Which hardware acceleration mode should I be using with an Intel Nuc N2820 with Intel HD graphics (on the cpu)?
[http://www.intel.com.au/content/www/au/en/nuc/nuc-kit-dn2820fykh.html](http://www.intel.com.au/content/www/au/en/nuc/nuc-kit-dn2820fykh.html)
There are various types such as gl gl1 gl2 vdpau, etc, etc. Some work, some don't but which one is the best with my cpu/graphics?

Is mplayer the best media player in Ubuntu to utilise hardware acceleration.

---

### Post by Yellow Pasque on 2016-09-18
Intel GPU?. Use va-api. Make sure it works:
```
sudo apt-get install vainfo
vainfo
```

> Is mplayer the best media player in Ubuntu to utilise hardware acceleration?
Probably not for va-api. I have no idea whether va-api is built into mplayer nowadays. You used to have to get a special version from a PPA. I switched to mpv a long time ago.

---

### Post by mc4man on 2016-09-18
I would also suggest mpv as it will use hwdec on supported files with just a simple option or conf line of hwdec=auto.

You could use mplayer on intel with the libvdpau-va-gl1 package & naming appropriate video out &  video codec, too much of a pita I think.
Ex. 
$ VDPAU_DRIVER=va_gl mplayer -vo vdpau -vc ffh264vdpau  /home/doug/Videos/amostviolentyear-clip1_h1080p.mov 
MPlayer SVN-r37881 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/Videos/amostviolentyear-clip1_h1080p.mov.
libavformat version 57.44.100 (internal)
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x55af37c0f760]Protocol name not provided, cannot determine if input is local or a network protocol, buffers and access patterns cannot be configured optimally without knowing the protocol
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 2: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1920x816  24bpp  23.976 fps  9277.7 kbps (1132.5 kbyte/s)
libva info: VA-API version 0.39.2
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
==========================================================================
Forced video codec: ffh264vdpau
ect.

---

