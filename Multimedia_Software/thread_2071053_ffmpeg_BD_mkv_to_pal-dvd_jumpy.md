---
title: "ffmpeg BD mkv to pal-dvd jumpy"
date: 2012-10-14
forum: Multimedia Software
---

### Post by essexboyracer on 2012-10-14
I am trying to use the following ffmpeg command to convert MKV ripped BD content to DVD (pal). I am streaming from a d-link DNS-320 via twonky to a sony kdl-32w5500. 

The sony DLNA can only play MPG files. I have successfully done all our DVD discs and would like to get BD content on there in DVD quality (I know, what's the point in decreasing the quality - but whats the point in shipping BD films with DVD versions as well?). I cant keep them as mpg BD quality as our network can't handle the data (wireless, TV one side, NAS on the other side of the room, wife, wires etc)

Original MKV: title00.mkv 299.7 MB
Output MPG: 98.4 MB

ffmpeg -i title00.mkv -target pal-dvd title00.mpg

It appears to do everything correct apart from jumpy video, about every second.

I tried other variations but non success, the output file is just as large as the original

ffmpeg -i title00.mkv -vcodec mpeg2video -sameq -acodec copy -ab 448k -f vob -copyts -y title01.mpg

ffmpeg -i title00.mkv -vcodec mpeg2video -sameq -acodec ac3 -ac 6 -ab 448k -f vob -copyts -y title02.mpg

I also tried this on windows7 and got the same result, jumpy video, so its not the famous VLC media player/ffmpeg performance bug. The 1080p MKV file plays super fine in VLC.

---

### Post by FakeOutdoorsman on 2012-10-14
> **essexboyracer said:**
> I cant keep them as mpg BD quality as our network can't handle the data (wireless, TV one side, NAS on the other side of the room, wife, wires etc)
What is your wireless network speed? What version of Ubuntu are you using?

> **essexboyracer said:**
> ```
ffmpeg -i title00.mkv -target pal-dvd title00.mpg
```
Can you show the complete console output? I'm guessing ffmpeg is dropping frames to compensate for PAL but I am not sure.

> **essexboyracer said:**
> It appears to do everything correct apart from jumpy video, about every second.
Is it jumpy on only the device, or on your computer player too?

> **essexboyracer said:**
> ```
ffmpeg -i title00.mkv -vcodec mpeg2video -sameq -acodec copy -ab 448k -f vob -copyts -y title01.mpg
```

*-sameq* should not be used here: [sameq does not mean "same quality"](http://superuser.com/a/478550/110524). Also it has been removed upstream.

---

### Post by essexboyracer on 2012-10-15
```
oliver@oliver-G71V:~$ ffmpeg -i /media/dlink/Videos/test_t00.mkv -target pal-dvd /home/oliver/Videos/test/title00.mpg
ffmpeg version 0.7.6-4:0.7.6-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jun 12 2012 16:28:10 with gcc 4.6.1
  configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.6ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.6ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[matroska,webm @ 0x8a63a40] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '/media/dlink/Videos/test_t00.mkv':
  Metadata:
    title           : Test
  Duration: 02:22:54.89, start: 0.000000, bitrate: 1536 kb/s
    Chapter #0.0: start 0.000000, end 482.315156
    Metadata:
      title           : Chapter 00
    Chapter #0.1: start 482.315156, end 709.166778
    Metadata:
      title           : Chapter 01
    Chapter #0.2: start 709.166778, end 918.751156
    Metadata:
      title           : Chapter 02
    Chapter #0.3: start 918.751156, end 1233.482244
    Metadata:
      title           : Chapter 03
    Chapter #0.4: start 1233.482244, end 1384.257867
    Metadata:
      title           : Chapter 04
    Chapter #0.5: start 1384.257867, end 1779.444333
    Metadata:
      title           : Chapter 05
    Chapter #0.6: start 1779.444333, end 2243.991733
    Metadata:
      title           : Chapter 06
    Chapter #0.7: start 2243.991733, end 2567.982067
    Metadata:
      title           : Chapter 07
    Chapter #0.8: start 2567.982067, end 3022.269244
    Metadata:
      title           : Chapter 08
    Chapter #0.9: start 3022.269244, end 3664.661000
    Metadata:
      title           : Chapter 09
    Chapter #0.10: start 3664.661000, end 4445.107333
    Metadata:
      title           : Chapter 10
    Chapter #0.11: start 4445.107333, end 5281.234289
    Metadata:
      title           : Chapter 11
    Chapter #0.12: start 5281.234289, end 5900.561333
    Metadata:
      title           : Chapter 12
    Chapter #0.13: start 5900.561333, end 6340.167156
    Metadata:
      title           : Chapter 13
    Chapter #0.14: start 6340.167156, end 6675.085067
    Metadata:
      title           : Chapter 14
    Chapter #0.15: start 6675.085067, end 7067.769022
    Metadata:
      title           : Chapter 15
    Chapter #0.16: start 7067.769022, end 7478.679533
    Metadata:
      title           : Chapter 16
    Chapter #0.17: start 7478.679533, end 7779.396622
    Metadata:
      title           : Chapter 17
    Chapter #0.18: start 7779.396622, end 7990.691022
    Metadata:
      title           : Chapter 18
    Chapter #0.19: start 7990.691022, end 8574.899000
    Metadata:
      title           : Chapter 19
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: dca (DTS), 48000 Hz, 5.1, s16, 1536 kb/s (default)
    Metadata:
      title           : 3/2+1
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
File '/home/oliver/Videos/test/title00.mpg' already exists. Overwrite ? [y/N] y
[buffer @ 0x8ae2980] w:1920 h:1080 pixfmt:yuv420p
[scale @ 0x8c259e0] w:1920 h:1080 fmt:yuv420p -> w:720 h:576 fmt:yuv420p flags:0x4
Output #0, dvd, to '/home/oliver/Videos/test/title00.mpg':
  Metadata:
    title           : Test
    encoder         : Lavf53.3.0
    Chapter #0.0: start 0.000000, end 482.315156
    Metadata:
      title           : Chapter 00
    Chapter #0.1: start 482.315156, end 709.166778
    Metadata:
      title           : Chapter 01
    Chapter #0.2: start 709.166778, end 918.751156
    Metadata:
      title           : Chapter 02
    Chapter #0.3: start 918.751156, end 1233.482244
    Metadata:
      title           : Chapter 03
    Chapter #0.4: start 1233.482244, end 1384.257867
    Metadata:
      title           : Chapter 04
    Chapter #0.5: start 1384.257867, end 1779.444333
    Metadata:
      title           : Chapter 05
    Chapter #0.6: start 1779.444333, end 2243.991733
    Metadata:
      title           : Chapter 06
    Chapter #0.7: start 2243.991733, end 2567.982067
    Metadata:
      title           : Chapter 07
    Chapter #0.8: start 2567.982067, end 3022.269244
    Metadata:
      title           : Chapter 08
    Chapter #0.9: start 3022.269244, end 3664.661000
    Metadata:
      title           : Chapter 09
    Chapter #0.10: start 3664.661000, end 4445.107333
    Metadata:
      title           : Chapter 10
    Chapter #0.11: start 4445.107333, end 5281.234289
    Metadata:
      title           : Chapter 11
    Chapter #0.12: start 5281.234289, end 5900.561333
    Metadata:
      title           : Chapter 12
    Chapter #0.13: start 5900.561333, end 6340.167156
    Metadata:
      title           : Chapter 13
    Chapter #0.14: start 6340.167156, end 6675.085067
    Metadata:
      title           : Chapter 14
    Chapter #0.15: start 6675.085067, end 7067.769022
    Metadata:
      title           : Chapter 15
    Chapter #0.16: start 7067.769022, end 7478.679533
    Metadata:
      title           : Chapter 16
    Chapter #0.17: start 7478.679533, end 7779.396622
    Metadata:
      title           : Chapter 17
    Chapter #0.18: start 7779.396622, end 7990.691022
    Metadata:
      title           : Chapter 18
    Chapter #0.19: start 7990.691022, end 8574.899000
    Metadata:
      title           : Chapter 19
    Stream #0.0(eng): Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-31, 6000 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, flt, 448 kb/s (default)
    Metadata:
      title           : 3/2+1
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
Input stream #0.1 frame changed from rate:48000 fmt:s16 ch:6 to rate:48000 fmt:flt ch:6
frame=   50 fps= 50 q=2.0 size=     114kB time=1.96 bitrate= 476.5kbits/s dup=1 
frame=   53 fps= 21 q=1.6 size=     136kB time=2.08 bitrate= 535.6kbits/s dup=1 
frame=   64 fps= 21 q=2.0 size=     624kB time=2.52 bitrate=2028.5kbits/s dup=2 
frame=   72 fps= 20 q=2.0 size=    1056kB time=2.84 bitrate=3046.0kbits/s dup=2 
frame=   73 fps= 16 q=6.5 size=    1112kB time=2.88 bitrate=3163.0kbits/s dup=2 
frame=   82 fps= 16 q=8.6 size=    1522kB time=3.24 bitrate=3848.2kbits/s dup=2 
frame=   92 fps= 16 q=7.2 size=    1982kB time=3.64 bitrate=4460.6kbits/s dup=3 
frame=   93 fps= 14 q=5.1 size=    2030kB time=3.68 bitrate=4519.0kbits/s dup=3 
frame=  100 fps= 14 q=3.0 size=    2354kB time=3.96 bitrate=4869.7kbits/s dup=3 
frame=  107 fps= 14 q=6.5 size=    2700kB time=4.24 bitrate=5216.6kbits/s dup=3 
frame=  112 fps= 13 q=5.4 size=    2930kB time=4.44 bitrate=5406.0kbits/s dup=4 
frame=  120 fps= 13 q=11.5 size=    3314kB time=4.76 bitrate=5703.4kbits/s dup=4
frame=  127 fps= 13 q=5.5 size=    3632kB time=5.04 bitrate=5903.4kbits/s dup=4 
frame=  129 fps= 12 q=8.3 size=    3732kB time=5.12 bitrate=5971.2kbits/s dup=4 
frame=  138 fps= 12 q=3.8 size=    4134kB time=5.48 bitrate=6179.9kbits/s dup=5 
frame=  145 fps= 12 q=4.0 size=    4472kB time=5.76 bitrate=6360.2kbits/s dup=5 
frame=  145 fps= 11 q=4.0 size=    4472kB time=5.76 bitrate=6360.2kbits/s dup=5 
frame=  152 fps= 11 q=7.0 size=    4812kB time=6.04 bitrate=6526.5kbits/s dup=5 
frame=  160 fps= 11 q=7.2 size=    5152kB time=6.36 bitrate=6636.0kbits/s dup=6 
frame=  160 fps= 11 q=7.2 size=    5152kB time=6.36 bitrate=6636.0kbits/s dup=6 
frame=  168 fps= 11 q=3.6 size=    5502kB time=6.68 bitrate=6747.4kbits/s dup=
frame=  174 fps= 11 q=2.7 Lsize=    5694kB time=6.91 bitrate=6748.4kbits/s dup=8 drop=0    
video:5213kB audio:378kB global headers:0kB muxing overhead 1.847904%
Received signal 2: terminating.

```

---

### Post by essexboyracer on 2012-10-15
using xubuntu 11.10 oneiric 3.0.0.26-generic

the conversion is jumpy on the computer, so I think that rules out network connectivity (for the minute, perhaps a side issue later on).

Yes, I read that sameq isn't literal, the command I found was a copy and paste job.

---

### Post by FakeOutdoorsman on 2012-10-16
> **essexboyracer said:**
> 
```

Input:
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc
 Output:
    Stream #0.0(eng): Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-31, 6000 kb/s, 90k tbn, 25 tbc

```

Try to put your console outputs into the [noparse]```

```[/noparse] tags since it will make it easier to read.

The frame rate differs between input (23.98 NTSC Film) and output (25 PAL). FFmpeg will simply drop or duplicate frames, as in your case, if the input and output frame rates vary which probably doesn't always look good. Fortunately there is also the film- prefix which will provide the proper frame rate of 23.98, or more specifically 24000/1001.

Try this:
```
ffmpeg -i /media/dlink/Videos/test_t00.mkv -target film-dvd /home/oliver/Videos/test/title00.mpg
```

---

### Post by essexboyracer on 2012-10-17
Wow, thank you. An initial test appeared to have solved the skipping. I never knew about the film-dvd preset, probably a case of RTFM on my behalf. Have cleaned up my post earlier with the code tags.

Does film-dvd provide any better quality than pal-dvd?

---

### Post by FakeOutdoorsman on 2012-10-17
> **essexboyracer said:**
> Wow, thank you. An initial test appeared to have solved the skipping. I never knew about the film-dvd preset, probably a case of RTFM on my behalf.
Glad it worked out for you. The docs aren't always easy to follow.

> **essexboyracer said:**
> Does film-dvd provide any better quality than pal-dvd?
No. The only difference between film-dvd and pal-dvd is the frame rate and the "group of picture size" (*-g* option), but the quality should be the same. The trick is matching the proper frame rates for the input and output when using *-target*.

---

### Post by essexboyracer on 2012-10-17
> The trick is matching the proper frame rates for the input and output when using -target

That explains the jumpy video. thank you again for your help. marked as solved.

---

### Post by essexboyracer on 2012-10-18
Interestingly, the Sony TV DLNA cant seem to see the film-dvd encoded file. I am trying to re-encode it using the film-dvd file to pal-dvd. This TV is so picky about its files...

---

### Post by essexboyracer on 2012-10-19
SO the conversion from film-dvd to pal-dvd didnt work, were back to skippy jumpy video, but the TV can now pick up on the pal-dvd file and play it, where as it couldn't see the film-dvd file.

I can see the film-dvd file from twonkies browser interface and obviously play it via the laptop on VLC.

Any other ideas? Like you say it does appear to be connected with framerates, but I can't understand how a DVD converts fine?

---

### Post by FakeOutdoorsman on 2012-10-19
I have little experience with changing frame rates and no experience using  Sony DLNA. AviSynth or avxsynth may be worth looking into, but I've never really used those either.

---

### Post by essexboyracer on 2012-10-20
No problem. It does appear that DLNA on the Sony is the main problem, with encoding the BD files as mpg probelm a result of the DLNA on the Sony. The manual states that it only picks up AVCHD and mpg (mpeg2) files.

I will leave this as unsolved for anyone else to pick up. THanks again

---

### Post by qyot27 on 2012-10-23
> **FakeOutdoorsman said:**
> I have little experience with changing frame rates and no experience using  Sony DLNA. AviSynth or avxsynth may be worth looking into, but I've never really used those either.
It depends on what course of action you decide to take.

You can perform what's called a Euro pulldown, where 23.976 fps footage is flagged to play back at PAL standard 25 fps by duplicating frames on the fly (similar to the typical NTSC case of flagging 23.976 to 29.97).  Those in NTSC countries are very familiar with telecined video, so they practically don't notice the duplication when watching it.  PAL countries don't normally do this with Film content (instead they speed the video up and adjust the audio pitch, slightly shortening the running time), so it can be very noticeable to the eyes of people used to the typical PAL speed-up technique.

Euro pulldown - if that's what you decide on doing - can be accomplished by running the video stream you get from FFmpeg through DGPulldown (you'll need Wine).  You'll want to demux the video from the output .mpg file first, and you have to use the GUI - DGPulldown's CLI interface refuses to work with Wine.

PAL speed-up can indeed be done by using AviSynth.  Not sure if AvxSynth finally got its audio functions fixed, so it may be a no-go.  But AviSynth can definitely perform this, and rather simply:
```
FFmpegSource2("input.mkv",atrack=-1,fpsnum=24000,fpsden=1001)
AssumeFPS(25,sync_audio=true)
SSRC(48000,fast=false)
```
(if it says there's an error with SSRC not being able to resample the audio, just copy and paste the SSRC line above AssumeFPS, so that it goes SSRC->AssumeFPS->SSRC).

And then you feed the script to the encoder.  Again, needs Wine (which also means you could use HCenc as the MPEG-2 encoder instead of ffmpeg, if you wanted to).

---

### Post by FakeOutdoorsman on 2012-10-23
Interesting and informative post. Thanks.

---

### Post by BicyclerBoy on 2012-10-23
AFAIK
The frame duplication for rate change of film to NTSC rates is not called euro pulldown; is named Telecining/3:2 pulldown.

Euro judder/pulldown is the frame duplication to play PAL at approx. NTSC frame rate TVs; uses 2:2:3:2:3 pulldown.

Possibly the best soln could be to use pull down & then allow the TV to detect & inverse telecine & play correctly at 24p cadence.

AFAIK The only linux tools that do correct frame rate conversion by interpolation are mjpegtools & yuvmotionfps/yuvtools.
These tools use pipes so can avoid the enormous intermediate files.

It is not recommended to use frame creation for PAL to NTSC conversion..

---

### Post by qyot27 on 2012-10-24
> **BicyclerBoy said:**
> AFAIK
The frame duplication for rate change of film to NTSC rates is not called euro pulldown; is named Telecining/3:2 pulldown.
I never said it was.  ["Euro pulldown" is 23.976->25, or to be more precise, 2:2:2:2:2:2:2:2:2:2:2:3 pulldown.](http://forum.doom9.org/showthread.php?t=151372)

[http://en.wikipedia.org/wiki/Telecine](http://en.wikipedia.org/wiki/Telecine)
> This pulldown method is sometimes used in order to convert 24 frame/s material to 25 frame/s. Usually, this involves a film to PAL transfer without the aforementioned 4% speedup. For film at 24 frame/s, there are 24 frames of film for every 25 frames of PAL video. In order to accommodate this mismatch in frame rate, 24 frames of film have to be distributed over 50 PAL fields. This can be accomplished by inserting a pulldown field every 12 frames, thus effectively spreading 12 frames of film over 25 fields (or &#8220;12.5 frames&#8221;) of PAL video. The method used is 2:2:2:2:2:2:2:2:2:2:2:3 (Euro) pulldown (see below).
...
...
PAL material in which 2:3 pulldown has been applied, suffers from a similar lack of smoothness, though this effect is not usually called &#8220;telecine judder&#8221;. Effectively, every 12th film frame is displayed for the duration of three PAL fields (60 milliseconds), whereas the other 11 frames are each displayed for the duration of two PAL fields (40 milliseconds). This causes a slight &#8220;hiccup&#8221; in the video about twice a second. Increasingly being referred to as Euro pulldown as it largely affects European territories.

Doing a 25->29.97 flagging doesn't have any sort of special name beyond the flag pattern.  This is only suitable for material that actually was composed to be played back at 25fps, since it would be incorrect to take material that had been subjected to PAL speed-up (like a Hollywood movie's European DVD release) and do the operation on it - you could just take it back to the original film rate and do a proper 3:2 on it.  Why someone in an NTSC country would buy a European disc of a Hollywood movie is the probably more important question that situation raises anyway (the only reason I can think of is that the movie wasn't popular enough to get a release in North America), not how to properly deal with it.

But for things actually produced in Europe, Australia, Africa, most of Asia and most of Central/South America, in which the audio is at a normal pitch and the frame rate is 25, slowing it down first to suit 23.976 will result in things sounding deeper than they should.  Doing 25->29.97 pulldown flagging is the cleanest option to handle it without mucking with the audio (or deleting one frame every second, which would make the typical telecine judder that much worse), since the alternative - hard telecine requiring hardcoded interlacing - is incredibly messy and requires any software-based players to try and deinterlace or IVTC first, which often produces subpar results (it's also arguable that this might also be true of newer TVs and DVD players that either aren't hooked up/configured correctly or that just have problems with playback of interlaced content).  If it's just flagged, players are typically intelligent enough to just remove the flags and return it to the proper framerate for playback.  At least, mplayer does, and I've never had issues with my DVD players or TVs accepting 25->29.97 pulldown and it remaining smooth (or me just not noticing the hiccup).

Short of your TV/computer monitor being able to output at 600Hz (or being able to switch between 47.952/48Hz, 50Hz, and 59.94/60Hz or multiples thereof, like 100 and 120), any conversion of actual framerate between NTSC, PAL, and Film will result in judder - whether it's noticeable to the viewer is a different story.

---

### Post by BicyclerBoy on 2012-10-26
Learn something new very day..I thought euro judder was from playback of 25fps on 30 fps displays..

The latest TVs have real refresh rates of 100/120Hz.

And the 24p mess is now happening with BDs (recording of i50 & 50p "motionflowed" to VC1-24p). 

I would hazard a guess that almost all PAL-land TVs & DVD players are happy playing NTSC frame rate media at native framerate.

The OP could try to make a NTSC DVD from the original..
That "conversion" is not so destructive/complicated & the player has a chance of detecting & undoing the damage.
24p is so flickery anyway without frame creation tricks that conversion to NTSC DVD could be fine.

ffmpeg can not encode (with correct temporal space) progressive scan video to interlaced video unless the original-fps=final-fps.
i.e. need 50p to encode to i50(25fps).

Possible to play 24p in ffmpeg  & pipe (rawvideo) to mjpegtools (24p->60p) pipe to ffmpeg to encode NTSC DVD.
Used this approach to convert 17fps DV to PAL DVD.

---

### Post by qyot27 on 2012-10-27
> **BicyclerBoy said:**
> I would hazard a guess that almost all PAL-land TVs & DVD players are happy playing NTSC frame rate media at native framerate.

The OP could try to make a NTSC DVD from the original..
That "conversion" is not so destructive/complicated & the player has a chance of detecting & undoing the damage.
24p is so flickery anyway without frame creation tricks that conversion to NTSC DVD could be fine.
I think it's possible insofar as the framerate is concerned (I seem to remember reading that newer PAL TVs can play 24 and 30 without issues - probably gained as part of the move to HDTV and Blu-ray), but the resolution is where the problem lies: I would expect a PAL DVD player to choke on an NTSC DVD because of the resolution difference.  Whether a PAL Blu-ray player can handle NTSC DVDs is iffy, I guess.  But this may have been more of an issue with the first wave of BD players; the trend seems to be going to supporting all of this natively no matter where you are, so it may very well be possible now.  I just wouldn't go in expecting it to work; if it does, I'd consider it a nice fringe bonus.


To be honest, the trickiness of getting a native workflow to behave correctly on this is why I prefer to do it with Windows tools (read, AviSynth and HCenc) in Wine.  HCenc can properly apply 3:2 pulldown to 23.976fps video during the encoding phase; DGPulldown is only necessary if you need to do exotic patterns, like 24 integer or 25 as the original fps.

---

### Post by FakeOutdoorsman on 2012-10-27
> **qyot27 said:**
> To be honest, the trickiness of getting a native workflow to behave correctly on this is why I prefer to do it with Windows tools (read, AviSynth and HCenc) in Wine.

I'll mention [HOWTO: AviSynth video processing with WINE](http://ubuntuforums.org/showthread.php?t=1333264) for other readers who may be interested in following this route.

---

### Post by BicyclerBoy on 2012-10-28
It's a real shame & sad that AviSynth does not exist as a native app.

My attempt to convert 17fps to PAL DVD with mjpegtools etc resulted in a "better" soln than the Adobe FinalCut Pro motion-flow.

I've never had problems playing NTSC DVDs in PAL-land DVD players.
YMMV if you suffer with zoning issues..

The first wave of BD players were Sony PS3 with which they buried HD-DVD.
The US versions of PS3 can not play BD i50.

I haven't purchased any BDs with i50 (BBC Life/Planet Earth) because it is too easy to end up with a US 24p motionflow version..
Downton Abbey was mangled to 24p because of US market.

---

### Post by qyot27 on 2012-10-28
> **BicyclerBoy said:**
> It's a real shame & sad that AviSynth does not exist as a native app.
Well, AvxSynth exists.  And now so does VapourSynth.  Two different approaches, with differing levels of compatibility with AviSynth.  Disregarding, of course, that the plugins (which are really what makes the tool so versatile) are independent of the core even with the original and would also have to be ported to be useful (although there was brief talk about how it would be cool to have a thunking layer for the plugin .dlls to work with AvxSynth since relatively few of them rely on the Windows subsystem).

I think much of the relative lack of activity in getting the external filters ported is sort of a case of waiting with baited breath that one of the solutions actually succeeds and takes hold.  Or the developers being Windows-centric, or with some plugins, being just plain old and active development on them having stopped years ago because there just wasn't anything else to add.

Speaking of AvxSynth, though, there is some activity right now regarding changes to FFmpeg's AviSynth parser that would allow it to accept AvxSynth input on Linux.  Hopefully this happens soon and then there'll be more traction to work with on that front.

---

### Post by essexboyracer on 2012-11-03
Thanks for all your replies, it appears my problem may be more expansive than originally thought and perhaps I haven't given you enough information, particurally about the hardware I am using. 

I may try a ntsc-dvd conversion but am not holding out much hope. I may leave this thread for the moment and probably re-visit it in a year or so

---

### Post by BicyclerBoy on 2012-11-03
I'd like to thank qyot27 for the detailed & interesting replies..

I did not know of avxsyth etc..

---

### Post by qyot27 on 2012-11-04
In regards to AvxSynth, the effectiveness of the patch for FFmpeg to allow using it directly is influenced by the particular version of FFmpeg you're using - I experienced segfaults when using the git master (and I later found this same caveat in the patch thread on ffmpeg-devel), but it supposedly works if you use 1.0 or 0.11.  For reference, though, the relevant posts are:

[http://ffmpeg.org/pipermail/ffmpeg-devel/2012-September/131529.html](http://ffmpeg.org/pipermail/ffmpeg-devel/2012-September/131529.html) (for the avs_ffmpeg_configure.diff only)
[http://ffmpeg.org/pipermail/ffmpeg-devel/2012-October/132129.html](http://ffmpeg.org/pipermail/ffmpeg-devel/2012-October/132129.html) (for an updated version of avisynth.c)

You also need to fiddle with some of the install paths for the include files, and if you're using FFMS2 from SVN, you'll need to patch AvxSynth because it fails to build libavxffms2 ever since libpostproc support was completely removed from the trunk.  As of r730, though, you no longer need to run autogen.sh to get VapourSynth support activated.



There are, however, another couple of patches, included on [0x09's osx branch](https://github.com/0x09/avxsynth), that enable AvxSynth to be used as input by mplayer2 (through mpdemux) and x264 (by modifying the existing AviSynth input support).  These patches are considered to be temporary until the libavformat demuxer is complete/accepted (although I can't see how lavf support of AvxSynth would solve this for x264, since its AviSynth input has always been discrete), but I know first-hand that the mplayer2 patch works, and that it works with ffmpeg-git.  It allows for both seeking backwards and forwards in scripts and to output audio, the latter of which was an issue for the avxFrameServer application that's bundled with the source (and which is apparently undergoing a rewrite right now).  And in the event that you built the vo-lavc branch of mplayer2, it also lets you transcode using the script as input.


With VapourSynth support, x264 still hasn't received an official update, so getting support for the extended Y4M colorspaces is still only in the x264-devel branch.

If installing both VapourSynth and AvxSynth (because it is possible and they don't conflict with each other), then you should install VapourSynth first.  Mostly because FFMS2 as built from SVN supports it as-is, and you need FFMS2 installed prior to AvxSynth so it can use it to generate libavxffms2.

---

