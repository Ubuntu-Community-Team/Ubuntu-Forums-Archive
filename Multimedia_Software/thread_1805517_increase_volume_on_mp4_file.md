---
title: "increase volume on mp4 file"
date: 2011-07-16
forum: Multimedia Software
---

### Post by davidtuti on 2011-07-16
Hi,
I would like some application (with command line) to can increase volume of a some mp4 files.

Many thanks and sorry for my english!

---

### Post by andrew.46 on 2011-07-16
Perhaps you could use the -vol option with FFmpeg:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -h | grep vol[/COLOR]**
ffmpeg version N-31484-gb43ca2d, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul 15 2011 10:46:00 with gcc 4.5.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-amrwbenc --enable-libvo-aacenc --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version3
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  8. 0 / 53.  8. 0
  libavformat  53.  6. 0 / 53.  6. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 26. 0 /  2. 26. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
**[COLOR="Red"]-vol volume         change audio volume (256=normal)[/COLOR]**

```

---

