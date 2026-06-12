---
title: "Getting Vdpau to work with SMplayer"
date: 2012-10-11
forum: Multimedia Software
---

### Post by christopher.suttles on 2012-10-11
Just switched from Ubuntu to Xubuntu in order to ditch unity.

Loving how fast this is. All I have done since doing an entire clean install was updates, then installed the lastest nvidia driver from x-swat ppa (version 304.51 in nvidia x server settings). I also installed xubuntu-restricted-extras as well as any other programs I use.

Now, when trying to run a .mkv that is h.264 encoded with either smplayer, or mplayer from terminal, I get the same error no matter what I try.

Where did I go wrong?

Videos play fine using VX but take up about 50% of my core 2 duo.....:icon_frown:

[PHP]christopher@G51VX-XUBUNTU:~/Videos$ 
christopher@G51VX-XUBUNTU:~/Videos$ mplayer -vo vdpau -vc ffh264vdpau test.mkv
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.mkv.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[matroska,webm @ 0x7f4e398b3940]Unknown entry 0x437E
[matroska,webm @ 0x7f4e398b3940]Unknown entry 0x437E
[matroska,webm @ 0x7f4e398b3940]Unknown entry 0x437E
[matroska,webm @ 0x7f4e398b3940]Unknown entry 0x437E
[matroska,webm @ 0x7f4e398b3940]Unknown entry 0x437E
[matroska,webm @ 0x7f4e398b3940]Unknown entry 0x437E
[matroska,webm @ 0x7f4e398b3940]max_analyze_duration reached
[matroska,webm @ 0x7f4e398b3940]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0
[lavf] stream 2: subtitle (***), -sid 0
VIDEO:  [H264]  1280x720  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...


MPlayer interrupted by signal 11 in module: decode video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]
[/PHP]

---

### Post by pqwoerituytrueiwoq on 2012-10-12
[[img]http://www.zimagez.com/miniature/screenshot-10122012-053540pm.php[/img]](http://www.zimagez.com/zimage/screenshot-10122012-053540pm.php)

---

### Post by petran79 on 2013-02-09
there is another problem regarding VDPAU and videos encoded in P010 10-bit format.
videos encoded in 8-bit run without problems with vdpau.
Only when I switch video to XV or GL2 do 10-bit videos play. 
Is this normal? I'd like for them to use less CPU resources if possible.

Smplayer gives me the following error message when playing 10-bit files. is it because of the subtitles?
Only solution is to install Mplayer2 and SMplayer2 and disable the vdpau h264 acceleration option in the config 

 p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -lavdopts threads=2 -sub-fuzziness 1 -identify -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 60817459 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/petros/.config/smplayer/styles.ass -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -volume 100 -nocache -ss 86 -osdlevel 0 -noslices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 -lavdopts fast:skiploopfilter=all /media/any 10-bit file].mkv
 

 MPlayer SVN-r34707-4.6 (C) 2000-2012 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
 

 Playing /media/  any 10-bit file. mkv.
 libavformat version 54.0.0 (internal)
 libavformat file format detected.
 [matroska,webm @ 0xcac860]max_analyze_duration reached
 [matroska,webm @ 0xcac860]Estimating duration from bitrate, this may be inaccurate
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=33
 ID_CHAPTER_0_END=89920
 ID_CHAPTER_0_NAME=OP
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=89920
 ID_CHAPTER_1_END=658950
 ID_CHAPTER_1_NAME= A
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=658950
 ID_CHAPTER_2_END=1354930
 ID_CHAPTER_2_NAME=  B
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=1354930
 ID_CHAPTER_3_END=1444940
 ID_CHAPTER_3_NAME=ED
 ID_CHAPTER_ID=4
 ID_CHAPTER_4_START=1444940
 ID_CHAPTER_4_END=1449930
 ID_CHAPTER_4_NAME= 
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=jpn
 ID_AID_0_NAME= 
 [lavf] stream 1: audio (aac), -aid 0, -alang jpn, 
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME= 
 [lavf] stream 2: subtitle (ass), -sid 0, 
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME= 
 [lavf] stream 3: subtitle (ass), -sid 1,  
 VIDEO:  [H264]  1280x720  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Load subtitles in /media/ 
 ID_FILENAME=/media/ [ any 10-bit file ].mkv
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=1280
 ID_VIDEO_HEIGHT=720
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=1.7778
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=1449.93
 ID_SEEKABLE=1
 ID_CHAPTERS=5
 Opening video filter: [ass auto=1]
 Couldn't open video filter 'ass'.
 ASS: cannot add video filter
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 libavcodec version 54.0.0 (internal)
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=ffaac
 [Mixer] No hardware mixing, inserting volume filter.
 Starting playback...
 

 

 MPlayer interrupted by signal 11 in module: decode video
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.

---

### Post by BicyclerBoy on 2013-02-09
VDPAU does not support 10 bit video because the nVidia GPU h/w decoder does not support 10 bit video.

Higher bitrate/better encoding would be more usable than 10 bit..

---

