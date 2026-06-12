---
title: "nuvexport dramatics"
date: 2009-10-25
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-25
Using a clean install of mythbuntu 9.10 - I had nuvexport working with mencoder. I'd like to use ffmpeg for xvid but it doesn't do that anymore :(

Then two days ago, after an update, I think, nuvexport/mencoder started this with every file processed:

> 
Waiting for mythtranscode to set up the fifos.
Starting mencoder.
processed:  38312 of 39161 frames (97.83%), 25.13 fps 
mythtranscode finished.
processed:  39114 of 39161 frames (99.88%), 25.09 fps 

mythtranscode died early.Please use the --debug option to figure out what went wrong.
[http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode](http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode)


As you can see it doesn't quite finish the job and exits. That means I can't batch process. 

I've tried the --debug option and then executing the commands.
> 
mkdir -m 0755 /tmp/fifodir_10768/


completes
The second command
> 
/usr/bin/nice -n19 /usr/bin/mythtranscode --showprogress -p '0' -c '1002' -s '2009-10-24T22:10:00' -f "/tmp/fifodir_10768/" --honorcutlist 2>&1


seems to hang at this point:

> 
2009-10-26 08:32:21.861 Using runtime prefix = /usr
2009-10-26 08:32:21.862 Using configuration directory = /home/guiguy/.mythtv
2009-10-26 08:32:21.862 Empty LocalHostName.
2009-10-26 08:32:21.877 New DB connection, total: 1
2009-10-26 08:32:21.896 Closing DB connection named 'DBManager0'
2009-10-26 08:32:21.896 Enabled verbose msgs: important
2009-10-26 08:32:21.923 New DB connection, total: 2
2009-10-26 08:32:22.004 Using protocol version 50


 Essentially I now cannot archive any recording since ffmpeg and transcode won't do xvid etc. Unless there is a more practical way to archive recordings?

Can any one help?

Thanks

---

### Post by carwinz on 2009-11-01
The second command seems to set up pipes for the third command, so I believe this is expected behaviour (Notice how the output from using the --debug option says "forking").

That said, when I execute the third command (while the second is still running), I get:

> /usr/bin/nice -n19 transcode -V --print_status 16 --import_asr 3 --export_asr 3 --export_fps 25.000,3 -Z 160x96 -k -i /tmp/fifodir_8774/vidout -p /tmp/fifodir_8774/audout -H 0 -x raw -g 704x576 -f 25.000,3 -n 0x1 -e 48000,16,2 -j 8,10,8,10 -J smartyuv -J yuvdenoise=mode=2  -y xvid,null  -N 0x55 -b 128,0,2,0 -R 1,/tmp/xvid.8774.log -w 100  -o /dev/null 2>&1
[transcode] critical: bad argument for -V/--video_format, should be one of: yuv420p (default), yuv422p, rgb24

However, if I set the -V argument to yuv420p and remove the "--print_status 16" then it starts processing.... still waiting to see if it turns out ok.

**Edit: ** It completed and created the output file as expected, but there were some audio warnings and NO audio in the exported file. Output was:

> transcode v1.1.4 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 704x576  1.22:1  encoded @ 16:9
[transcode] V: clip frame (<-)  | 684x560
[transcode] V: zoom             | 160x096  1.67:1 (Lanczos3)
[transcode] V: rgb2bgr          | yes
[transcode] V: bits/pixel       | 0.260
[transcode] V: decoding fps,frc | 25.000,3
[transcode] V: multi-pass       | (mode=2) reading data (pass2) from /tmp/xvid.8774.log
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x1     PCM          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG ES Layer 3 [48000,16,2]  128 kbps
[transcode] V: export format    | unknown (module dependant)
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 sse2 sse 3dnowext 3dnow mmxext mmx cmove asm 
[transcode] V: video buffer     | 10 @ 704x576 [0x2]
[transcode] A: audio buffer     | 10 @ 48000x2x16
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import_raw.so] v0.3.3 (2008-11-23) (video) RGB/YUV | (audio) PCM
[filter_smartyuv.so] (MMX) 0.1.6 (2007-05-31) Motion-adaptive deinterlacing
[filter_yuvdenoise.so] Using extended MMX SIMD optimisations.
[filter_yuvdenoise.so] v0.2.1 (2003-11-26) mjpegs YUV denoiser
[export_xvid4.so] v0.0.6 (2007-08-11) (video) XviD 1.0.x series (aka API 4.0) | (audio) MPEG/AC3/PCM
[import_raw.so] tcextract -i "/tmp/fifodir_8774/vidout" -d 0 -x yuv420p | tcextract -a 0 -x yuv420p -d 0
[export_xvid4.so] warning: Error opening configuration file ./xvid4.cfg: No such file or directory
[extract_yuv.c] warning: no file type specified, assuming (RAW stream)
[transcode] Audio: using lame-3.98.2
[export_xvid4.so] warning: Usage of this module for audio encoding is deprecated.
[export_xvid4.so] warning: Consider switch to export_tcaud module.
[encoder.c] Delaying audio
[decoder.c] cancelling the import threads 0:00:16,  ( 8| 0|12) 

[transcode] encoded 422 frames (0 dropped, 0 cloned), clip length  16.88 s

---

### Post by carwinz on 2009-11-09
Got mine working for xvid4

Made the following edits to /usr/share/nuvexport/export/transcode.pm

[LIST]
[*] Remove ".' -V'" from line 87 (no longer an option in transcode)
[*] Remove ".' --print_status 16'" from line 88 (no longer an option in transcode)
[*] Remove "$transcode .= ' -k';" from line 223 (this was making faces have a bluish tinge)
[*] Change ".' -H 0 -x raw'" on line 243 to ".' -H 0 -x raw,raw'" so that the audio input is processed
[/LIST]

---

