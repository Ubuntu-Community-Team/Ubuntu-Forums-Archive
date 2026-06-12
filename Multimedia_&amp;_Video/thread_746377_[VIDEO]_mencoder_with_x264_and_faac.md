---
title: "[VIDEO] mencoder with x264 and faac"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by finalsayan on 2008-04-05
Hi everybody

I am trying to convert an avi file with mencoder using x264 and faac codecs for video and audio

by the way it crashes without messages that can help me

this is the output

```
finalsayan@finalsayan-laptop:~/Desktop/CONVERSIONE/mplayer$ ./mencoder ../Dragon\ Ball\ Z\ -\ 062\ -\ La\ Squadra\ Giniu\ In\ Azione.avi -oac faac -ovc x264 -x264encopts bitrate=300 pass=3 -o /home/finalsayan/Desktop/prova.mp4
MEncoder dev-SVN-r26325-4.1.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xae5d800
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  640x480  24bpp  25.000 fps  1067.5 kbps (130.3 kbyte/s)
[V] filefmt:3  fourcc:0x30355844  size:640x480  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================

Exiting...
```

probably the problem is with the faac codec, in fact if I leave faac and i put "copy" everything works

```
finalsayan@finalsayan-laptop:~/Desktop/CONVERSIONE/mplayer$ ./mencoder ../Dragon\ Ball\ Z\ -\ 062\ -\ La\ Squadra\ Giniu\ In\ Azione.avi -oac copy -ovc x264 -x264encopts bitrate=300 pass=3 -o /home/finalsayan/Desktop/prova.mp4
```

i am really blocked at this point :(
thank you

---

### Post by finalsayan on 2008-04-06
i have solved the problem with avidemux 2

it does the work without errors

bye

---

### Post by alphacrux on 2008-04-19
I second avidemux 2 its a great program with auto ipod settings. ffmpeg is just a bunch of problems this is alot easier. 

you can get the latest version [[COLOR="Blue"]here[/COLOR]]("http://www.getdeb.net/search.php?keywords=avidemux") (its a .deb, so its super easy to install)

the program is in the repositories but its the 2.3.0 version and ALOT of changes happen between it and the 2.4.1 current version, go to the link, the download and setup is automated anyways there.

---

