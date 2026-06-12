---
title: "Webcam streaming difficulty: ffmpeg, ffserver, webm format"
date: 2011-09-20
forum: Multimedia Software
---

### Post by michaeljtbrooks on 2011-09-20
Hello,

I'm a long-time-lurker first-time-poster who recently got fully converted from the dark side (windows)...

I am struggling to get my webcam with audio streaming across my home LAN via ffmpeg/ffserver. I'd appreciate any help to get this working.

::The Problem::

I can start ffserver with no problems.

When I call ffmpeg, I get the below output. At the bottom the number of frames / kB encoded is shown for a second, then the encoding stops and I am returned back to my command line.

I'm accessing my server via SSH. Interestingly, after calling the ffmpeg, putty then becomes incapable of displaying any characters I type, yet commands from the command line still execute.

Attempts to access the stream on another network computer at http://<server's LAN IP>:58081/test.webm via VLC fail.

I have tested ffmpeg without ffserver and it is able to capture the webcam video and audio to a .webm file which I can then play back remotely via VLC without a problem. libvpx and libogg are definitely installed on the server.

Any ideas what I am doing wrong? I ideally want low-latency (real-time) audio and video streaming from the webcam.


::ffmpeg info::
```

FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep 16 2011 17:11:24 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[video4linux2 @ 0x973d420]Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2, from '/dev/video0':
  Duration: N/A, start: 3457623.726137, bitrate: -2147483 kb/s
    Stream #0.0: Video: rawvideo, yuyv422, 1280x720, -2147483 kb/s, 1000k tbr, 1000k tbn, 1000k tbc
[alsa @ 0x973eb20]Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'hw:1,0':
  Duration: N/A, start: 3457624.998958, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 48000 Hz, 1 channels, s16, 768 kb/s
[libvpx @ 0x9749860]v0.9.5
Output #0, webm, to 'http://localhost:58180/feed1.ffm':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: libvpx, yuv420p, 1280x720, q=2-31, 512 kb/s, 1k tbn, 15 tbc
    Stream #0.1: Audio: libvorbis, 16000 Hz, 1 channels, s16, 32 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Press [q] to stop encoding
$mike@metis:~$ [putty now won't display any characters here!]

```::My Configuration & Commands ::

OS: Maverick (server)
Webcam: Logitech HD C270

-------/etc/ffserver.conf-------
```
Port 58180
BindAddress 0.0.0.0
MaxHTTPConnections 2000
MaxClients 1000
MaxBandwidth 4096
CustomLog -

<Feed feed1.ffm>
 File /tmp/feed1.ffm
 FileMaxSize 1024K
 ACL allow 127.0.0.1
</Feed>

<Stream test.webm>
# --FEED--
        Feed feed1.ffm
        Format webm
# --VIDEO--
        VideoCodec libvpx
        VideoFrameRate 15
        VideoBufferSize 80000
        VideoBitRate 512
        VideoQMin 1
        VideoQMax 10
        VideoSize 1280x720
        PreRoll 0
# --AUDIO--
        AudioBitRate 32
        AudioChannels 1
        AudioSampleRate 16000
        #AudioCodec libogg
</Stream>
```----------------------------------

```

$ ffserver
$ ffmpeg -s hd720 -f video4linux2 -i /dev/video0 -vcodec libvpx -vb 512000 -r 15 -f alsa -ac 1 -i hw:1,0 -acodec libvorbis -ab 32000 -ar 16000 -f webm [http://localhost:58180/feed1.ffm](http://localhost:58180/feed1.ffm)
```
Cheers,
Mike

---

### Post by michaeljtbrooks on 2011-09-21
Further to my webcam streaming in WebM format woes...

I've managed to get FFmpeg capturing video and audio from my webcam (Logitech C270 with built in mic).

However despite experimenting with all manner of vsync and async  options, I can either get out of sync audio, or Benny Hill style  fast-forward video with matching fast audio. The stream needs to run at less than 1Mbps total, so I'm limited on the fidelity.

```
ffmpeg -s 640x360 \ -f video4linux2 -i /dev/video0 -isync -vcodec libvpx -vb 768000 -r 10 -vsync 1 \ -f alsa -ac 1 -i hw:1,0 -acodec libvorbis -ab 32000 -ar 11025 \ -f webm /var/www/telemed/test.webm 
```What am I doing wrong to end up with out of sync audio + video?

Cheers,
Mike

---

### Post by michaeljtbrooks on 2011-09-24
Bump!

