---
title: "WinFF"
date: 2008-08-19
forum: Multimedia Software
---

### Post by cesaregb on 2008-08-19
Hi all i dont know why but I have probles with this program i keep getting this error

Seems stream 0 codec frame rate differs from container frame rate: 29.97 (30000/1001) -> 59.94 (60000/1001)
Input #0, mpeg, from '/media/disk/Documents and Settings/cesar/Desktop/lost/VTS_04_1.VOB':
Duration: 00:41:46.3, start: 0.280633, bitrate: 3427 kb/s
Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 9800 kb/s, 59.94 fps(r)
Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, 5 channels, 384 kb/s
Stream #0.2[0x81]: Audio: 0x0000, 48000 Hz, stereo, 192 kb/s
Stream #0.3[0x82]: Audio: 0x0000, 48000 Hz, stereo, 192 kb/s
Stream #0.4[0x20]: Subtitle: dvdsub
Stream #0.5[0x21]: Subtitle: dvdsub
Stream #0.6[0x22]: Subtitle: dvdsub
Stream #0.7[0x23]: Subtitle: dvdsub
Stream #0.8[0x24]: Subtitle: dvdsub
Stream #0.9[0x25]: Subtitle: dvdsub
Stream #0.10[0x26]: Subtitle: dvdsub
Stream #0.11[0x27]: Subtitle: dvdsub
Unknown codec 'xvid'

could anyone help me 

is there anything else that i can do, i install this same program in the same machine with windows so dont know what a.... can be

---

### Post by mocha on 2008-08-19
It has to do with ffmpeg, not WinFF, that's why it works ok in Windows.  I suggest you compile your own ffmpeg so that you can enable all of the encoding capabilites.  Or I believe you can install the version from the medibuntu repository which does not have as many format restrictions.  Also note that ffmpeg has done strange things with the command line switches.  For example, the xvid codec is called with libxvid now.  You have to double check the presets in WinFF to make sure the switches are correct.

---

### Post by cesaregb on 2008-08-19
I solved, it was something with the ubuntu installations 

thanks a lot

---

