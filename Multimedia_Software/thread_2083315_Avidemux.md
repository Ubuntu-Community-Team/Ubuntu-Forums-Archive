---
title: "Avidemux"
date: 2012-11-12
forum: Multimedia Software
---

### Post by eslavko on 2012-11-12
Hello...

I tried to capture some tv show from my DVB-T receiver. The kaffeine does work's nicely.
But the recorded file is m2t type and with a lot of commercials.
So I try AviDemux 2.6.0 (r8273) in my ubuntu 12.04. 
The cutting works nice. Well if I don't forget to align all cut's in I frame. But it's ok.
The problem is that I have standalone DVD/Player/recorder capable to play divx. But I can't produce the right one with avidemux. Is it possible at all?
the unit is  LG RH265.

For now I can produce playable file only with mencorder with that settings:
mencoder test.m2t -o test.avi -ovc lavc -oac mp3lame -ffourcc DX50

Is it possible to make same output with Avidemux to avoid double conversion?

Thanks.

p.s.
It's really question for avidemux forum but I can't register as no new registration is accepted.

---

### Post by BicyclerBoy on 2012-11-12
Your recorded files are mpeg2-ts transport stream..

Lots of programs call DivX Xvid by the real name mpeg4/layer2 or mpeg4-visual or ASP &/or leave off the layer2 or -asp (just to add confusion).

So mpeg4/layer10 is H264AVC (H264)
mpeg4-visual is mpeg4/2 is mpeg4-asp is DivX Xvid etc (MPEG4).
(likely avidemux labels)

---

### Post by eslavko on 2012-11-13
Well I know that naming scheme for divx is al little mess.
And my DVD recorder is a little bit picky. I tried a lot of variant made with different programs but only that made with mencoder are digestible for them.
But I tryed just short examples. Yesterday I try to convert bigger file but mencoder give me a error.

```
1 duplicate frame(s)!
Pos: 184.9s   8413f (10%) 71.76fps Trem:  16min 448mb  A-V:-0.042 [1911:243]

1 duplicate frame(s)!
Pos: 185.2s   8423f (10%) 71.75fps Trem:  16min 448mb  A-V:-0.042 [1911:243]

1 duplicate frame(s)!
Pos: 185.3s   8431f (10%) 71.74fps Trem:  16min 448mb  A-V:-0.038 [1912:243]

Too many audio packets in the buffer: (4096 in 2359296 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16384:9004.
Setting audio delay to 0.024s.

Video stream: 1912.263 kbit/s  (239032 B/s)  size: 44302348 bytes  185.340 secs  8431 frames

Audio stream:  243.901 kbit/s  (30487 B/s)  size: 5666304 bytes  185.856 secs

```

so actually I have no solution how to prepare video for my player.
The only way working is to make DVD disc. But it's space inefficient. 
HELP..

Slavko

---

### Post by BicyclerBoy on 2012-11-13
I don't ever use AVI file container & avoid XVid etc..
I use MythTV & generate a cutlist & cut the original HD h264 files & play them on a HTPC.

There could be multiple problems..
1. AVI container with advanced video codecs (any MPEG4) is a ugly hack because the container does not support out of order frames.
So there are multiple hacks like packed B-frames etc 
Basically .avi is obsolete.

2. Discovering the player requirements..
- for the container
- for the DivX codec (& the audio codec)

3.AviDeMUX 2.5 does not work with mpeg4/10 h264/avc..you must have mpeg2 video over dvb-t
The latest AviDeMux 2.6 purports to work h264.

Does your TV or DVD/BD player support DLNA?

---

### Post by eslavko on 2012-11-14
I think I'm loocked to avi due player restriction.

Is it there some example files for different containers and codecs to easy test if player works on that

DLNA what is?

---

### Post by eslavko on 2012-11-14
Now I know little more.
I can transcode video in windows version of avidemux.

Under linux there are no xvid available for video.

The resulting video stream that works on my player (as is reported in Mediainfo) made with Avidemux 2.6.0 windows) is:
8711 Kbps, 720*576 (5:4), at 25 fps, MPEG-4 Visual (DivX 4) (PAL) (Advanced Simple@L4) (BVOP2)

