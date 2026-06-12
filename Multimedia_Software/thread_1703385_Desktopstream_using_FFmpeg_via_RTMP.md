---
title: "Desktopstream using FFmpeg via RTMP"
date: 2011-03-09
forum: Multimedia Software
---

### Post by theDominik on 2011-03-09
Couldn't find anything via google or forum search.

[LIST]
[*]Browser: Chomium 11.0.692.0 (77027)
[*]OS: Ubuntu 10.10 Meerkat (GNOME 2.32.0)
[*]Connection: 20mbit down, 1mbit up
[/LIST]

I try to stream my desktop/ingame using FFmpeg.
I found a short script which works for the guy who made it (he uses gentoo btw):

~/.bashrc (JustIn.tv)
```
justin() {
INRES="1680x1050" # input resolution
OUTRES="1280x800"
FPS="20" # target FPS
QUAL="fast"  # one of the many FFMPEG preset
STREAM_KEY="live_XXXXXX"

ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0 \
 -f alsa -ac 2 -i pulse -vcodec libx264 -vpre "$QUAL" -s "$OUTRES" \
 -acodec libmp3lame -ab 128k -threads 0  \
 -f flv "rtmp://live.justin.tv/app/$STREAM_KEY flashver=FMLE/3.0\20(compatible;\20FMSc/1.0)"  
}
```

I get the following error:
```
dominik@Dome-desktop:~$ justin
FFmpeg version git-f4f4e12, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar  7 2011 13:13:40 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.113. 2 / 52.113. 2
  libavformat  52.102. 0 / 52.102. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[x11grab @ 0x26385f0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1680 height: 1050
[x11grab @ 0x26385f0] shared memory extension  found
[x11grab @ 0x26385f0] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1299674293.408971, bitrate: 1128960 kb/s
    Stream #0.0: Video: rawvideo, bgra, 1680x1050, 1128960 kb/s, 20 tbr, 1000k tbn, 20 tbc
[alsa @ 0x2645fa0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x2645fa0] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'pulse':
  Duration: N/A, start: 1299674293.438054, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Server error: Authentication Failed.
rtmp://live.justin.tv/app/live_XXXXX flashver=FMLE/3.0\20(compatible;\20FMSc/1.0): Input/output error

```


I also tried UStream.tv:
```
ustream() {
INRES="1680x1050" # input resolution
OUTRES="1280x800"
FPS="20" # target FPS
QUAL="fast"  # one of the many FFMPEG preset


URL="rtmp://1.6216020.fme.ustream.tv/ustreamVideo/XXXXXX/XXXXXX flashver=FMLE/3.0\20(compatible;\20FMSc/1.0)"


ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0 \
 -f alsa -ac 2 -i pulse -vcodec libx264 -vpre "$QUAL" -s "$OUTRES" \
 -acodec libmp3lame -ab 128k -threads 0  \
 -f flv "$URL"
 }
```


Error:
```
dominik@Dome-desktop:~$ ustream
FFmpeg version git-f4f4e12, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar  7 2011 13:13:40 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.113. 2 / 52.113. 2
  libavformat  52.102. 0 / 52.102. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[x11grab @ 0x18315f0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1680 height: 1050
[x11grab @ 0x18315f0] shared memory extension  found
[x11grab @ 0x18315f0] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1299674352.431517, bitrate: 1128960 kb/s
    Stream #0.0: Video: rawvideo, bgra, 1680x1050, 1128960 kb/s, 20 tbr, 1000k tbn, 20 tbc
[alsa @ 0x183efa0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x183efa0] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'pulse':
  Duration: N/A, start: 1299674352.461347, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
rtmp://1.6216020.fme.ustream.tv/ustreamVideo/XXXXXX/XXXXXX flashver=FMLE/3.0\20(compatible;\20FMSc/1.0): Input/output error

```

This error is bothering me, but I have no clue whats wrong. I'm an linux newbe.
```
flashver=FMLE/3.0\20(compatible;\20FMSc/1.0): Input/output error
```


Things I know/have tried:
[LIST]
[*]I know the stream key is correct. ("Authentification failed" in first error should not occure.)
[*]I don't use a firewall or sth. similar.
[*]I forwarded port 1935 (default RTMP port) to my local address. (even if it's not needed)
[*]I recompiled "ffmpeg" and "x264" and reinstalled them.
[/LIST]


Maybe this helps, console output when it's working:
```
[alsa @ 0x64eec0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x64eec0] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'pulse':
  Duration: N/A, start: 1299526006.804731, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[buffer @ 0x697ac0] w:1280 h:1024 pixfmt:bgra
[scale @ 0x6b5530] w:1280 h:1024 fmt:bgra -> w:640 h:512 fmt:yuv420p flags:0xa0000004
[libx264 @ 0x6757b0] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x6757b0] profile High, level 2.2
[libx264 @ 0x6757b0] 264 - core 114 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=12 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=abr mbtree=1 bitrate=200 ratetol=1.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.41 aq=1:1.00
Output #0, flv, to 'rtmp://live.justin.tv/app/live_xxxxxxxxxxxxx flashver=FMLE/3.0\20(compatible;\20FMSc/1.0)':
  Metadata:
    encoder         : Lavf52.84.0
    Stream #0.0: Video: libx264, yuv420p, 640x512, q=10-51, 200 kb/s, 1k tbn, 15 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Press [q] to stop encoding
frame=   78 fps= 13 q=-1.0 Lsize=     170kB time=3.74 bitrate= 373.1kbits/s dup=0 drop=14    op=10    
video:108kB audio:58kB global headers:0kB muxing overhead 2.487676%
frame I:1     Avg QP:28.18  size: 32406
CTRL-c
```

I appreciate every helpful information.

Thanks :)

Crosslink: The game forum where I found the script and what I try: [http://forums.heroesofnewerth.com/showthread.php?t=229469](http://forums.heroesofnewerth.com/showthread.php?t=229469)

---

### Post by theDominik on 2011-03-13
Bump.

---

### Post by theDominik on 2011-03-19
Bump.

---

### Post by theDominik on 2011-03-24
Bump.

---

### Post by jelofson on 2012-03-29
Having the same issue here with ffmpeg. No idea why. If I output to file, it works but as soon as I try rtmp, input/output error.

---

### Post by SAKeeler on 2012-04-09
I'm fighting with a similar issue, this may help you,
comment out or remove this bit
```
flashver=FMLE/3.0\20(compatible;\20FMSc/1.0)"
```

should stop the auth errors.

my issue is that everything seems to go smoothly, but when I check the stream on my Justin.tv page, I get no video.  Just black space.  I'm still
tinkering and will cross link my post later, as well as my progress.

best of luck.  Let me know if you get it working.

---