Recap:
FFmpeg streaming of webM video from webcam in near real-time. Anyone know how to make the audio and video in-sync, and then get it working with FFstreamer? See above.

---

### Post by michaeljtbrooks on 2011-10-03
Bump! Anyone?

---

### Post by mike4ubuntu on 2011-10-05
Can anybody explain why when I capture video and audio from devices, I get video ok, but the audio cuts out after a second or two?

```

ffmpeg -s 640x480 \
-t 00:00:30 \
-f video4linux2 -i /dev/video0 -isync -vcodec libvpx -vb 768000 -r 10 -vsync 1 \
-f alsa -ac 1 -i pulse -acodec libvorbis  -ab 32k -ar 16000 \
-f webm art-webcam-test-pulse-`date +%Y%m%d-%H.%M.%S`.webm 

```

it seems to be the ```
-t 00:00:30
``` that's causing the problem.  My intent of using the -t to limit it to 30 seconds of capture.  If I take it out and just let the capture run, the video and sound both get captured.

---

### Post by mike4ubuntu on 2011-10-06
I too have issues with syncing the video and the audio.  I see and hear it as much as 3 seconds or so.  

I found this:

[http://howto-pages.org/ffmpeg/]("http://howto-pages.org/ffmpeg/")

> DELAYING THE AUDIO OR THE VIDEO

Depending on how your original files were generated, it could happen that the sound and the picture become out of sync when you start processing them with ffmpeg. Thankfully, there's a mechanism that will allow you to stagger the audio and video with respect to each other in the output, thus bringing them back into alignment &#8722; the "-itsoffset" option, which is used this way:

$ ffmpeg -i input_1 -itsoffset 00:00:03.5 -i input_2 ...........

In this example, input_2 will be delayed by 3.5 seconds. In other words, The content of input_1 will start at the beginning of the movie generated by ffmpeg, and the content in input_2 will start 3.5 seconds into the movie.

In real life you're unlikely to come across such an extreme case of A/V skew. I do, however, come across cases regularly that need correcting by a fraction of a second. Using MPlayer to fast-forward into the movie you're generating and then the + and - keys to add more or less delay in 100ms increments gives you a good idea of how much delay to use and whether it's the sound or the picture that needs delaying.

Remember to put the source that needs delaying after the "-itsoffset" option. Thus, if the audio comes in too soon and needs delaying:

$ ffmpeg -i video_source -itsoffet delay -i audio_source -map 0:x -map 1:y ......

Conversely, if the audio comes in too late and the video therefore needs delaying:

$ ffmpeg -i audio_source -itsoffet delay -i video_source -map 1:x -map 0:y ......

Note how the "-map" options specify video from the second source and audio from the first in this second example.

Note also that video_source and audio_source can be the same file. Nothing's to stop you from fixing (or breaking) the A/V sync within the same original movie. 

I haven't had a chance to test this yet, and I don't quite understand how to use the -map parameters.

---

### Post by mike4ubuntu on 2011-10-06
Also, can try the -async parameter

```
# Audio sync method. "Stretches/squeezes" the audio stream to match the timestamps, 
# the parameter is the maximum samples per second by which the audio is changed. 
# -async 1 is a special case where only the start of the audio stream is corrected without any later correction. 
ffmpeg \
-f video4linux2 -s hd480 -i /dev/video0 -isync -vcodec libvpx -vb 600000 -r 30 -vsync 1 \
-f alsa -ac 1 -i pulse -acodec libvorbis  -ab 96k -ar 48000 -async 1\
-f webm art-webcam-test-pulse-`date +%Y%m%d-%H.%M.%S`.webm

```

also, the async option takes samples as parameter.  Found this:

> The documentation is a bit sketchy on that (and many other points), but 
them as complain can feel free to rewrite it :).  AFAIK, -async X will 
resample the audio track to speed up or slow down by as much as X 
samples per second as required to match the video timestamps.  You 
probably don't need to make big adjustments, you're talking 1 second in 
5 minutes, less than 1%.  If you sample audio at 48000 an -async 480 
would be more than enough to compensate.


```
# try also the -async delay
ffmpeg \
-f video4linux2 -s hd480 -i /dev/video0 -isync -vcodec libvpx -vb 600000 -r 14 -vsync 1 \
-f alsa -ac 1 -i pulse -acodec libvorbis  -ab 96k -ar 48000 -async 480 \
-f webm art-webcam-test-pulse-`date +%Y%m%d-%H.%M.%S`.webm

```

---

