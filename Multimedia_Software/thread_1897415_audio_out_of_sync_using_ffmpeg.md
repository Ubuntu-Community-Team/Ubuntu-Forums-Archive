---
title: "audio out of sync using ffmpeg"
date: 2011-12-19
forum: Multimedia Software
---

### Post by unckybob on 2011-12-19
The file I am trying to convert:

# ffmpeg -i test.mpg
ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:13:26 with gcc 4.6.1
  configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[mpeg @ 0x21f2340] max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 59.94 (60000/1001)
Input #0, mpeg, from 'test.mpg':
  Duration: 00:32:59.81, start: 14801.723367, bitrate: 4606 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 23.98 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
At least one output file must be specified

I tried the following commmand: 

# ffmpeg -i test.mpg -ac 2 -b 1500k output4.avi
ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:13:26 with gcc 4.6.1
  configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[mpeg @ 0x11ec340] max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 59.94 (60000/1001)
Input #0, mpeg, from 'test.mpg':
  Duration: 00:32:59.81, start: 14801.723367, bitrate: 4606 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 23.98 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
[buffer @ 0x11ee9a0] w:720 h:480 pixfmt:yuv420p
Output #0, avi, to 'output4.avi':
  Metadata:
    ISFT            : Lavf53.2.0
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=2-31, 1500 kb/s, 59.94 tbn, 59.94 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
Input stream #0.1 frame changed from rate:48000 fmt:s16 ch:6 to rate:48000 fmt:s16 ch:2
frame=47459 fps=211 q=1.9 Lsize=  382040kB time=1979.18 bitrate=1581.3kbits/s    
video:361831kB audio:15462kB global headers:0kB muxing overhead 1.258185%

The only problem with this is that the further along you get in the video, the further the audio gets out of sync with the video. 

Can someone suggest a way to use the ffmpeg command to make this mpg into an avi video that is in sync?

---

### Post by unckybob on 2011-12-19
I did some reading on the man pages and the following command got things synced up:

ffmpeg -i test.mpg -ac 2 -b 3000k -s 352x288 -async 1 output.avi

Unfortunately, the video quality is not so good. I tried upping the bit rat from 1000k to 3000k with no effect. Does anyone have any ideas?

---

### Post by sudodus on 2011-12-19
I have had similar problems converting from avi to mp4, particularly if avi was not the original format (dv --> avi --> mp4). I'm interested in tips and advice, so I will subscribe to your thread.

---

### Post by flemur13013 on 2011-12-19
avidemux sometimes works where ffmpeg doesn't and vice-versa.

---

### Post by unckybob on 2011-12-19
With this particular file avidemux doesn't get me a file with any sound, but thanks.

---

### Post by unckybob on 2011-12-19
I think there is some kind of upper limit on how good quality can be when you are transcoding. This command seems to get the best results:

ffmpeg -i test.mpg -ac 2 -qscale 1 -s 352x288 -async 1 output.avi

If you have any better ideas, I hope you'll post them here.

---

### Post by FakeOutdoorsman on 2011-12-19
Is there a particular reason you want to use the AVI container? There are usually better choices, but of course there are always exceptions.

I've personally never had to use -async, and -qscale is the option to use to control the video quality and usually recommend it instead of -b. Use -qscale when you want to set a particular quality level, or -b if you are trying to get a particular output file size.

Also, your ffmpeg output will be easier to read if you use the code tag:

[noparse]```
ffmpeg -i input.mp4 ...
```[/noparse]

...resulting in:
```
ffmpeg -i input.mp4 ...
```

---

### Post by shantiq on 2011-12-20
> **unckybob said:**
> 

I tried the following commmand: 

# ffmpeg -i test.mpg -ac 2 -b 1500k output4.avi



well there ffmpeg is a great prog and so is mencoder
i have found sometimes one works better than the other for a specific job
i do not know why ; but i always give both a whirl if something is amiss in the first one


so  maybe try  > mencoder  input.mpg  -oac lavc -lavcopts acodec=ac3 :abitrate=224 -ovc xvid -xvidencopts pass=1 bitrate=1500 -o output.avi    


hope your sync works here  :KS   [adjust bitrate for audio and video to suit your needs]



further refinement mayhaps

> 7.1.9. Notes on Audio/Video synchronization

MEncoder's audio/video synchronization algorithms were designed with the intention of recovering files with broken sync. However, in some cases they can cause unnecessary skipping and duplication of frames, and possibly slight A/V desync, when used with proper input (of course, A/V sync issues apply only if you process or copy the audio track while transcoding the video, which is strongly encouraged). Therefore, you may have to switch to basic A/V sync with the -mc 0 option, or put this in your ~/.mplayer/mencoder config file, as long as you are only working with good sources (DVD, TV capture, high quality MPEG-4 rips, etc) and not broken ASF/RM/MOV files. 

 [COLOR="DarkRed"]If you want to further guard against strange frame skips and duplication, you can use both **-mc 0**[/COLOR] and -noskip. This will prevent all A/V sync, and copy frames one-to-one, so you cannot use it if you will be using any filters that unpredictably add or drop frames, or if your input file has variable framerate! Therefore, using -noskip is not in general recommended. 

 

so maybe

> mencoder input.mpg -oac lavc -lavcopts acodec=ac3 :abitrate=224 -ovc xvid -xvidencopts pass=1 bitrate=1500   [COLOR="DarkRed"]-mc 0[/COLOR] -o output.avi

---

### Post by satanselbow on 2011-12-20
> **unckybob said:**
> 

ffmpeg -i test.mpg -ac 2 -b 3000k -s 352x288 -async 1 output.avi

Unfortunately, the video quality is not so good. I tried upping the bit rat from 1000k to 3000k with no effect. Does anyone have any ideas?

Is there any particular reason you are shrinking the frame size so significantly? 720x480 -> 352x288

That would have a significant impact on quality when viewing the resultant video on a fullscreen monitor / TV etc.

Also ffmpeg defaults to very low quality audio (64k) if you do not specify a bit rate ;)

---

### Post by shantiq on 2011-12-20
whoops had not seen scale requirements  :KS


so this instead of my earlier posting might/should/will give you joy

>  mencoder input.mpg -o output.avi -ovc xvid -xvidencopts bitrate=1800  -vf scale=352:288  -oac lavc -lavcopts acodec=ac3 :abitrate=224






would pick .mkv instead of .avi as it is often more stable [simply replace]
bitrates can be modified to suit needs...

---

### Post by shantiq on 2011-12-20
==sorry duplicate==

---

