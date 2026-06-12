---
title: "Transcode video stabilize not working at me"
date: 2011-07-15
forum: Multimedia Software
---

### Post by buddig on 2011-07-15
I have installed [transcode]("http://www.transcoding.org") to make [stabilie videos]("http://public.hronopik.de/vid.stab/features.php?lang=en") from handheld camera.

```
henning@henning-Lenovo-G550:~$ transcode -J stabilize -i ./Videos/MVI_7727.AVI -y null,null -o dummytranscode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[transcode] V: auto-probing     | ./Videos/MVI_7727.AVI (OK)
[transcode] V: import format    | MJPEG in RIFF data, AVI (module=ffmpeg)
[transcode] A: auto-probing     | ./Videos/MVI_7727.AVI (OK)
[transcode] A: import format    | PCM in RIFF data, AVI (module=raw)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 640x480  1.33:1  encoded @ 4:3
[transcode] V: bits/pixel       | 0.195
[transcode] V: decoding fps,frc | 30.000,5
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x1     PCM          [44100,16,1]  705 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 30.000,5
[transcode] A: bytes per frame  | 2940 (2940.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[transcode] V: video buffer     | 10 @ 640x480 [0x2]
[transcode] A: audio buffer     | 10 @ 44100x1x16
[import_raw.so] v0.3.3 (2008-11-23) (video) RGB/YUV | (audio) PCM
[import_ffmpeg.so] v0.1.15 (2008-01-28) (video) ffmpeg: MS MPEG4v1-3/MPEG4/MJPEG
[filter_stabilize.so] v0.61 (2009-10-25) extracts relative transformations of 
    subsequent frames (used for stabilization together with the
    transform filter in a second pass)
[filter_stabilize.so] Image Stabilization Settings:
[filter_stabilize.so]       maxshift = 40
[filter_stabilize.so]       stepsize = 2
[filter_stabilize.so]       allowmax = 1
[filter_stabilize.so]           algo = 1
[filter_stabilize.so]       fieldnum = 20
[filter_stabilize.so]      fieldsize = 32
[filter_stabilize.so]    mincontrast = 0.150000
[filter_stabilize.so]           show = 0
[filter_stabilize.so]         result = MVI_7727.AVI.trf
[filter_stabilize.so] field setup: row 1 with 6 fields
[filter_stabilize.so] field setup: row 2 with 7 fields
[filter_stabilize.so] field setup: row 3 with 6 fields
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[import_raw.so] tcextract -x pcm -i "./Videos/MVI_7727.AVI" -d 0 | tcextract -a 0 -x pcm -d 0 -t raw
[import_ffmpeg.so] input is mjpeg, reducing range from YUVJ420P to YUV420P
[filter_levels.so] instance #2
[filter_levels.so] v1.2.0 (2007-06-07) Luminosity level scaler
[filter_levels.so] scaling 0-255 gamma 1.000000 to 16-240 (pre-process)
Segmentation fault
henning@henning-Lenovo-G550:~$ 
```Running the code result in a new file named MVI_7727.AVI.trf but it is empty, 0 bytes,
and a Segmentation fault.
I use Ubuntu 11.04 Natty.
Any Ideas?
Henning

---

### Post by buddig on 2011-07-18
Now I have installed [Wine and VirtualDub with Deshaker Plugin]("http://forums.opensuse.org/english/information-new-users/unreviewed-how-faq/429428-howto-install-virtualdub-under-wine-deshaker-plugin.html") and it works fine.
It is the program, I used in Windows.
My last need for Windows is now solved in this way, and the Windows installation is deleted. :)
With all the things, I have read here in this forum, I thank you for great help 
 on my travel into the wonderfull Linux world. :)
Henning

---

