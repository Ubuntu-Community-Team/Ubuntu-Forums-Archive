---
title: "dvd::rip will not encode to h264"
date: 2010-12-30
forum: Multimedia Software
---

### Post by Oracle_The_Blind on 2010-12-30
Hi,

I am running Ubuntu 10.04 x64.

I have recently started ripping my DVDs to avi files using dvd::rip.
I was using ffmpeg's mpeg4 codec without any problems, but after reading that the h264 provides better quality for a given file size, I decided to try it.

However, when I try to encode using h264, I get the following error:

> Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/james/dvdrip-data/singingInTheRain/tmp' && cd /home/james/dvdrip-data/singingInTheRain/tmp && mkdir -p /home/james/dvdrip-data/singingInTheRain/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob,null -i \/home\/james\/dvdrip\-data\/singingInTheRain\/vob\/001\/ -w 3042,50 -F h264 -b 192,0,2 -s 3.475 --a52_drc_off -f 25.000 --export_par 106,100 -R 1 -y ffmpeg,null -o /dev/null --progress_meter 2 --progress_rate 25 --avi_limit 9999 && cp x264_2pass.log divx4.log && echo EXECFLOW_OK

Output: transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[[34;1mtranscode[0m] V: auto-probing     | /home/james/dvdrip-data/singingInTheRain/vob/001/ (OK)
[[34;1mtranscode[0m] V: import format    | MPEG 2 program stream in  (module=vob)
[[34;1mtranscode[0m] A: auto-probing     | /home/james/dvdrip-data/singingInTheRain/vob/001/ (OK)
[[34;1mtranscode[0m] A: import format    | AC3 in  (module=null)
[[34;1mtranscode[0m] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[[34;1mtranscode[0m] V: import frame     | 720x576  1.25:1  encoded @ 4:3
[[34;1mtranscode[0m] V: bits/pixel       | 0.293
[[34;1mtranscode[0m] V: decoding fps,frc | 25.000,0
[[34;1mtranscode[0m] V: multi-pass       | (mode=1) writing data (pass 1) to divx4.log
[[34;1mtranscode[0m] V: video format     | YUV420 (4:2:0) aka I420
[[34;1mtranscode[0m] A: import format    | 0x2000  AC3          [48000,16,4]  192 kbps
[[34;1mtranscode[0m] A: downmix          | 4 channels -> 2 channels
[[34;1mtranscode[0m] A: export           | disabled
[[34;1mtranscode[0m] V: encoding fps,frc | 25.000,3
[[34;1mtranscode[0m] A: bytes per frame  | 7680 (7680.000000)
[[34;1mtranscode[0m] A: adjustment       | 0@1000
[[34;1mtranscode[0m] A: rescale stream   | 3.475
[[34;1mtranscode[0m] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[[34;1mtranscode[0m] V: video buffer     | 10 @ 720x576 [0x2]
[[34;1mtranscode[0m] A: audio buffer     | 10 @ 48000x2x16
[[34;1mimport_null.so[0m] v0.2.0 (2002-01-19) (video) null | (audio) null
[[34;1mimport_vob.so[0m] v0.6.1 (2006-05-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[[34;1mexport_null.so[0m] v0.1.2 (2001-08-17) (video) null | (audio) null
[[34;1mexport_ffmpeg.so[0m] v0.3.18 (2008-11-29) (video) Lavc52.20.0 | (audio) MPEG/AC3/PCM
[[34;1mimport_vob.so[0m] tccat -i "/home/james/dvdrip-data/singingInTheRain/vob/001/" -t vob -d 0 -S 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yuv420p
[[34;1mexport_ffmpeg.so[0m] Using FFMPEG codec 'h264' (FourCC 'h264', H264 (avc)).
[[34;1mexport_ffmpeg.so[0m] No profile selected
[[31;1mexport_ffmpeg.so[0m][33;1m warning[0m: Error opening configuration file ./ffmpeg.cfg: No such file or directory
[[34;1mexport_ffmpeg.so[0m] Starting 1 thread(s)
[[34;1mdecode_mpeg2.c[0m] libmpeg2 acceleration: none (plain C)
[libx264 @ 0x2504d20]broken ffmpeg default settings detected
[libx264 @ 0x2504d20]use an encoding preset (vpre)
[[31;1mexport_ffmpeg.so[0m][33;1m warning[0m: could not open FFMPEG codec
[[31;1mencoder.c[0m][33;1m warning[0m: video export module error: init failed
[[31;1mtranscode[0m][31;1m critical[0m: failed to init encoder
[[31;1mdecode_mpeg2.c[0m][31;1m critical[0m: failed to write Y data of frame (len=65536)
[[31;1mextract_mpeg2.c[0m][31;1m critical[0m: error while writing output data: Broken pipe
[[31;1mdemuxer.c[0m][31;1m critical[0m: write program stream packet: Broken pipe
[[31;1miodir.c[0m][33;1m warning[0m: left out 2 directory entries

--------------------------------------------------------------------------------


All DVDs will consistently rip successfully on mpeg4, but will consistently fail on h264.
As far as I know I installed the required packages for h264, but I may have missed a vital one.

Any help with tracking down this error will be much appreciated.

---

### Post by cchhrriiss121212 on 2010-12-30
You could try Handbrake, that will determine whether it is a library issue or not.

---

### Post by Oracle_The_Blind on 2010-12-30
Ha! Well, it turns out that it does encode to h264 with HandBreak!
Would you suggest that I just continue to use handbreak as my converter?

Ideally, it would be nice to get dvd::rip to work, as I know how to use it properly. 
A lot of the advanced settings in HandBreak look rather confusing:
"Subpel ME & Mode", "Trellis", "Adaptive B-Frames"... hu?


edit: I take that back, the descriptions in handbreak for each of the options is fantastic. I think I'll stick with it. :D

---

### Post by cchhrriiss121212 on 2010-12-30
Yeah Handbrake has worked nicely for me in the last year or so. These are the only settings I change from default:
Switch to MKV container
Use "High profile" setting

Like this, the rips look indistinguishable from source DVD and still take up the same space as an AVI rip (~700MB for a movie).

---

### Post by kgarbutt on 2010-12-30
I recently wanted to rip some dvd movies to watch on my android. I used handbrake to successfully do it, and I used h264 format so, yes, keep using handbrake.

---

### Post by Oracle_The_Blind on 2010-12-31
> **cchhrriiss121212 said:**
> Yeah Handbrake has worked nicely for me in the last year or so. These are the only settings I change from default:
Switch to MKV container
Use "High profile" setting

Like this, the rips look indistinguishable from source DVD and still take up the same space as an AVI rip (~700MB for a movie).
Great, thanks.
Though, what's the practical difference between using mkv rather than mp4?

---

### Post by cchhrriiss121212 on 2010-12-31
> Though, what's the practical difference between using mkv rather than mp4?
Practically speaking: MKV is a little smaller and looks better, MP4 is compatible with Apple devices.

I have not done extensive testing, just did a few rips of a 30min TV show. The MP4 rips were around 350MB with small defects, and the MKVs were around 250MB and looked fine. I'm sure others will have different experiences though.

---

### Post by JohnAStebbins on 2010-12-31
> **cchhrriiss121212 said:**
> Practically speaking: MKV is a little smaller and looks better, MP4 is compatible with Apple devices.

I have not done extensive testing, just did a few rips of a 30min TV show. The MP4 rips were around 350MB with small defects, and the MKVs were around 250MB and looked fine. I'm sure others will have different experiences though.

mp4 and mkv are containers and should have no effect on video quality, all other things being equal.  You probably didn't use equivalent encoder codec settings when producing the files you compared.

The advantages of mkv are support for more codec and subtitle formats (e.g. theora video, dts audio and dvd subtitles). The advantage of mp4 is that it is supported by more devices and players than mkv.

---

### Post by cchhrriiss121212 on 2011-01-01
> You probably didn't use equivalent encoder codec settings when producing the files you compared.

Yes, I think that is likely, I am just going from memory. The one thing I am sure of is that the default settings gave disappointing results.

---

### Post by bertram_wooster on 2011-06-14
It seems to be related to how ffmpeg and x264 are distributed on ubuntu. Please see this bug report (it is a closed bug report as it is not considered a bug):

[https://bugs.launchpad.net/ubuntu/+source/transcode/+bug/276519](https://bugs.launchpad.net/ubuntu/+source/transcode/+bug/276519)

I thought I had compiled ffmpeg and x264 from source -- see this how to here: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

But I still seem to have problems, so maybe I haven't been able to link x264 properly. I tried on 10.04.

If anyone does manage to get this working on dvdrip then please post, as I would be interested to know. Otherwise follow the advice above and use handbrake.

---

### Post by mdavies5 on 2011-11-22
I am new to ripping. ogmrip and dvd:rip both worked fine jsut once using H264. They then refused to do any more. dvd:rip gave the same mesage as oracle_the_blind reported. ogmrip worked again after a reboot. 
I am now trying handbrake as recommended. Done one successful rip and the second has started ok so keeping my fingers crossed. It seems more likely it is an underlying fault with Ubuntu or LInux..

---

### Post by metacell on 2012-03-24
I'm also using Ubuntu 10.04 LTS x64 and DVD::RIP, and get the following error:

```
Job 'Omkodar video - titel nr. 3, kapitel nr. 1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/jonas/dvdrip-data/Pirates_of_Dark_Water/tmp' && cd /home/jonas/dvdrip-data/Pirates_of_Dark_Water/tmp && mkdir -p /home/jonas/dvdrip-data/Pirates_of_Dark_Water/avi/003 && execflow -n 19 transcode -H 10 -a 0 -T 3,1,1 -x dvd -i \/home\/jonas\/Video\/Pirates_of_Dark_Water\/PIRATES_OF_DARK_WATER_DISC_1 -w 3107,50 -F h264 -b 128,0,2 --a52_drc_off -f 30,4 -M 2 --export_par 88,100 -R 1 -y ffmpeg,null -o /dev/null --progress_meter 2 --progress_rate 25 && cp x264_2pass.log divx4.log && echo EXECFLOW_OK

Output: rror (0): Broken pipe
[[31;1mseqinfo.c[0m][33;1m warning[0m: syncinfo write error (0): Broken pipe
```
(the last line is repeated over and over)

I tried to download, compile and package the latest ffmpeg using [these instructions]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289"), but same result.

**EDIT**: Switched to Handbrake, and it worked like a charm. Very easy to use program.

---

