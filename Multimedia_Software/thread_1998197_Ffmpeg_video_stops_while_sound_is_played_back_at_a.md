---
title: "Ffmpeg: video stops while sound is played back at a normal speed"
date: 2012-06-06
forum: Multimedia Software
---

### Post by Smiletastic on 2012-06-06
Hello ' Ubuntu breeders',
 I  installed ffmpeg ([ttps://ffmpeg.org/trac/ffmpeg/wiki/Ubuntu]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")[h]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")[CompilationGuide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")). The installation process was successful.
 I tried to record desktop video using either “*[COLOR=#6b0094][SIZE=2]ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 output.mkv” or [/SIZE][/COLOR]**[COLOR=#004a4a][SIZE=4]**“**[/SIZE][/COLOR]**[COLOR=#004a4a][SIZE=4]ffmpeg[/SIZE][/COLOR]**[COLOR=#004a4a][SIZE=4] -f alsa -i pulse -f x11grab -r 30 -s 1366x768 [/SIZE][/COLOR]**[COLOR=#004a4a][SIZE=4]**-i :0.0 -vcodec libx264 -preset ultrafast -threads 4 -y -sameq test.mkv”**[/SIZE][/COLOR]*
 When I try to play back my video the video goes too fast and stops in a few seconds while the sound is played at a normal speed with a motionless picture as a background.
 

 That's what one can see in terminal:
 

 r@r-P4M800-M7:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 output.mkv 
 ffmpeg version git-2012-06-06-c8a1101 Copyright (c) 2000-2012 the FFmpeg developers 
   built on Jun  6 2012 13:04:33 with gcc 4.6.3 
   configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab 
   libavutil      51. 56.100 / 51. 56.100 
   libavcodec     54. 25.100 / 54. 25.100 
   libavformat    54.  6.101 / 54.  6.101 
   libavdevice    54.  0.100 / 54.  0.100 
   libavfilter     2. 78.100 /  2. 78.100 
   libswscale      2.  1.100 /  2.  1.100 
   libswresample   0. 15.100 /  0. 15.100 
   libpostproc    52.  0.100 / 52.  0.100 
 [alsa @ 0x9c3e460] Estimating duration from bitrate, this may be inaccurate 
 Guessed Channel Layout for  Input Stream #0.0 : stereo 
 Input #0, alsa, from 'pulse': 
   Duration: N/A, start: 1338987570.710593, bitrate: 1536 kb/s 
     Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s 
 [x11grab @ 0x9c38960] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768 
 [x11grab @ 0x9c38960] shared memory extension found 
 [x11grab @ 0x9c38960] Estimating duration from bitrate, this may be inaccurate 
 Input #1, x11grab, from ':0.0': 
   Duration: N/A, start: 1338987570.766082, bitrate: 1007124 kb/s 
     Stream #1:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1366x768, 1007124 kb/s, 30 tbr, 1000k tbn, 30 tbc 
 [buffer @ 0x9c38600] w:1366 h:768 pixfmt:bgr0 tb:1/30 sar:0/1 sws_param:flags=2 
 [ffmpeg_buffersink @ 0x9c41840] No opaque field provided 
 [format @ 0x9c41880] auto-inserting filter 'auto-inserted scaler 0' between the filter 'Parsed_null_0' and the filter 'format' 
 [buffer @ 0x9c38600] TB:0.033333 
 [auto-inserted scaler 0 @ 0x9c430a0] w:1366 h:768 fmt:bgr0 sar:0/1 -> w:1366 h:768 fmt:yuv420p sar:0/1 flags:0x4 
 [libx264 @ 0x9c36720] using cpu capabilities: MMX2 SSE2 SSE3 Cache64 
 [libx264 @ 0x9c36720] profile High 4:4:4 Predictive, level 3.2, 4:2:0 8-bit 
 [libx264 @ 0x9c36720] 264 - core 125 r2200 999b753 - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0 
 Output #0, matroska, to 'output.mkv': 
   Metadata: 
     encoder         : Lavf54.6.101 
     Stream #0:0: Video: h264, yuv420p, 1366x768, q=-1--1, 1k tbn, 30 tbc 
     Stream #0:1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s 
 Stream mapping: 
   Stream #1:0 -> #0:0 (rawvideo -> libx264) 
   Stream #0:0 -> #0:1 (pcm_s16le -> pcm_s16le) 
 Press [q] to stop, [?] for help 
 frame=    3 fps=0.0 q=0.0 size=     737kB time=00:00:00.06 bitrate=90064.2kbits/frame=    5 fps=4.2 q=0.0 size=     929kB time=00:00:00.13 bitrate=57196.8kbits/frame=    7 fps=4.1 q=0.0 size=     961kB time=00:00:00.20 bitrate=39346.6kbits/frame=    9 fps=4.0 q=0.0 size=    1185kB time=00:00:00.26 bitrate=36345.8kbits/frame=   11 fps=4.0 q=0.0 size=    1249kB time=00:00:00.33 bitrate=30716.5kbits/frame=   13 fps=3.0 q=0.0 size=    1377kB time=00:00:00.40 bitrate=28193.0kbits/frame=   15 fps=3.0 q=0.0 size=    1409kB time=00:00:00.46 bitrate=24709.5kbits/frame=   17 fps=3.1 q=0.0 size=    1729kB time=00:00:00.53 bitrate=26568.0kbits/frame=   20 fps=3.2 q=0.0 size=    1889kB time=00:00:00.63 bitrate=24441.5kbits/frame=   23 fps=3.4 q=0.0 size=    2049kB time=00:00:00.73 bitrate=22895.2kbits/frame=   26 fps=3.5 q=0.0 size=    2177kB time=00:00:00.83 bitrate=21405.5kbits/frame=   29 fps=3.6 q=0.0 size=    2241kB time=00:00:00.93 bitrate=19673.2kbits/frame=   32 fps=3.7 q=0.0 size=    2369kB time=00:00:01.03 bitrate=18783.8kbits/frame=   35 fps=3.8 q=0.0 size=    2465kB time=00:00:01.13 bitrate=17820.0kbits/frame=   38 fps=3.9 q=0.0 size=    2561kB time=00:00:01.23 bitrate=17012.6kbits/frame=   41 fps=3.9 q=0.0 size=    2657kB time=00:00:01.33 bitrate=16326.3kbits/frame=   44 fps=4.0 q=0.0 size=    2753kB time=00:00:01.43 bitrate=15735.8kbits/frame=   47 fps=4.0 q=0.0 size=    2849kB time=00:00:01.53 bitrate=15222.3kbits/frame=   50 fps=4.1 q=0.0 size=    2945kB time=00:00:01.63 bitrate=14771.7kbits/frame=   53 fps=4.1 q=0.0 size=    3009kB time=00:00:01.73 bitrate=14221.9kbits/frame=   56 fps=4.2 q=0.0 size=    3105kB time=00:00:01.83 bitrate=13875.0kbits/frame=   59 fps=3.9 q=0.0 size=    3201kB time=00:00:01.93 bitrate=13564.1kbits/frame=   61 fps=3.9 q=0.0 size=    3233kB time=00:00:02.00 bitrate=13240.8kbits/frame=   64 fps=3.9 q=0.0 size=    3361kB time=00:00:02.10 bitrate=13109.6kbits/frame=   67 fps=3.9 q=0.0 size=    3425kB time=00:00:02.20 bitrate=12752.0kbits/frame=   70 fps=4.0 q=0.0 size=    3521kB time=00:00:02.30 bitrate=12539.5kbits/frame=   73 fps=4.0 q=0.0 size=    3585kB time=00:00:02.40 bitrate=12235.5kbits/frame=   76 fps=4.0 q=0.0 Lsize=    6786kB time=00:00:02.53 bitrate=21946.9kbits/s     
 video:3192kB audio:3497kB global headers:0kB muxing overhead 1.447683% 
 [libx264 @ 0x9c36720] frame I:1     Avg QP: 0.00  size:566742 
 [libx264 @ 0x9c36720] frame P:75    Avg QP: 0.00  size: 36017 
 [libx264 @ 0x9c36720] mb I  I16..4: 100.0%  0.0%  0.0% 
 [libx264 @ 0x9c36720] mb P  I16..4:  9.8%  0.0%  0.0%  P16..4:  1.4%  0.0%  0.0%  0.0%  0.0%    skip:88.8% 
 [libx264 @ 0x9c36720] coded y,uvDC,uvAC intra: 39.2% 48.4% 48.3% inter: 0.7% 1.5% 1.5% 
 [libx264 @ 0x9c36720] i16 v,h,dc,p: 79% 21%  0%  0% 
 [libx264 @ 0x9c36720] i8c dc,h,v,p: 54% 14% 31%  2% 
 [libx264 @ 0x9c36720] kb/s:10320.09 
 r@r-P4M800-M7:~$ clear 
  
 r@r-P4M800-M7:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 output.mkv 
 ffmpeg version git-2012-06-06-c8a1101 Copyright (c) 2000-2012 the FFmpeg developers 
   built on Jun  6 2012 13:04:33 with gcc 4.6.3 
   configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab 
   libavutil      51. 56.100 / 51. 56.100 
   libavcodec     54. 25.100 / 54. 25.100 
   libavformat    54.  6.101 / 54.  6.101 
   libavdevice    54.  0.100 / 54.  0.100 
   libavfilter     2. 78.100 /  2. 78.100 
   libswscale      2.  1.100 /  2.  1.100 
   libswresample   0. 15.100 /  0. 15.100 
   libpostproc    52.  0.100 / 52.  0.100 
 [alsa @ 0xb347460] Estimating duration from bitrate, this may be inaccurate 
 Guessed Channel Layout for  Input Stream #0.0 : stereo 
 Input #0, alsa, from 'pulse': 
   Duration: N/A, start: 1338987612.749067, bitrate: 1536 kb/s 
     Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s 
 [x11grab @ 0xb341960] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768 
 [x11grab @ 0xb341960] shared memory extension found 
 [x11grab @ 0xb341960] Estimating duration from bitrate, this may be inaccurate 
 Input #1, x11grab, from ':0.0': 
   Duration: N/A, start: 1338987612.804761, bitrate: 1007124 kb/s 
     Stream #1:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1366x768, 1007124 kb/s, 30 tbr, 1000k tbn, 30 tbc 
 File 'output.mkv' already exists. Overwrite ? [y/N]  
 

 Of course I print 'y' and 'Enter'
  In Ubuntu 11.10 it worked fine after installing ffmpeg : [ttps://ffmpeg.org/trac/ffmpeg/wiki/Ubuntu]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")[h]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")[CompilationGuide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")
 I did the same with 12.04 but it, as I have already said, doesn't work.  
 

 Can anyone help me out?

---

### Post by FakeOutdoorsman on 2012-06-06
Don't use *-sameq*. It doesn't mean "same quality" and shouldn't ever be used with x264. Also, commands and console outputs are easier to read with the [noparse]```
[/noparse] tags.

What player are you using? Does it work as expected with ffplay?
[code]ffplay output.mkv
```

---

### Post by Smiletastic on 2012-06-06
Thank you, FakeOutdoorsman.
But I've some questions:
1) What exactly should I write to record  desktop video via ffplay?
2) How to install ffplay media player or is it autamatically installed with ffmpeg? 
3) What command should I use to play my videos via ffplay?
Thanks for the reply.

---

### Post by FakeOutdoorsman on 2012-06-06
> **Smiletastic said:**
> 1) What exactly should I write to record  desktop video via ffplay?
ffplay is just a simple player, not something you can record with. FFplay is often used to test outputs files, but I often use it as my main media player.

> **Smiletastic said:**
> 2) How to install ffplay media player or is it autamatically installed with ffmpeg?
It should be automatically installed.

> **Smiletastic said:**
> 3) What command should I use to play my videos via ffplay?
```
ffplay the_actual_name_of_the_file_you_want_to_play.mp4
```

---

### Post by Smiletastic on 2012-06-07
Thanks a lot FakeOutdoorsman, ffplay works better than other players.  But, unfortunately, I can't make screencasting yet.
Does anybody have any "magic pills" to solve the problem?
Thanks in advance.

---