And closest possible made in ubuntu with Avidemux 2.6.0 (r8273) is :
1531 Kbps, 720*576 (5:4), at 25 fps, MPEG-4 Visual (DivX 4) (PAL) (Advanced Simple@L1) (BVOP2)

So the difference is in @L1 vs @L4. Audio works as MP3 or AC3.
(Windows version had xvid in dropdown menu)

Really want to leave windoze....

Any solution?

---

### Post by BicyclerBoy on 2012-11-14
There was some discussion about the DivX encoder on the avidemux.org forums in the linux or experimental 2.6 section..
[http://avidemux.org/smuf/index.php/topic,11546.0.html](http://avidemux.org/smuf/index.php/topic,11546.0.html)

[http://avidemux.org/smuf/index.php/topic,11402.0.html](http://avidemux.org/smuf/index.php/topic,11402.0.html)
That thread is rambling & confusing..

Your info suggests there is a DivX encoder but has the wrong/different configuration. The bitrates are very different.

A DVD is allowed 10Mbps for sum of all streams.

---

### Post by eslavko on 2012-11-14
I tryed many bitrates.. from 1000 to 8000kbps with same results. Over 8000 motion come jerky and audio distorted.

---

### Post by BicyclerBoy on 2012-11-15
If latest avidemux has broken the Xvid encode then just use the old 2.5 version.. 

Or use it to cut the video file & leave the video as mpeg2video..
Then convert with mencoder or ffmpeg (real one not avconv)

ffmpeg -i input.mpg -c:a libmp3lame -c:v mpeg4 -mbd rd -vtag xvid -flags +ilme+ildct+mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 out.avi

I just made this cmd up..could need some work..

---

### Post by eslavko on 2012-11-15
I tried few options but still not get usable result. 

and command fail...
```

slavko@ePodstresnik:~/DVB_RECORDS$ ffmpeg -i minuta.mp4 -c:a libmp3lame -c:v mpeg4 -mbd rd -vtag xvid -flags +ilme+ildct+mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 out.avi
ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x20019a0] multiple edit list entries, a/v desync might occur, patch welcome
    Last message repeated 1 times
Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 50.00 (50/1)
    Last message repeated 1 times
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'minuta.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf54.29.104
  Duration: 00:01:00.17, start: 0.129000, bitrate: 1726 kb/s
    Stream #0.0(und): Video: h264 (Main), yuv420p, 720x576 [PAR 12:11 DAR 15:11], 1530 kb/s, 25.02 fps, 50 tbr, 50k tbn, 50 tbc
    Stream #0.1(und): Audio: mp2, 48000 Hz, 2 channels, s16, 192 kb/s
Unrecognized option 'c:a'
Failed to set value 'libmp3lame' for option 'c:a'
slavko@ePodstresnik:~/DVB_RECORDS$ 

```

The options I managed to make readable file is:

```

mencoder test.m2t -o out003.avi -ovc lavc -oac mp3lame -ffourcc DX50

```
or 

```

ffmpeg -i test.m2t -f avi -b 2500k -vcodec msmpeg4 out008.avi

```

But the problems with both is that works for short files. On longer ones both output errors

Mencoder:
```


snip snip


1 duplicate frame(s)!
Pos: 114.7s   5215f (12%) 175.55fps Trem:   3min 112mb  A-V:-0.041 [814:242]

1 duplicate frame(s)!
Pos: 114.9s   5225f (12%) 175.51fps Trem:   3min 112mb  A-V:-0.041 [814:242]

1 duplicate frame(s)!
Pos: 115.1s   5235f (13%) 175.54fps Trem:   3min 112mb  A-V:-0.041 [814:242]

1 duplicate frame(s)!
Pos: 115.3s   5245f (13%) 175.56fps Trem:   3min 112mb  A-V:-0.041 [814:242]

1 duplicate frame(s)!
Pos: 115.6s   5255f (13%) 175.55fps Trem:   3min 112mb  A-V:-0.041 [814:242]

1 duplicate frame(s)!
Pos: 115.8s   5265f (13%) 175.54fps Trem:   3min 112mb  A-V:-0.041 [813:242]

1 duplicate frame(s)!
Pos: 116.0s   5275f (13%) 175.54fps Trem:   3min 111mb  A-V:-0.041 [813:242]

1 duplicate frame(s)!
Pos: 116.2s   5285f (13%) 175.62fps Trem:   3min 112mb  A-V:-0.041 [813:242]

1 duplicate frame(s)!
Pos: 116.4s   5295f (13%) 175.54fps Trem:   3min 112mb  A-V:-0.041 [817:242]

1 duplicate frame(s)!
Pos: 116.7s   5305f (13%) 175.46fps Trem:   3min 112mb  A-V:-0.041 [818:243]

1 duplicate frame(s)!
Pos: 116.9s   5315f (13%) 175.37fps Trem:   3min 112mb  A-V:-0.041 [819:243]

1 duplicate frame(s)!
Pos: 117.1s   5325f (13%) 175.26fps Trem:   3min 112mb  A-V:-0.041 [821:243]

1 duplicate frame(s)!
Pos: 117.3s   5335f (13%) 175.19fps Trem:   3min 112mb  A-V:-0.041 [822:243]

1 duplicate frame(s)!
Pos: 117.5s   5345f (13%) 175.18fps Trem:   3min 112mb  A-V:-0.041 [823:243]

1 duplicate frame(s)!
Pos: 117.8s   5355f (13%) 175.14fps Trem:   3min 112mb  A-V:-0.041 [824:243]

1 duplicate frame(s)!
Pos: 118.0s   5365f (13%) 175.04fps Trem:   3min 112mb  A-V:-0.041 [825:243]

1 duplicate frame(s)!
Pos: 118.2s   5375f (13%) 175.01fps Trem:   3min 112mb  A-V:-0.041 [825:243]

1 duplicate frame(s)!
Pos: 118.4s   5385f (13%) 175.02fps Trem:   3min 112mb  A-V:-0.041 [824:243]

1 duplicate frame(s)!
Pos: 118.6s   5395f (13%) 174.99fps Trem:   3min 112mb  A-V:-0.041 [823:243]

1 duplicate frame(s)!
Pos: 118.9s   5405f (13%) 175.02fps Trem:   3min 112mb  A-V:-0.041 [823:243]

1 duplicate frame(s)!
Pos: 119.1s   5415f (13%) 175.00fps Trem:   3min 112mb  A-V:-0.041 [822:243]

1 duplicate frame(s)!
Pos: 119.3s   5425f (13%) 174.99fps Trem:   3min 112mb  A-V:-0.041 [821:243]

1 duplicate frame(s)!
Pos: 119.5s   5435f (13%) 174.97fps Trem:   3min 112mb  A-V:-0.041 [821:243]

1 duplicate frame(s)!
Pos: 119.7s   5445f (13%) 174.96fps Trem:   3min 112mb  A-V:-0.041 [820:243]

1 duplicate frame(s)!
Pos: 120.0s   5455f (13%) 174.95fps Trem:   3min 112mb  A-V:-0.041 [820:243]

1 duplicate frame(s)!
Pos: 120.2s   5465f (13%) 174.96fps Trem:   3min 111mb  A-V:-0.041 [820:243]

1 duplicate frame(s)!
Pos: 120.4s   5475f (13%) 174.91fps Trem:   3min 111mb  A-V:-0.041 [820:243]

1 duplicate frame(s)!
Pos: 120.6s   5485f (13%) 174.90fps Trem:   3min 111mb  A-V:-0.041 [820:243]

1 duplicate frame(s)!
Pos: 120.8s   5495f (13%) 174.87fps Trem:   3min 111mb  A-V:-0.041 [820:243]

1 duplicate frame(s)!
Pos: 120.9s   5499f (13%) 174.84fps Trem:   3min 111mb  A-V:-0.029 [820:243]

Too many audio packets in the buffer: (4096 in 2359296 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  820.349 kbit/s  (102543 B/s)  size: 12401621 bytes  120.940 secs  5499 frames

Audio stream:  243.940 kbit/s  (30492 B/s)  size: 3703008 bytes  121.440 secs
slavko@ePodstresnik:~/DVB_RECORDS$
```


ffmpeg got multiple times something like:
```

[h264 @ 0x1152dc0] reference picture missing during reorder
[h264 @ 0x1152dc0] Missing reference picture
[msmpeg4 @ 0x13faa00] warning, clipping 1 dct coefficients to -127..127ts/s 

```

and out of sync audio at the end of the file.

---

### Post by andrew.46 on 2012-11-15
If you keen to come to grips with FFmpeg you could do worse than move on from the rather old and intentionally crippled version you have. Perhaps try this version

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

and hopefully things will be a little smoother :).

---

### Post by eslavko on 2012-11-16
> **andrew.46 said:**
> If you keen to come to grips with FFmpeg you could do worse than move on from the rather old and intentionally crippled version you have. Perhaps try this version

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

and hopefully things will be a little smoother :).

