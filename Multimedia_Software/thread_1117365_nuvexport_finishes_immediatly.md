---
title: "nuvexport finishes immediatly"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Captain_Glen on 2009-04-05
Hi when I run nuvexport and try to convert to xvid it finishes immediately.

```
glen@glen-laptop:~$ nuvexport

Loading MythTV recording info.
60% 

Using ffmpeg for exporting.
What would you like to do?

  1. Export to XviD
  2. Export to SVCD
  3. Export to VCD
  4. Export to DVCD (VCD with 48kHz audio for making DVDs)
  5. Export to DVD
  6. Export to DivX
  7. Export to ASF
  8. Export to MP3
  9. Export to PSP (disabled)
 10. Export to MP4 (iPod)
 11. Export to .nuv and .sql

  q. Quit

Choose a function:  1

You have recorded the following shows:

  1. Dateline (1 episode)
  2. Landline (1 episode)
  3. The World Game (1 episode)

  q. Quit

Choose a show:  1

You have chosen to export 1 episode:

  1. Dateline
     (Sun Apr  5 05:30 AM) 720x576 MPEG2 (16:9)
     Mark Davis reports from strife-torn Madagascar as soldiers storm the
     presidential palace. And a report from Adrian Brown on a new electric car
     that could revolutionise China. Current affairs analysis program hosted by
     George Negus.

* Separate multiple episodes with spaces, or ranges with '-'

  c. Continue
  n. Choose another show
  q. Quit

Choose a function, or episode(s) to remove:  c
Where would you like to export the files to? [.] 
Enable Myth cutlist? [Yes] 
Enable noise reduction (slower, but better results)? [No] 
Enable deinterlacing? [Yes] 
Crop broadcast overscan border (0-5%) ? [1.5] 
Audio bitrate? [128] 
Variable bitrate video? [Yes] 
Multi-pass (slower, but better quality)? [Yes] 
Video bitrate? [768] 
Default resolution based on requested dimensions.
Width? [512] 
Height? [288] 

Now encoding:  Dateline:  Untitled
Encode started:  Mon Apr  6 11:59:37 2009
First pass...
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed:  0 of 63071 frames at 0 fps (~%, eta: unknown)  
ffmpeg finished.
processed:  0 of 63071 frames at 0 fps (~%, eta: unknown)  

ffmpeg died early.Please use the --debug option to figure out what went wrong.
http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode

Cleaning up temp files.
Cleaning up child processes.
glen@glen-laptop:~$ 

```

When I run it in debug mode and run each fork in a separate window I get:

```
glen@glen-laptop:~$ /usr/bin/nice -n19 ffmpeg -y -f s16le -ar 48000 -ac 2 -i /tmp/fifodir_12028/audout -f rawvideo -pix_fmt yuv420p -s 720x576 -aspect 1.77777777777778 -r 25.000 -i /tmp/fifodir_12028/vidout -aspect 1.77777777777778 -r 25.000 -deinterlace -croptop    8 -cropright 10 -cropbottom 8 -cropleft  10 -s 512x288  -vcodec libxvid -b '768k' -minrate '32' -maxrate '1536k' -bt '32k' -bufsize 65535 -flags +mv4+trell+loop -aic 1 -mbd 1 -cmp 2 -subcmp 2 -cgop 1 -b_qfactor '150' -b_qoffset '100' -bf '1' -pass 2 -passlogfile '/tmp/xvid.12028.log' -acodec libmp3lame -async 1  -ab '128k' -f avi './Dateline.avi' 2>&1
FFmpeg version SVN-r18333, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.24. 0 / 52.24. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr  5 2009 16:41:09, gcc: 4.3.2
Input #0, s16le, from '/tmp/fifodir_12028/audout':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Input #1, rawvideo, from '/tmp/fifodir_12028/vidout':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #1.0: Video: rawvideo, yuv420p, 720x576, 25 tbr, 25 tbn, 25 tbc
Unable to parse option value "trell+loop": undefined constant or missing (
Invalid value '+mv4+trell+loop' for option 'flags'
glen@glen-laptop:~$ 

```

and:

```
glen@glen-laptop:~$ mkdir -m 0755 /tmp/fifodir_12028/
glen@glen-laptop:~$ /usr/bin/nice -n19 /usr/bin/mythtranscode --showprogress -p '0' -c '1033' -s '2009-04-05T20:53:00' -f "/tmp/fifodir_12028/" --honorcutlist 2>&1
2009-04-06 12:02:31.466 Using runtime prefix = /usr
2009-04-06 12:02:31.492 Empty LocalHostName.
2009-04-06 12:02:31.518 New DB connection, total: 1
2009-04-06 12:02:31.532 Closing DB connection named 'DBManager0'
2009-04-06 12:02:31.539 Enabled verbose msgs: important
2009-04-06 12:02:31.547 New DB connection, total: 2
2009-04-06 12:02:31.606 Using protocol version 40
2009-04-06 12:02:42.598 Processed: 24 of 63071 frames(0 seconds)
2009-04-06 12:02:47.606 Processed: 398 of 63071 frames(15 seconds)
2009-04-06 12:02:52.613 Processed: 779 of 63071 frames(31 seconds)
2009-04-06 12:02:57.624 Processed: 1156 of 63071 frames(46 seconds)
2009-04-06 12:03:02.636 Processed: 1541 of 63071 frames(61 seconds)
2009-04-06 12:03:07.644 Processed: 1940 of 63071 frames(77 seconds)
2009-04-06 12:03:10.256 [mpeg2video @ 0xb7431764]ac-tex damaged at 41 13
2009-04-06 12:03:10.259 [mpeg2video @ 0xb7431764]Warning MVs not available
2009-04-06 12:03:12.740 Processed: 2271 of 63071 frames(90 seconds)
2009-04-06 12:03:17.747 Processed: 2636 of 63071 frames(105 seconds)
2009-04-06 12:03:22.750 Processed: 3047 of 63071 frames(121 seconds)
2009-04-06 12:03:27.759 Processed: 3474 of 63071 frames(138 seconds)
2009-04-06 12:03:31.571 mythtranscode: 6% Completed @ 64.0327 fps.
2009-04-06 12:03:32.765 Processed: 3910 of 63071 frames(156 seconds)
2009-04-06 12:03:37.775 Processed: 4352 of 63071 frames(174 seconds)
2009-04-06 12:03:42.780 Processed: 4778 of 63071 frames(191 seconds)
2009-04-06 12:03:47.781 Processed: 5190 of 63071 frames(207 seconds)
2009-04-06 12:03:51.580 mythtranscode: 8% Completed @ 69.3279 fps.
2009-04-06 12:03:52.785 Processed: 5604 of 63071 frames(224 seconds)
2009-04-06 12:03:57.788 Processed: 6005 of 63071 frames(240 seconds)
2009-04-06 12:04:02.798 Processed: 6409 of 63071 frames(256 seconds)
2009-04-06 12:04:07.806 Processed: 6830 of 63071 frames(273 seconds)
2009-04-06 12:04:11.600 mythtranscode: 11% Completed @ 71.57 fps.
2009-04-06 12:04:12.808 Processed: 7214 of 63071 frames(288 seconds)
2009-04-06 12:04:17.813 Processed: 7614 of 63071 frames(304 seconds)
2009-04-06 12:04:22.820 Processed: 8003 of 63071 frames(320 seconds)
2009-04-06 12:04:27.831 Processed: 8401 of 63071 frames(336 seconds)
2009-04-06 12:04:31.603 mythtranscode: 13% Completed @ 72.8119 fps.
2009-04-06 12:04:32.834 Processed: 8792 of 63071 frames(351 seconds)
2009-04-06 12:04:37.843 Processed: 9204 of 63071 frames(368 seconds)
2009-04-06 12:04:42.848 Processed: 9598 of 63071 frames(383 seconds)
2009-04-06 12:04:47.861 Processed: 9992 of 63071 frames(399 seconds)
2009-04-06 12:04:51.611 mythtranscode: 16% Completed @ 73.867 fps.
2009-04-06 12:04:52.869 Processed: 10404 of 63071 frames(416 seconds)
2009-04-06 12:04:57.870 Processed: 10820 of 63071 frames(432 seconds)
2009-04-06 12:05:02.874 Processed: 11276 of 63071 frames(451 seconds)
2009-04-06 12:05:07.877 Processed: 11819 of 63071 frames(472 seconds)
2009-04-06 12:05:11.619 mythtranscode: 19% Completed @ 76.7514 fps.
2009-04-06 12:05:12.879 Processed: 12378 of 63071 frames(495 seconds)
2009-04-06 12:05:17.898 Processed: 12941 of 63071 frames(517 seconds)
2009-04-06 12:05:22.912 Processed: 13500 of 63071 frames(540 seconds)
2009-04-06 12:05:27.918 Processed: 14075 of 63071 frames(563 seconds)
2009-04-06 12:05:31.635 mythtranscode: 22% Completed @ 80.6827 fps.
2009-04-06 12:05:32.922 Processed: 14616 of 63071 frames(584 seconds)
2009-04-06 12:05:37.929 Processed: 15059 of 63071 frames(602 seconds)
2009-04-06 12:05:42.936 Processed: 15345 of 63071 frames(613 seconds)
2009-04-06 12:05:44.082 [mpeg2video @ 0xb7431764]00 motion_type at 35 31
2009-04-06 12:05:44.096 [mpeg2video @ 0xb7431764]Warning MVs not available
2009-04-06 12:05:47.952 Processed: 15668 of 63071 frames(626 seconds)
2009-04-06 12:05:51.658 mythtranscode: 25% Completed @ 79.6628 fps.
2009-04-06 12:05:52.958 Processed: 15980 of 63071 frames(639 seconds)
2009-04-06 12:05:57.973 Processed: 16284 of 63071 frames(651 seconds)
2009-04-06 12:06:02.987 Processed: 16593 of 63071 frames(663 seconds)
2009-04-06 12:06:07.993 Processed: 16894 of 63071 frames(675 seconds)
2009-04-06 12:06:11.673 mythtranscode: 27% Completed @ 77.9163 fps.
2009-04-06 12:06:13.020 Processed: 17176 of 63071 frames(687 seconds)
2009-04-06 12:06:18.029 Processed: 17476 of 63071 frames(699 seconds)
2009-04-06 12:06:23.045 Processed: 17788 of 63071 frames(711 seconds)
2009-04-06 12:06:28.052 Processed: 18112 of 63071 frames(724 seconds)
2009-04-06 12:06:31.677 mythtranscode: 29% Completed @ 76.4485 fps.
2009-04-06 12:06:33.066 Processed: 18398 of 63071 frames(735 seconds)
2009-04-06 12:06:38.067 Processed: 18679 of 63071 frames(747 seconds)
2009-04-06 12:06:43.077 Processed: 19003 of 63071 frames(760 seconds)
2009-04-06 12:06:48.091 Processed: 19378 of 63071 frames(775 seconds)
2009-04-06 12:06:51.686 mythtranscode: 31% Completed @ 75.7409 fps.
2009-04-06 12:06:53.096 Processed: 19767 of 63071 frames(790 seconds)
2009-04-06 12:06:58.100 Processed: 20137 of 63071 frames(805 seconds)
2009-04-06 12:07:03.114 Processed: 20506 of 63071 frames(820 seconds)
2009-04-06 12:07:08.123 Processed: 20886 of 63071 frames(835 seconds)
2009-04-06 12:07:11.714 mythtranscode: 33% Completed @ 75.6982 fps.
2009-04-06 12:07:13.124 Processed: 21270 of 63071 frames(850 seconds)
2009-04-06 12:07:18.131 Processed: 21653 of 63071 frames(866 seconds)
2009-04-06 12:07:23.140 Processed: 22013 of 63071 frames(880 seconds)
2009-04-06 12:07:28.153 Processed: 22391 of 63071 frames(895 seconds)
2009-04-06 12:07:31.730 mythtranscode: 35% Completed @ 75.6376 fps.
2009-04-06 12:07:33.159 Processed: 22764 of 63071 frames(910 seconds)
2009-04-06 12:07:38.163 Processed: 23148 of 63071 frames(925 seconds)
2009-04-06 12:07:43.175 Processed: 23529 of 63071 frames(941 seconds)
2009-04-06 12:07:48.184 Processed: 23904 of 63071 frames(956 seconds)
2009-04-06 12:07:51.739 mythtranscode: 38% Completed @ 75.6675 fps.
2009-04-06 12:07:53.196 Processed: 24283 of 63071 frames(971 seconds)
2009-04-06 12:07:58.197 Processed: 24633 of 63071 frames(985 seconds)
2009-04-06 12:08:03.206 Processed: 25023 of 63071 frames(1000 seconds)
2009-04-06 12:08:08.223 Processed: 25408 of 63071 frames(1016 seconds)
2009-04-06 12:08:10.651 [mpeg2video @ 0xb7431764]invalid cbp at 43 8
2009-04-06 12:08:10.653 [mpeg2video @ 0xb7431764]Warning MVs not available
2009-04-06 12:08:11.754 mythtranscode: 40% Completed @ 75.5689 fps.
2009-04-06 12:08:13.228 Processed: 25774 of 63071 frames(1030 seconds)
2009-04-06 12:08:18.239 Processed: 26162 of 63071 frames(1046 seconds)
2009-04-06 12:08:21.670 [mpeg2video @ 0xb7431764]invalid cbp at 24 23
2009-04-06 12:08:23.247 Processed: 26542 of 63071 frames(1061 seconds)
2009-04-06 12:08:28.251 Processed: 26912 of 63071 frames(1076 seconds)
2009-04-06 12:08:31.757 mythtranscode: 43% Completed @ 75.5366 fps.
2009-04-06 12:08:33.253 Processed: 27276 of 63071 frames(1091 seconds)
2009-04-06 12:08:38.260 Processed: 27671 of 63071 frames(1106 seconds)
2009-04-06 12:08:38.797 [mpeg2video @ 0xb7431764]00 motion_type at 27 32
2009-04-06 12:08:43.272 Processed: 28042 of 63071 frames(1121 seconds)
2009-04-06 12:08:48.288 Processed: 28425 of 63071 frames(1137 seconds)
2009-04-06 12:08:51.771 mythtranscode: 45% Completed @ 75.5899 fps.
2009-04-06 12:08:53.296 Processed: 28808 of 63071 frames(1152 seconds)
2009-04-06 12:08:58.304 Processed: 29186 of 63071 frames(1167 seconds)
2009-04-06 12:09:03.318 Processed: 29568 of 63071 frames(1182 seconds)
2009-04-06 12:09:08.322 Processed: 29950 of 63071 frames(1198 seconds)
2009-04-06 12:09:11.775 mythtranscode: 47% Completed @ 75.6547 fps.
2009-04-06 12:09:13.327 Processed: 30359 of 63071 frames(1214 seconds)
2009-04-06 12:09:18.342 Processed: 30740 of 63071 frames(1229 seconds)
2009-04-06 12:09:23.344 Processed: 31107 of 63071 frames(1244 seconds)
2009-04-06 12:09:28.351 Processed: 31491 of 63071 frames(1259 seconds)
2009-04-06 12:09:31.781 mythtranscode: 50% Completed @ 75.6772 fps.
2009-04-06 12:09:33.364 Processed: 31866 of 63071 frames(1274 seconds)
2009-04-06 12:09:38.372 Processed: 32229 of 63071 frames(1289 seconds)
2009-04-06 12:09:43.381 Processed: 32589 of 63071 frames(1303 seconds)
2009-04-06 12:09:48.397 Processed: 32976 of 63071 frames(1319 seconds)
2009-04-06 12:09:51.792 mythtranscode: 52% Completed @ 75.5717 fps.
2009-04-06 12:09:53.406 Processed: 33343 of 63071 frames(1333 seconds)
2009-04-06 12:09:58.421 Processed: 33707 of 63071 frames(1348 seconds)
2009-04-06 12:10:03.426 Processed: 34078 of 63071 frames(1363 seconds)
2009-04-06 12:10:08.442 Processed: 34447 of 63071 frames(1377 seconds)
2009-04-06 12:10:11.805 mythtranscode: 55% Completed @ 75.5077 fps.
2009-04-06 12:10:13.445 Processed: 34834 of 63071 frames(1393 seconds)
2009-04-06 12:10:18.456 Processed: 35340 of 63071 frames(1413 seconds)
2009-04-06 12:10:23.458 Processed: 36078 of 63071 frames(1443 seconds)
2009-04-06 12:10:27.596 [mpeg2video @ 0xb7431764]skipped MB in I frame at 25 19
2009-04-06 12:10:28.466 Processed: 36805 of 63071 frames(1472 seconds)
2009-04-06 12:10:31.810 mythtranscode: 59% Completed @ 77.7018 fps.
2009-04-06 12:10:33.474 Processed: 37510 of 63071 frames(1500 seconds)
2009-04-06 12:10:38.475 Processed: 38245 of 63071 frames(1529 seconds)
2009-04-06 12:10:43.483 Processed: 38992 of 63071 frames(1559 seconds)
2009-04-06 12:10:48.486 Processed: 39745 of 63071 frames(1589 seconds)
2009-04-06 12:10:51.820 mythtranscode: 63% Completed @ 80.5378 fps.
2009-04-06 12:10:53.489 Processed: 40486 of 63071 frames(1619 seconds)
2009-04-06 12:10:58.491 Processed: 41216 of 63071 frames(1648 seconds)
2009-04-06 12:11:03.503 Processed: 41919 of 63071 frames(1676 seconds)
2009-04-06 12:11:08.510 Processed: 42627 of 63071 frames(1705 seconds)
2009-04-06 12:11:11.825 mythtranscode: 68% Completed @ 82.9293 fps.
2009-04-06 12:11:13.513 Processed: 43336 of 63071 frames(1733 seconds)
2009-04-06 12:11:18.520 Processed: 44081 of 63071 frames(1763 seconds)
2009-04-06 12:11:23.532 Processed: 44845 of 63071 frames(1793 seconds)
2009-04-06 12:11:25.597 [mpeg2video @ 0xb7431764]ac-tex damaged at 19 27
2009-04-06 12:11:28.547 Processed: 45573 of 63071 frames(1822 seconds)
2009-04-06 12:11:31.832 mythtranscode: 72% Completed @ 85.2987 fps.
2009-04-06 12:11:33.559 Processed: 46291 of 63071 frames(1851 seconds)
2009-04-06 12:11:38.566 Processed: 47027 of 63071 frames(1881 seconds)
2009-04-06 12:11:43.571 Processed: 47732 of 63071 frames(1909 seconds)
2009-04-06 12:11:48.577 Processed: 48442 of 63071 frames(1937 seconds)
2009-04-06 12:11:51.836 mythtranscode: 77% Completed @ 87.3867 fps.
2009-04-06 12:11:53.579 Processed: 49136 of 63071 frames(1965 seconds)
2009-04-06 12:11:58.586 Processed: 49863 of 63071 frames(1994 seconds)
2009-04-06 12:12:02.347 [mpeg2video @ 0xb7431764]ac-tex damaged at 43 29
2009-04-06 12:12:03.587 Processed: 50567 of 63071 frames(2022 seconds)
2009-04-06 12:12:08.589 Processed: 51292 of 63071 frames(2051 seconds)
2009-04-06 12:12:11.842 mythtranscode: 82% Completed @ 89.2389 fps.
2009-04-06 12:12:13.591 Processed: 51975 of 63071 frames(2079 seconds)
2009-04-06 12:12:18.596 Processed: 52653 of 63071 frames(2106 seconds)
2009-04-06 12:12:23.600 Processed: 53335 of 63071 frames(2133 seconds)
2009-04-06 12:12:28.603 Processed: 54059 of 63071 frames(2162 seconds)
2009-04-06 12:12:31.847 mythtranscode: 86% Completed @ 90.9809 fps.
2009-04-06 12:12:33.613 Processed: 54810 of 63071 frames(2192 seconds)
2009-04-06 12:12:38.618 Processed: 55507 of 63071 frames(2220 seconds)
2009-04-06 12:12:43.622 Processed: 56195 of 63071 frames(2247 seconds)
2009-04-06 12:12:48.626 Processed: 56915 of 63071 frames(2276 seconds)
2009-04-06 12:12:51.853 mythtranscode: 90% Completed @ 92.5943 fps.
2009-04-06 12:12:53.630 Processed: 57638 of 63071 frames(2305 seconds)
2009-04-06 12:12:58.636 Processed: 58365 of 63071 frames(2334 seconds)
2009-04-06 12:13:03.637 Processed: 59087 of 63071 frames(2363 seconds)
2009-04-06 12:13:08.644 Processed: 59824 of 63071 frames(2392 seconds)
2009-04-06 12:13:11.863 mythtranscode: 95% Completed @ 94.289 fps.
2009-04-06 12:13:13.647 Processed: 60609 of 63071 frames(2424 seconds)
2009-04-06 12:13:18.648 Processed: 61397 of 63071 frames(2455 seconds)
2009-04-06 12:13:23.651 Processed: 62258 of 63071 frames(2490 seconds)
2009-04-06 12:13:28.655 Processed: 62955 of 63071 frames(2518 seconds)
glen@glen-laptop:~$ 

```

