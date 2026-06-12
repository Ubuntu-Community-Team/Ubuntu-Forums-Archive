---
title: "How to combine video files together...?"
date: 2009-09-21
forum: Multimedia Software
---

### Post by sroussey on 2009-09-21
I followed this post to install ffmpeg/x264:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Then I followed the example at [http://ffmpeg.org/faq.html#SEC30:](http://ffmpeg.org/faq.html#SEC30:)

mkfifo temp1.a
mkfifo temp1.v
mkfifo temp2.a
mkfifo temp2.v
mkfifo all.a
mkfifo all.v
ffmpeg -i input1.mp4 -vn -f u16le -acodec pcm_s16le -ac 2 -ar 44100 -
> temp1.a < /dev/null &
ffmpeg -i input2.flv -vn -f u16le -acodec pcm_s16le -ac 2 -ar 44100 -
> temp2.a < /dev/null &
ffmpeg -i input1.mp4 -an -f yuv4mpegpipe - > temp1.v < /dev/null &
ffmpeg -i input2.flv -an -f yuv4mpegpipe - > temp2.v < /dev/null &
cat temp1.a temp2.a > all.a &
cat temp1.v temp2.v > all.v &
ffmpeg -f u16le -acodec pcm_s16le -ac 2 -ar 44100 -i all.a \
      -f yuv4mpegpipe -i all.v \
      -sameq -y output.flv
rm temp[12].[av] all.[av]

I get a resulting file that has all the audio, but only the first video. after the first video, there is just the last frame of the first video until the all the audio ends.

Besides changing the first vid reference to an mp4 (my preroll), I've tried adding -r 30 -s vga -b 512k  to make it the same if not already:

mkfifo temp1.a
mkfifo temp1.v
mkfifo temp2.a
mkfifo temp2.v
mkfifo all.a
mkfifo all.v
ffmpeg -i input1.mp4 -vn -f u16le -acodec pcm_s16le -ac 2 -ar 44100 -
> temp1.a < /dev/null &
ffmpeg -i input2.flv -vn -f u16le -acodec pcm_s16le -ac 2 -ar 44100 -
> temp2.a < /dev/null &
ffmpeg -i input1.mp4 -an  -r 30 -s vga -b 512k -f yuv4mpegpipe - >
temp1.v < /dev/null &
ffmpeg -i input2.flv -an  -r 30 -s vga -b 512k -f yuv4mpegpipe - >
temp2.v < /dev/null &
cat temp1.a temp2.a > all.a &
cat temp1.v temp2.v > all.v &
ffmpeg -f u16le -acodec pcm_s16le -ac 2 -ar 44100 -i all.a \
      -f yuv4mpegpipe -i all.v \
      -sameq -y output.flv
rm temp[12].[av] all.[av]

But that doesn't work either. Any idea what I can do???

-s




FFmpeg version SVN-r19931, Copyright (c) 2000-2009 Fabrice Bellard, et al.
 configuration: --enable-gpl --enable-nonfree --enable-pthreads
--enable-libfaac --enable-libfaad --enable-libmp3lame
--enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
 libavutil     50. 3. 0 / 50. 3. 0
 libavcodec    52.35. 0 / 52.35. 0
 libavformat   52.38. 0 / 52.38. 0
 libavdevice   52. 2. 0 / 52. 2. 0
 libswscale     0. 7. 1 /  0. 7. 1
 built on Sep 20 2009 11:21:22, gcc: 4.3.2
FFmpeg version SVN-r19931, Copyright (c) 2000-2009 Fabrice Bellard, et al.
 configuration: --enable-gpl --enable-nonfree --enable-pthreads
--enable-libfaac --enable-libfaad --enable-libmp3lame
--enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
 libavutil     50. 3. 0 / 50. 3. 0
 libavcodec    52.35. 0 / 52.35. 0
 libavformat   52.38. 0 / 52.38. 0
 libavdevice   52. 2. 0 / 52. 2. 0
 libswscale     0. 7. 1 /  0. 7. 1
 built on Sep 20 2009 11:21:22, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate:
60.00 (60/1) -> 30.00 (30/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/ubuntu/preroll2.mp4':
 Duration: 00:00:05.03, start: 0.000000, bitrate: 456 kb/s
   Stream #0.0(eng): Video: h264, yuv420p, 640x480 [PAR 1:1 DAR 4:3],
30 tbr, 30 tbn, 60 tbc
   Stream #0.1(eng): Audio: aac, 44100 Hz, 2 channels, s16
 Metadata
   muxer           : Lavf52.38.0
Output #0, u16le, to 'pipe:':
   Stream #0.0(eng): Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
 Stream #0.1 -> #0.0
Press [q] to stop encoding
Input #0, u16le, from '/tmp/all.a':
 Duration: N/A, start: 0.000000, bitrate: N/A
   Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
FFmpeg version SVN-r19931, Copyright (c) 2000-2009 Fabrice Bellard, et al.
 configuration: --enable-gpl --enable-nonfree --enable-pthreads
--enable-libfaac --enable-libfaad --enable-libmp3lame
--enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
 libavutil     50. 3. 0 / 50. 3. 0
 libavcodec    52.35. 0 / 52.35. 0
 libavformat   52.38. 0 / 52.38. 0
 libavdevice   52. 2. 0 / 52. 2. 0
 libswscale     0. 7. 1 /  0. 7. 1
 built on Sep 20 2009 11:21:22, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate:
60.00 (60/1) -> 30.00 (30/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/ubuntu/preroll2.mp4':
 Duration: 00:00:05.03, start: 0.000000, bitrate: 456 kb/s
   Stream #0.0(eng): Video: h264, yuv420p, 640x480 [PAR 1:1 DAR 4:3],
30 tbr, 30 tbn, 60 tbc
   Stream #0.1(eng): Audio: aac, 44100 Hz, 2 channels, s16
 Metadata
   muxer           : Lavf52.38.0
Output #0, yuv4mpegpipe, to 'pipe:':
   Stream #0.0(eng): Video: rawvideo, yuv420p, 640x480 [PAR 1:1 DAR
4:3], q=2-31, 512 kb/s, 90k tbn, 30 tbc
Stream mapping:
 Stream #0.0 -> #0.0
Press [q] to stop encoding
[yuv4mpegpipe @ 0x953aab0]MAX_READ_SIZE:5000000 reached
Input #1, yuv4mpegpipe, from '/tmp/all.y4m':
 Duration: N/A, bitrate: N/A
   Stream #1.0: Video: rawvideo, yuv420p, 640x480, PAR 1:1 DAR 4:3,
30 tbr, 30 tbn, 30 tbc
Output #0, flv, to '/www/live/Application/ServerSide/webroot/final.flv':
   Stream #0.0: Video: flv, yuv420p, 640x480 [PAR 1:1 DAR 4:3],
q=2-31, 200 kb/s, 1k tbn, 30 tbc
   Stream #0.1: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
 Stream #1.0 -> #0.0
 Stream #0.0 -> #0.1
Press [q] to stop encoding
size=     856kB time=4.97 bitrate=1411.2kbits/s     bitrate=1529.0kbits/s
video:0kB audio:856kB global headers:0kB muxing overhead 0.000000%
FFmpeg version SVN-r19931, Copyright (c) 2000-2009 Fabrice Bellard, et al.
 configuration: --enable-gpl --enable-nonfree --enable-pthreads
--enable-libfaac --enable-libfaad --enable-libmp3lame
--enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
 libavutil     50. 3. 0 / 50. 3. 0
 libavcodec    52.35. 0 / 52.35. 0
 libavformat   52.38. 0 / 52.38. 0
 libavdevice   52. 2. 0 / 52. 2. 0
 libswscale     0. 7. 1 /  0. 7. 1
 built on Sep 20 2009 11:21:22, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate:
59.94 (60000/1001) -> 30.00 (30/1)
Input #0, flv, from
'/mnt/tmp/5minWatermark/34-44-41c8c92ba34eec1e6bbfacada30c3254.flv':
 Duration: 00:04:15.25, start: 0.066000, bitrate: 512 kb/s
   Stream #0.0: Video: h264, yuv420p, 640x480, 512 kb/s, 30 tbr, 1k
tbn, 59.94 tbc
   Stream #0.1: Audio: aac, 48000 Hz, 2 channels, s16
 Metadata
   duration        : 255
   width           : 640
   height          : 480
   videodatarate   : 500
   framerate       : 30
   videocodecid    : 7
   audiodatarate   : 0
   audiosamplerate : 48000
   audiosamplesize : 16
   stereo          : true
   audiocodecid    : 10
   filesize        : 20836753
Output #0, u16le, to 'pipe:':
   Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
 Stream #0.1 -> #0.0
Press [q] to stop encoding
frame=  150 fps=115 q=0.0 Lsize=   67501kB time=5.00 bitrate=110593.5kbits/s
video:0kB audio:0kB global headers:0kB muxing overhead inf%
FFmpeg version SVN-r19931, Copyright (c) 2000-2009 Fabrice Bellard, et al.
 configuration: --enable-gpl --enable-nonfree --enable-pthreads
--enable-libfaac --enable-libfaad --enable-libmp3lame
--enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
 libavutil     50. 3. 0 / 50. 3. 0
 libavcodec    52.35. 0 / 52.35. 0
 libavformat   52.38. 0 / 52.38. 0
 libavdevice   52. 2. 0 / 52. 2. 0
 libswscale     0. 7. 1 /  0. 7. 1
 built on Sep 20 2009 11:21:22, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate:
59.94 (60000/1001) -> 30.00 (30/1)
Input #0, flv, from
'/mnt/tmp/5minWatermark/34-44-41c8c92ba34eec1e6bbfacada30c3254.flv':
 Duration: 00:04:15.25, start: 0.066000, bitrate: 512 kb/s
   Stream #0.0: Video: h264, yuv420p, 640x480, 512 kb/s, 30 tbr, 1k
tbn, 59.94 tbc
   Stream #0.1: Audio: aac, 48000 Hz, 2 channels, s16
 Metadata
   duration        : 255
   width           : 640
   height          : 480
   videodatarate   : 500
   framerate       : 30
   videocodecid    : 7
   audiodatarate   : 0
   audiosamplerate : 48000
   audiosamplesize : 16
   stereo          : true
   audiocodecid    : 10
   filesize        : 20836753
Output #0, yuv4mpegpipe, to 'pipe:':
   Stream #0.0: Video: rawvideo, yuv420p, 640x480, q=2-31, 512 kb/s,
90k tbn, 30 tbc
Stream mapping:
 Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   43957kB time=255.17 bitrate=1411.2kbits/s    itrate=1329.8kbits/s
video:0kB audio:43957kB global headers:0kB muxing overhead 0.000000%
frame=  150 fps= 11 q=0.0 Lsize=    2958kB time=5.00 bitrate=4846.7kbits/s
video:767kB audio:2033kB global headers:0kB muxing overhead 5.652848%

---