Actually I don't care what software to use. Just want to convert to playable file for my player.

For removing commercials the avidemux is nice. Easy seek and cut. And if I save with AV copy stream is super fast. Sadly I cant use it to do all the job.

If I install 2.5.x version I have DIVX option. But I really can't solve audio sync problem.  At beginning the audio is out of sync for some random time from 0 to aprox 2 seconds. And when some cutting is done the audio sync just get worse and worse. I spend few days to solve that and read forums post but without success. In avidemux 2.6 the audio sync seems perfect. But there are no (right) divx options. (sadly same version for windows have it)

So what I can do?

---

### Post by BicyclerBoy on 2012-11-16
Some of us do care about the s/w we use & go to some effort to understand how to use it..

As Andrew suggested..Your ffmpeg is the *buntu package avconv from libav project.
You could use the real ffmpeg from Jon Serverisson's PPA & install libavc*-extra packages.

Now can see your recordings are H264 (mpe4/10AVC)..
AFAIK Avidemux2.5 makes a mess of H264 files..

A quick expt with latest Avidemux2.6 suggests no interlace encoding support with H264 or mpeg4-asp..that's really bad for TV recordings.
Could use this version to make a cut-list of timecodes..
Or cut at keyframes with avidemux2.6 & save as an mpeg or mkv container file. Makes sense to leave video as H264 (lossless copy).