I have the latest version of ffmpeg from the repository and am running Intrepid Ibex 8.10.

---

### Post by makkus on 2009-04-26
I have the same problem. Strange thing is: it worked for me for Intrepid. Stopped working after the Jaunty upgrade...

Anyone an idea?

---

### Post by Captain_Glen on 2009-04-26
I found a work around.  Just type ```
nuvexport --transcode
```

---

### Post by GuiGuy on 2009-04-26
> **Captain_Glen said:**
> I found a work around.  Just type ```
nuvexport --transcode
```

All you've done is use the mythtv's inbuilt transcoder instead of ffmpeg. 

nuvexport --mencoder will use mencoder.

mencoder and transcode are about 50% slower than ffmpeg given similar parameters. However, ffmpeg is said to yield lower quality.

[Check the wiki]("http://mythtv.org/wiki/Nuvexport#Transcode_Or_FFMpeg") for configuring nuvepxort.

[This page]("http://jankus.cz/offline/howto_auto_transcode_mythtv.html") is also useful. 

I note that 9.04 broke ffmpeg for xvid and divx transcoding. I find the solutions offered too complicated. I wasn't able to get them to work.

---

### Post by DirtDart on 2009-06-19
> **Captain_Glen said:**
> Hi when I run nuvexport and try to convert to xvid it finishes immediately.

