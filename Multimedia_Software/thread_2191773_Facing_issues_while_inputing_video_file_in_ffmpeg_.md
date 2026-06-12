---
title: "Facing issues while inputing video file in ffmpeg code"
date: 2013-12-04
forum: Multimedia Software
---

### Post by vswapnasr on 2013-12-04
Hi,
I downloade and configured x264 by using
git clone git://git.videolan.org/x264
./configure --enable-shared --prefix=/home/path/ffmlib/
make 
make install
and also ffmpeg with
./configure --enable-shared --enable-gpl --enable-libx264 --prefix=/home/path/ffmlib/
make
make install
Finally while giving input file like

./ffmpeg -f rawvideo -r 50 -s 416x240 -vcodec rawvideo -i BasketballPass_416x240_50.yuv -c:v libx264 -intra -qp 9 out.h264


Its not linking libx264 library properly and also if i write any printf in the code its not printing anything..

Output displaying error:Opening filter

avutil      configuration: --enable-libx264 --enable-shared --enable-gpl
  avformat    configuration: --enable-libx264 --enable-shared --enable-gpl
  avdevice    configuration: --enable-libx264 --enable-shared --enable-gpl
  avfilter    configuration: --enable-libx264 --enable-shared --enable-gpl
  swscale     configuration: --enable-libx264 --enable-shared --enable-gpl
  swresample  configuration: --enable-libx264 --enable-shared --enable-gpl
  postproc    configuration: --enable-libx264 --enable-shared --enable-gpl
  libavutil      52. 46.101 / 52. 48.100
  libavcodec     55. 36.100 / 55. 36.100
  libavformat    55. 19.102 / 55. 19.104
  libavdevice    55.  4.100 / 55.  5.100
  libavfilter     3. 88.101 /  3. 90.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.103 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
GOING INSIDE AVCODEC_opn2 in utils.c..[rawvideo @ 0x21c7b20] Estimating duration from bitrate, this may be inaccurate
Input #0, rawvideo, from 'BasketballPass_416x240_50.yuv':
  Duration: 00:00:10.02, start: 0.000000, bitrate: 59904 kb/s
    Stream #0:0: Video: rawvideo (I420 / 0x30323449), yuv420p, 416x240, 59904 kb/s, 50 tbr, 50 tbn, 50 tbc
[AVFilterGraph @ 0x21b8760] Error initializing threading.
[AVFilterGraph @ 0x21b8760] Error creating filter 'null'
Error opening filters!

---