Then use ffmpeg to convert to XVid with -c:v libxvid into your avi container.

ffmpeg -i input.mpg -c:a libmp3lame -c:v libxvid -mbd rd -vtag xvid -flags +ilme+ildct+mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 out.avi
(assumes libxvid & libmp3lame support)

You can also keyframe cut using the ffmpeg -segment option.
Can cut with mkvmerge -split using the cut timecodes.(mkv out only)
Can record/edit/cut from mythtv & use MythCutKey.sh/lossless_cut.py user jobs.
MythTV can DLNA serve or HLS/airplay stream recordings transcoded to XVid etc.

The audio sync problem with aviddemux2.5 could possibly be fixed by pre-processing with ffmpeg to a constant bitrate video & audio (do not use avi container).

avi files are a disaster for modern video codecs, out-of-order frames & variable bit rate encoding; have no PTS timing information.

You could look into DNLA & bypass burning a disk entirely..
DLNA server, client, render controller..

---

### Post by andrew.46 on 2012-11-16
> **BicyclerBoy said:**
> Then use ffmpeg to convert to XVid with -c:v libxvid into your avi container.

Or perhaps:

```
-c:v mpeg4 -vtag XVID
```

I will have to admit that I have experimented with both and I could not see much of a difference so eventually I settled on this. Interested to hear your thoughts...

---

### Post by eslavko on 2012-11-17
Well I see codec (libxvid) installed but ffmpeg say no.