```
Unable to parse option value "trell+loop": undefined constant or missing (
Invalid value '+mv4+trell+loop' for option 'flags'
glen@glen-laptop:~$ 

```


It is a bug, due to the changes version 0.5 of ffmpeg.

[http://svn.mythtv.org/trac/ticket/6214]("http://svn.mythtv.org/trac/ticket/6214")

---

### Post by greerd on 2009-06-21
That bug fixed worked for me, thanks a bunch for the link DirtDart.:popcorn:

Doug

---

### Post by malaTG on 2009-07-22
HI everyone,

I have done the fix as described but now I instead get this when running in debug mode

> /usr/bin/nice -n19 ffmpeg -threads 2 -y -f s16le -ar 48000 -ac 2 -f rawvideo -pix_fmt yuv420p -s 720x576 -aspect 1.33333333333333 -r 25.000 -i /tmp/fifodir_30477/vidout -aspect 1.33333333333333 -r 25.000 -deinterlace -croptop    12 -cropright 14 -cropbottom 12 -cropleft  14 -padtop 2 -padbottom 2 -s 720x540  -vcodec libxvid -b '900k' -minrate '32' -maxrate '1800k' -bt '32k' -bufsize 65535 -flags +mv4+loop+aic+cgop -trellis 1 -mbd 1 -cmp 2 -subcmp 2 -b_qfactor '150' -b_qoffset '100' -bf '1' -pass 1 -passlogfile '/tmp/xvid.30477.log' -f avi /dev/null 2>&1
[sudo] password for mala: 
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, rawvideo, from '/tmp/fifodir_30477/vidout':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: rawvideo, yuv420p, 720x576, 25 tbr, 25 tbn, 25 tbc
Output #0, avi, to '/dev/null':
    Stream #0.0: Video: libxvid (hq), yuv420p, 720x544 [PAR 136:135 DAR 4:3], q=2-31, pass 1, 900 kb/s, 90k tbn, 25 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[libxvid @ 0x82a34c0]error, non monotone timestamps -2147483648 >= -2147483648
av_interleaved_write_frame(): Error while opening file


Anyone got any ideas on how to fix this?

Thx in advance!

Mala

---

### Post by theonlyrealperson on 2009-07-24
> **malaTG said:**
> HI everyone,

I have done the fix as described but now I instead get this when running in debug mode



Anyone got any ideas on how to fix this?

Thx in advance!

Mala

You are using a version of ffmpeg that doesn't have the xvid codec compiled in.  

I'd switch to transcode or mencoder, like above, until they get ffmpeg sorted out.  

Personally, I only use mencoder.  It's slower, but I think it ends up a better quality.

If you notice in your command, it says "vcodec libxvid" - but if you look below at the version information it doesn't list xvid.  You likely installed (or kept, I have no idea how Ubuntu is doing things now) a stripped version of ffmpeg.

---

