---
title: "Transcode error in dvd::rip"
date: 2010-07-23
forum: Multimedia Software
---

### Post by botot on 2010-07-23
Hi all,

I am generally pretty new to Ubuntu and am trying to rip a dvd into .avi file using dvd::rip. I have no problem ripping the title, but the transcode doesn't run normally... I kept on having the error msg pasted at the end of this post. I don't understand why libdvdread reports that it cannot find device name, and not sure how to correct for that, or whether that's even the core of the problem or not.

Thanks very much!

Error message:
```

Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/wjlee/dvdrip-data/A10010_new/tmp' && cd /home/wjlee/dvdrip-data/A10010_new/tmp && mkdir -p /home/wjlee/dvdrip-data/A10010_new/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/wjlee\/dvdrip\-data\/A10010_new\/vob\/001\/ -w 2435,50 -b 384,0,2 -s 1.102 --a52_drc_off -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -f 30,4 -M 2 -Y 4,2,4,6 -B 1,11,8 -R 1 -y xvid,null --psu_mode --nav_seek /home/wjlee/dvdrip-data/A10010_new/tmp/A10010_new-001-nav.log --no_split  -o /dev/null --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK

Output: transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[[34;1mtranscode[0m] V: auto-probing     | /home/wjlee/dvdrip-data/A10010_new/vob/001/ (OK)
[[34;1mtranscode[0m] V: import format    | MPEG 2 program stream in  (module=vob)
[[34;1mtranscode[0m] A: auto-probing     | /home/wjlee/dvdrip-data/A10010_new/vob/001/ (OK)
[[34;1mtranscode[0m] A: import format    | LPCM in  (module=vob)
[[34;1mtranscode[0m] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[[34;1mtranscode[0m] V: import frame     | 720x480  1.50:1  encoded @ 4:3
[[34;1mtranscode[0m] V: new aspect ratio | 632x472  1.34:1 (-B)
[[34;1mtranscode[0m] V: clip frame (->)  | 624x464
[[34;1mtranscode[0m] V: bits/pixel       | 0.281
[[34;1mtranscode[0m] V: decoding fps,frc | 29.970,4
[[34;1mtranscode[0m] V: multi-pass       | (mode=1) writing data (pass 1) to divx4.log
[[34;1mtranscode[0m] V: video format     | YUV420 (4:2:0) aka I420
[[34;1mtranscode[0m] A: import format    | 0x10001 LPCM         [48000,16,2] 1536 kbps
[[34;1mtranscode[0m] A: export           | disabled
[[34;1mtranscode[0m] V: encoding fps,frc | 29.970,4
[[34;1mtranscode[0m] A: bytes per frame  | 6408 (6406.400000)
[[34;1mtranscode[0m] A: adjustment       | -1600@1000
[[34;1mtranscode[0m] A: rescale stream   | 1.102
[[34;1mtranscode[0m] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[[34;1mtranscode[0m] V: video buffer     | 10 @ 720x480 [0x2]
[[34;1mtranscode[0m] A: audio buffer     | 10 @ 48000x2x16
[[34;1mimport_vob.so[0m] v0.6.1 (2006-05-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[[34;1mfilter_smartyuv.so[0m] options=threshold=10:Blend=1:diffmode=2:highq=1
[[34;1mfilter_smartyuv.so[0m] (MMX) 0.1.6 (2007-05-31) Motion-adaptive deinterlacing
[[34;1mexport_null.so[0m] v0.1.2 (2001-08-17) (video) null | (audio) null
[[34;1mexport_xvid4.so[0m] v0.0.6 (2007-08-11) (video) XviD 1.0.x series (aka API 4.0) | (audio) MPEG/AC3/PCM
[[31;1mexport_xvid4.so[0m][33;1m warning[0m: Error opening configuration file ./xvid4.cfg: No such file or directory
[[34;1msplit.c[0m] reading auto-split information from file "/home/wjlee/dvdrip-data/A10010_new/tmp/A10010_new-001-nav.log"
[[34;1msplit.c[0m] done reading 98055 entries
[split.c] chunk 0/0 PU=0 (-L 0 -c 15-30) mapped onto (-L 9285 -c 1-16)
[[34;1mimport_vob.so[0m] tccat -i "/home/wjlee/dvdrip-data/A10010_new/vob/001/" -t vob -d 0 -S 9285 | tcdemux -M 2 -a 0 -x pcm -S 0,0-17 -d 0 | tcextract -t vob -a 0 -x pcm -d 0
[[34;1mimport_vob.so[0m] tccat -i "/home/wjlee/dvdrip-data/A10010_new/vob/001/" -t vob -d 0 -S 9285 | tcdemux -s 0xa0 -x mpeg2 -S 0,0-17 -M 2 -f 29.970030 -P /tmp/fileOJwsYf   -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yuv420p
[demuxer.c] seeking to sequence 0:0 ...
[demuxer.c] seeking to sequence 0:0 ...
[[31;1miodir.c[0m][33;1m warning[0m: left out 2 directory entries
[[34;1mdecode_mpeg2.c[0m] libmpeg2 acceleration: none (plain C)
[[31;1miodir.c[0m][33;1m warning[0m: left out 2 directory entries
Segmentation fault
[[31;1mdecode_mpeg2.c[0m][31;1m critical[0m: failed to write Y data of frame (len=0)
[[31;1mextract_mpeg2.c[0m][31;1m critical[0m: error while writing output data: Broken pipe

--------------------------------------------------------------------------------

```