```
slavko@ePodstresnik:~/DVB_RECORDS$ ffmpeg -i test.mp4 -c:a libmp3lame -c:v libxvid -mbd rd -vtag xvid -flags +ilme+ildct+mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 out.avi
ffmpeg version 0.10.6-6:0.10.6-0ubuntu0jon1~precise1 Copyright (c) 2000-2012 the FFmpeg developers
  built on Nov 12 2012 13:11:38 with gcc 4.6.3
  configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.6-0ubuntu0jon1~precise1' --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1cdc680] multiple edit list entries, a/v desync might occur, patch welcome
    Last message repeated 1 times
[h264 @ 0x1cf28c0] Missing reference picture
    Last message repeated 1 times
[h264 @ 0x1cf28c0] Increasing reorder buffer to 1
[h264 @ 0x1cf28c0] Missing reference picture
    Last message repeated 1 times
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf54.29.104
  Duration: 00:00:51.26, start: 0.120000, bitrate: 1704 kb/s
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p, 720x576 [SAR 16:11 DAR 20:11], 1505 kb/s, 25.03 fps, 50 tbr, 50k tbn, 50 tbc
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: mp2 (mp4a / 0x6134706D), 48000 Hz, 2 channels, s16, 192 kb/s
    Metadata:
      handler_name    : 
Unknown encoder 'libxvid'
slavko@ePodstresnik:~/DVB_RECORDS$ 

```


at least second suggestion works but in report the some audio overhead is reported

```
slavko@ePodstresnik:~/DVB_RECORDS$ ffmpeg -i test.mp4 -c:a libmp3lame -c:v mpeg4 -vtag XVID -mbd rd -vtag xvid -flags +ilme+ildct+mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 out.avi
ffmpeg version 0.10.6-6:0.10.6-0ubuntu0jon1~precise1 Copyright (c) 2000-2012 the FFmpeg developers
  built on Nov 12 2012 13:11:38 with gcc 4.6.3
  configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.6-0ubuntu0jon1~precise1' --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x936680] multiple edit list entries, a/v desync might occur, patch welcome
    Last message repeated 1 times
[h264 @ 0x94c8c0] Missing reference picture
    Last message repeated 1 times
[h264 @ 0x94c8c0] Increasing reorder buffer to 1
[h264 @ 0x94c8c0] Missing reference picture
    Last message repeated 1 times
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf54.29.104
  Duration: 00:00:51.26, start: 0.120000, bitrate: 1704 kb/s
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p, 720x576 [SAR 16:11 DAR 20:11], 1505 kb/s, 25.03 fps, 50 tbr, 50k tbn, 50 tbc
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: mp2 (mp4a / 0x6134706D), 48000 Hz, 2 channels, s16, 192 kb/s
    Metadata:
      handler_name    : 
[buffer @ 0x94df20] w:720 h:576 pixfmt:yuv420p tb:1/1000000 sar:16/11 sws_param:
Output #0, avi, to 'out.avi':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    ISFT            : Lavf53.32.100
    Stream #0:0(und): Video: mpeg4 (hq) (xvid / 0x64697678), yuv420p, 720x576 [SAR 16:11 DAR 20:11], q=2-31, 200 kb/s, 50 tbn, 50 tbc
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, 2 channels, s16, 128 kb/s
    Metadata:
      handler_name    : 
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> mpeg4)
  Stream #0:1 -> #0:1 (mp2 -> libmp3lame)
Press [q] to stop, [?] for help
[h264 @ 0xa577c0] Missing reference picture
    Last message repeated 1 times
[h264 @ 0xa57ca0] Missing reference picture
    Last message repeated 1 times
frame=   49 fps=  0 q=31.0 size=     150kB time=00:00:01.94 bitrate= 633.2kbits/frame=  104 fps=103 q=31.0 size=     235kB time=00:00:04.14 bitrate= 465.2kbits/frame=  157 fps=104 q=31.0 size=     325kB time=00:00:06.26 bitrate= 425.7kbits/frame=  210 fps=104 q=31.0 size=     401kB time=00:00:08.38 bitrate= 392.4kbits/frame=  261 fps=104 q=31.0 size=     474kB time=00:00:10.42 bitrate= 372.3kbits/frame=  313 fps=104 q=31.0 size=     562kB time=00:00:12.50 bitrate= 368.5kbits/frame=  368 fps=104 q=31.0 size=     656kB time=00:00:14.70 bitrate= 365.5kbits/frame=  418 fps=104 q=31.0 size=     739kB time=00:00:16.70 bitrate= 362.4kbits/frame=  473 fps=105 q=31.0 size=     824kB time=00:00:18.90 bitrate= 357.2kbits/frame=  526 fps=105 q=31.0 size=     911kB time=00:00:21.02 bitrate= 355.0kbits/frame=  581 fps=105 q=31.0 size=     977kB time=00:00:23.22 bitrate= 344.6kbits/frame=  631 fps=105 q=31.0 size=    1074kB time=00:00:25.22 bitrate= 348.9kbits/frame=  679 fps=104 q=31.0 size=    1171kB time=00:00:27.14 bitrate= 353.4kbits/frame=  728 fps=103 q=31.0 size=    1258kB time=00:00:29.10 bitrate= 354.1kbits/frame=  780 fps=103 q=31.0 size=    1340kB time=00:00:31.18 bitrate= 352.1kbits/frame=  831 fps=103 q=31.0 size=    1427kB time=00:00:33.22 bitrate= 351.9kbits/frame=  884 fps=103 q=31.0 size=    1520kB time=00:00:35.34 bitrate= 352.3kbits/frame=  933 fps=103 q=31.0 size=    1600kB time=00:00:37.30 bitrate= 351.3kbits/frame=  982 fps=103 q=31.0 size=    1692kB time=00:00:39.26 bitrate= 353.0kbits/frame= 1031 fps=102 q=31.0 size=    1769kB time=00:00:41.22 bitrate= 351.6kbits/frame= 1084 fps=103 q=31.0 size=    1851kB time=00:00:43.34 bitrate= 349.8kbits/frame= 1131 fps=102 q=31.0 size=    1948kB time=00:00:45.22 bitrate= 353.0kbits/frame= 1183 fps=102 q=31.0 size=    2034kB time=00:00:47.30 bitrate= 352.3kbits/frame= 1227 fps=102 q=31.0 size=    2113kB time=00:00:49.06 bitrate= 352.8kbits/frame= 1273 fps=101 q=31.0 size=    2195kB time=00:00:50.90 bitrate= 353.3kbits/frame= 1281 fps=101 q=31.0 Lsize=    2283kB time=00:00:51.16 bitrate= 365.5kbits/s    
video:1363kB audio:800kB global headers:0kB muxing overhead 5.566534%
slavko@ePodstresnik:~/DVB_RECORDS$ 


```

