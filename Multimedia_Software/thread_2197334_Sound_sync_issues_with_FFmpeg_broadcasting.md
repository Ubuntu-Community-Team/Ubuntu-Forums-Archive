---
title: "Sound sync issues with FFmpeg broadcasting"
date: 2014-01-03
forum: Multimedia Software
---

### Post by Kranium31 on 2014-01-03
I'm broadcasting to justin.tv using a script i found here:

[https://gist.github.com/XenGi/7951805](https://gist.github.com/XenGi/7951805)

I'm having really bad sync issues where the video is ahead of the sound. Is there anything im missing here? I get no errors but it is eating a ton of bandwidth and im not really sure why.



this is the modified script i'm using:

[COLOR=#333333][FONT=Helvetica][php]INRES="640x360" # input resolution
OUTRES="640x360" # Output resolution
FPS="25" # target FPS
QUAL="fast" # one of the many FFMPEG presets in /usr/share/ffmpeg
SAMPLERATE="44100" # AAC: any, MP3: max 44.1 KHz
BITRATE="96k" # AAC: 160 kb/s, MP3: 128 kb/s
BUFFER="500k" # adjust if you have issues
ffmpeg \
-f x11grab -s "$INRES" -r "$FPS" -i :0.0+4,180 \
-f alsa -ac 2 -i pulse \
-vcodec libx264 -crf 18 -s "$OUTRES" -pix_fmt yuv420p -g 2 -minrate 1000k -maxrate 1000k -bufsize $BUFFER -b:v 1000k \
-acodec libfdk_aac -ar $SAMPLERATE -b:a $BITRATE -threads 0 -q:a 3 \
-f flv "rtmp://live.justin.tv/app/$STREAM_KEY"[/php]



Here is the last  output:

[/FONT][/COLOR][php]ffmpeg version git-2013-12-05-0538b29 Copyright (c) 2000-2013 the FFmpeg developers
  built on Dec  4 2013 20:16:21 with gcc 4.7 (Ubuntu/Linaro 4.7.2-2ubuntu1)
  configuration: --prefix=/home/htpc/ffmpeg_build --extra-cflags=-I/home/htpc/ffmpeg_build/include --extra-ldflags=-L/home/htpc/ffmpeg_build/lib --bindir=/home/htpc/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 56.100 / 52. 56.100
  libavcodec     55. 45.100 / 55. 45.100
  libavformat    55. 22.100 / 55. 22.100
  libavdevice    55.  5.102 / 55.  5.102
  libavfilter     3. 91.100 /  3. 91.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
[x11grab @ 0x2ba36e0] device: :0.0+4,180 -> display: :0.0 x: 4 y: 180 width: 640 height: 360
[x11grab @ 0x2ba36e0] shared memory extension found
Input #0, x11grab, from ':0.0+4,180':
  Duration: N/A, start: 1388718354.055571, bitrate: 184320 kb/s
    Stream #0:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 640x360, 184320 kb/s, 25 tbr, 1000k tbn, 25 tbc
Guessed Channel Layout for  Input Stream #1.0 : stereo
Input #1, alsa, from 'pulse':
  Duration: N/A, start: 1388718354.065704, bitrate: 1536 kb/s
    Stream #1:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
[swscaler @ 0x2b850c0] deprecated pixel format used, make sure you did set range correctly
[libx264 @ 0x2bf0e40] max bitrate less than average bitrate, assuming CBR
[libx264 @ 0x2bf0e40] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX
[libx264 @ 0x2bf0e40] profile High, level 3.0
[libx264 @ 0x2bf0e40] 264 - core 140 r2 1ca7bb9 - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=4 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=1 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=1 keyint=2 keyint_min=1 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=cbr mbtree=1 bitrate=96 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 vbv_maxrate=96 vbv_bufsize=512 nal_hrd=none filler=0 ip_ratio=1.40 aq=1:1.00
Output #0, flv, to 'rtmp://live.justin.tv/app/live_**************************':
  Metadata:
    encoder         : Lavf55.22.100
    Stream #0:0: Video: h264 (libx264) ([7][0][0][0] / 0x0007), yuv420p, 640x360, q=-1--1, 800 kb/s, 1k tbn, 25 tbc
    Stream #0:1: Audio: mp3 (libmp3lame) ([2][0][0][0] / 0x0002), 44100 Hz, stereo, s16p, 96 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> libx264)
  Stream #1:0 -> #0:1 (pcm_s16le -> libmp3lame)
Press [q] to stop, [?] for help
frame=   29 fps=0.0 q=0.0 size=       0kB time=00:00frame=   42 fps= 42 q=36.0 size=       5kB time=00:0


frame=619561 fps= 25 q=33.0 size= 3390481kB time=06:frame=619573 fps= 25 q=31.0 size= 3390549kB time=06:frame=619586 fps= 25 q=31.0 size= 3390627kB time=06:frame=619599 fps= 25 q=30.0 size= 3390691kB time=06:frame=619611 fps= 25 q=29.0 size= 3390758kB time=06:frame=619624 fps= 25 q=32.0 size= 3390831kB time=06:frame=619637 fps= 25 q=29.0 size= 3390901kB time=06:frame=619649 fps= 25 q=29.0 size= 3390964kB time=06:frame=619662 fps= 25 q=29.0 size= 3391033kB time=06:frame=619675 fps= 25 q=28.0 size= 3391094kB time=06:frame=619687 fps= 25 q=27.0 size= 3391161kB time=06:frame=619700 fps= 25 q=30.0 size= 3391243kB time=06:frame=619712 fps= 25 q=29.0 size= 3391312kB time=06:frame=619725 fps= 25 q=27.0 size= 3391379kB time=06:frame=619737 fps= 25 q=30.0 size= 3391444kB time=06:frame=619750 fps= 25 q=33.0 size= 3391519kB time=06:frame=619763 fps= 25 q=31.0 size= 3391590kB time=06:frame=619775 fps= 25 q=31.0 size= 3391655kB time=06:frame=619788 fps= 25 q=33.0 size= 3391729kB time=06:frame=619801 fps= 25 q=31.0 size= 3391795kB time=06:frame=619813 fps= 25 q=31.0 size= 3391860kB time=06:frame=619826 fps= 25 q=33.0 size= 3391937kB time=06:frame=619839 fps= 25 q=31.0 size= 3392003kB time=06:frame=619851 fps= 25 q=31.0 size= 3392068kB time=06:frame=619864 fps= 25 q=33.0 size= 3392143kB time=06:frame=619877 fps= 25 q=31.0 size= 3392210kB time=06:frame=619889 fps= 25 q=31.0 size= 3392277kB time=06:frame=619902 fps= 25 q=33.0 size= 3392353kB time=06:frame=619915 fps= 25 q=31.0 size= 3392421kB time=06:frame=619927 fps= 25 q=31.0 size= 3392487kB time=06:frame=619940 fps= 25 q=33.0 size= 3392564kB time=06:frame=619952 fps= 25 q=33.0 size= 3392630kB time=06:[flv @ 0x2eb4640] Failed to update header with correct duration.
[flv @ 0x2eb4640] Failed to update header with correct filesize.
frame=619953 fps= 25 q=-1.0 Lsize= 3392822kB time=06:53:24.33 bitrate=1120.5kbits/s    
video:3010293kB audio:352686kB subtitle:0 global headers:0kB muxing overhead 0.887410%
[libx264 @ 0x2eb4e40] frame I:311330 Avg QP:24.94  size:  8996
[libx264 @ 0x2eb4e40] frame P:308623 Avg QP:26.75  size:   913
[libx264 @ 0x2eb4e40] mb I  I16..4: 13.7% 69.0% 17.2%
[libx264 @ 0x2eb4e40] mb P  I16..4:  0.6%  1.5%  0.1%  P16..4: 19.5%  4.9%  1.8%  0.0%  0.0%    skip:71.6%
[libx264 @ 0x2eb4e40] 8x8 transform intra:69.0% inter:86.4%
[libx264 @ 0x2eb4e40] coded y,uvDC,uvAC intra: 54.4% 57.1% 22.8% inter: 4.9% 6.3% 0.0%
[libx264 @ 0x2eb4e40] i16 v,h,dc,p: 47% 24% 10% 19%
[libx264 @ 0x2eb4e40] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 33% 16% 20%  4%  5%  6%  5%  5%  6%
[libx264 @ 0x2eb4e40] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 34% 23% 10%  5%  7%  6%  6%  5%  4%
[libx264 @ 0x2eb4e40] i8c dc,h,v,p: 56% 16% 23%  5%
[libx264 @ 0x2eb4e40] Weighted P-Frames: Y:1.7% UV:0.8%
[libx264 @ 0x2eb4e40] kb/s:994.44[/php]
[COLOR=#333333][FONT=Helvetica]
[/FONT][/COLOR]

---

### Post by dannyboy79 on 2014-01-03
using crf is not suggested for livestreams due to the bitrate fluctuating so much and also i've never been able to get ffmpeg to keep the audio and video in sync. sometimes the stream would start in sync but after only a couple minutes the sync would be almost 15 seconds off. I use simplescreenrecorder to stream and it works awesome! I am actually working on a youtube video this weekend showing how I use ssr to record myself gaming and capturing the audio from the game and my voice from a microphone

---

### Post by FakeOutdoorsman on 2014-01-03
> **Kranium31 said:**
> I'm broadcasting to justin.tv using a script i found here:

[https://gist.github.com/XenGi/7951805](https://gist.github.com/XenGi/7951805)

These bad scripts and their variants have been spreading like a disease. The good thing is that you're using a recent, real build of ffmpeg.

Try something like this:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -framerate 25 -video_size 640x360 -i :0.0+4,180 -c:v libx264 -preset ultrafast -maxrate 774k -bufsize 1548k -pix_fmt yuv420p -c:a libmp3lame -b:a 96k -ar 44100 -f flv rtmp://live.justin.tv/app/<stream key>
```

Notice the usage of "-framerate" instead of "-r" for an input option for your x11grab device.

"-maxrate" and "-bufsize" being the options you'll want to mess around with other than "-framerate" and "-video_size". If you have a crappy upload rate like me then that is the limiting factor. You can use a site like speedtest.com if you do not know your network limitations. Assuming you have an upload rate of 1024kbit/s (1 megabit/s), and assuming you can reliably utilize 85% of that = 870kbit/s. Audio may consume ~96kbit/s leaving ~774 kbit/s for video. This is your "-maxrate". This is also the minimum download rate required for the viewer so they can watch without annoying buffering (other than the initial 1-5 seconds of buffering). This may be a better way of thinking about -maxrate if you are not limited by your upload rate.

bufsize / maxrate = latency in seconds. Typical lengths are 1-5 seconds. In the example above the value is 2 seconds: 774 x 2 = 1548. This is your "-bufsize".

Other things that might work:

[list]
[*]Try "-f pulse" instead of "-f alsa" since I'm guessing you're using PulseAudio as an input. To enable this output device you need to configure FFmpeg with --enable-libpulse.  I don't use PulseAudio so I've never tried it. See the [FFmpeg pulse input device docs](http://ffmpeg.org/ffmpeg-devices.html#pulse-1) and "pactl list sources" for a list of devices.

[*]Capture the audio and video with separate ffmpeg processes, mux, and output to RTMP.
[/list]

Please use the [code tags](http://ubuntuforums.org/misc.php?do=bbcode#code) to format your commands, scripts, and console outputs.

---

### Post by Kranium31 on 2014-01-06
> **FakeOutdoorsman said:**
> These bad scripts and their variants have been spreading like a disease. The good thing is that you're using a recent, real build of ffmpeg.

Try something like this:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -framerate 25 -video_size 640x360 -i :0.0+4,180 -c:v libx264 -preset ultrafast -maxrate 774k -bufsize 1548k -pix_fmt yuv420p -c:a libmp3lame -b:a 96k -ar 44100 -f flv rtmp://live.justin.tv/app/<stream key>
```

Notice the usage of "-framerate" instead of "-r" for an input option for your x11grab device.

"-maxrate" and "-bufsize" being the options you'll want to mess around with other than "-framerate" and "-video_size". If you have a crappy upload rate like me then that is the limiting factor. You can use a site like speedtest.com if you do not know your network limitations. Assuming you have an upload rate of 1024kbit/s (1 megabit/s), and assuming you can reliably utilize 85% of that = 870kbit/s. Audio may consume ~96kbit/s leaving ~774 kbit/s for video. This is your "-maxrate". This is also the minimum download rate required for the viewer so they can watch without annoying buffering (other than the initial 1-5 seconds of buffering). This may be a better way of thinking about -maxrate if you are not limited by your upload rate.

bufsize / maxrate = latency in seconds. Typical lengths are 1-5 seconds. In the example above the value is 2 seconds: 774 x 2 = 1548. This is your "-bufsize".

Other things that might work:

[LIST]
[*]Try "-f pulse" instead of "-f alsa" since I'm guessing you're using PulseAudio as an input. To enable this output device you need to configure FFmpeg with --enable-libpulse.  I don't use PulseAudio so I've never tried it. See the [FFmpeg pulse input device docs]("http://ffmpeg.org/ffmpeg-devices.html#pulse-1") and "pactl list sources" for a list of devices.
[*]Capture the audio and video with separate ffmpeg processes, mux, and output to RTMP.
[/LIST]

Please use the [code tags]("http://ubuntuforums.org/misc.php?do=bbcode#code") to format your commands, scripts, and console outputs.


Ok I will try all that next time I stream.  The only thing I don't understand is how to capture the audio and video separately and mux them together.  Hopefully these things will fix the sync issues and the out of control bandwidth.

I just upgraded to mint 16 so I will have to rebuild ffmpeg again before I can test.

---