---

### Post by botot on 2010-07-23
Hi,

I was able to pass the conifguration part. Not sure why but I save the default setting of Xvid when I click on the Configuration botton in the Transcode menu. But I still cannot get through the last part of the error message (pasted as follows). I think most of the operations seem ok in the beginning, but there is a problem "write Y data of frame" and "... Broken pipe". I am not sure what the problem is right now. Anybody has come through the problem or know the solution of this will be very appreciated! Thanks very much!!

```

Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/wjlee/dvdrip-data/A10010_new/tmp' && cd /home/wjlee/dvdrip-data/A10010_new/tmp && mkdir -p /home/wjlee/dvdrip-data/A10010_new/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/wjlee\/dvdrip\-data\/A10010_new\/vob\/001\/ -w 2435,50 -b 384,0,2 -s 1.102 --a52_drc_off -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -f 30,4 -M 2 -Y 4,2,4,6 -B 1,11,8 -R 1 -y xvid,null --psu_mode --nav_seek /home/wjlee/dvdrip-data/A10010_new/tmp/A10010_new-001-nav.log --no_split  -o /dev/null --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK

Output: transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[[34;1mtranscode[0m] V: auto-probing     | /home/wjlee/dvdrip-data/A10010_new/vob/001/ (OK)
[[34;1mtranscode[0m] V: import format    | MPEG 2 program stream in  (module=vob)
[[34;1mtranscode[0m] A: auto-probing     | /home/wjlee/dvdrip-data/A10010_new/vob/001/ (OK)
[[34;1mtranscode[0m] A: import format    | LPCM in  (module=vob)
[[34;1mtranscode[0m] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[[34;1mtranscode[0m] V: import frame     | 720x480  1.50:1  encoded @ 4:3
[[34;1mtranscode[0m] V: new aspect ratio | 632x472  1.34:1 (-B)
[[34;1mtranscode[0m] V: clip frame (->)  | 624x464
[[34;1mtranscode[0m] V: bits/pixel       | 0.281
[[34;1mtranscode[0m] V: decoding fps,frc | 29.970,4
[[34;1mtranscode[0m] V: multi-pass       | (mode=1) writing data (pass 1) to divx4.log
[[34;1mtranscode[0m] V: video format     | YUV420 (4:2:0) aka I420
[[34;1mtranscode[0m] A: import format    | 0x10001 LPCM         [48000,16,2] 1536 kbps
[[34;1mtranscode[0m] A: export           | disabled
[[34;1mtranscode[0m] V: encoding fps,frc | 29.970,4
[[34;1mtranscode[0m] A: bytes per frame  | 6408 (6406.400000)
[[34;1mtranscode[0m] A: adjustment       | -1600@1000
[[34;1mtranscode[0m] A: rescale stream   | 1.102
[[34;1mtranscode[0m] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[[34;1mtranscode[0m] V: video buffer     | 10 @ 720x480 [0x2]
[[34;1mtranscode[0m] A: audio buffer     | 10 @ 48000x2x16
[[34;1mimport_vob.so[0m] v0.6.1 (2006-05-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[[34;1mfilter_smartyuv.so[0m] options=threshold=10:Blend=1:diffmode=2:highq=1
[[34;1mfilter_smartyuv.so[0m] (MMX) 0.1.6 (2007-05-31) Motion-adaptive deinterlacing
[[34;1mexport_null.so[0m] v0.1.2 (2001-08-17) (video) null | (audio) null
[[34;1mexport_xvid4.so[0m] v0.0.6 (2007-08-11) (video) XviD 1.0.x series (aka API 4.0) | (audio) MPEG/AC3/PCM
[[34;1msplit.c[0m] reading auto-split information from file "/home/wjlee/dvdrip-data/A10010_new/tmp/A10010_new-001-nav.log"
[[34;1msplit.c[0m] done reading 98055 entries
[split.c] chunk 0/0 PU=0 (-L 0 -c 15-30) mapped onto (-L 9285 -c 1-16)
[[34;1mimport_vob.so[0m] tccat -i "/home/wjlee/dvdrip-data/A10010_new/vob/001/" -t vob -d 0 -S 9285 | tcdemux -M 2 -a 0 -x pcm -S 0,0-17 -d 0 | tcextract -t vob -a 0 -x pcm -d 0
[[34;1mimport_vob.so[0m] tccat -i "/home/wjlee/dvdrip-data/A10010_new/vob/001/" -t vob -d 0 -S 9285 | tcdemux -s 0xa0 -x mpeg2 -S 0,0-17 -M 2 -f 29.970030 -P /tmp/fileJKLvYG   -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yuv420p
[demuxer.c] seeking to sequence 0:0 ...
[[34;1mdecode_mpeg2.c[0m] libmpeg2 acceleration: none (plain C)
[B][[31;1miodir.c[0m][33;1m warning[0m: left out 2 directory entries
[demuxer.c] seeking to sequence 0:0 ...
[[31;1miodir.c[0m][33;1m warning[0m: left out 2 directory entries
Segmentation fault
[[31;1mdecode_mpeg2.c[0m][31;1m critical[0m: failed to write Y data of frame (len=65536)
[[31;1mextract_mpeg2.c[0m][31;1m critical[0m: error while writing output data: Broken pipe[/B]

--------------------------------------------------------------------------------

```

---