The second one does produce output but is SOO low quality and it's 50 FPS but source is 25. And my player refuse anything above 29.97 (by spec)

---

### Post by andrew.46 on 2012-11-17
For the second example perhaps modify your commandline to something like the following:

```

ffmpeg -i test.mp4 \
       -c:a libmp3lame **[COLOR="Red"]-q:a 3[/COLOR]** \
       -c:v mpeg4 -vtag XVID **[COLOR="Red"]-q:v 5[/COLOR]** -mbd rd -flags +ilme+ildct+mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
       out.avi

```

Perhaps add in *-r 25* to reduce the fps of the output file but this is not the best thing to do, I would recommend compiling a newer version that hopefully would not have the odd effect of reportedly doubling the output fps. This copy of FFmpeg is from a PPA?

---

### Post by BicyclerBoy on 2012-11-17
You look to now be using Jon Severinsson's ffmpeg ppa.

I would (using synaptic) install all the lib*-extras packages..this gives you the un-stripped packages..

The cmd line I suggested were just a starting point & not setup to "configure" the libxvid encoder..

ffmpeg is not too good at interlaced encoding except from progessive or frame rate doubled source (de-interlaced). 
It is possible you may need to use a de-iterlacing filter between the H264 decode & mpeg4 encode (interlaced).

---

### Post by eslavko on 2012-11-19
This seems to be little TO frustrated to make it work. Seems that it's time to find some hardware solution.

---

### Post by BicyclerBoy on 2012-11-19
Plug  PC into your TV or try to use DLNA.

If you must have a consumer box under your TV then look at the new BD player with WiFiDirect etc..

Beware all that proprietary stuff is not designed to work with other brands or open solutions.

The new Samsung TVs can now be hacked to run open source apps which work directly with your server.

---

