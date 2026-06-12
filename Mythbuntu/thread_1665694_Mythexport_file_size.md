---
title: "Mythexport file size"
date: 2011-01-12
forum: Mythbuntu
---

### Post by rburt on 2011-01-12
I'm having a problem with mythexport file size when trying to export to an iPod compatible file.  Everything was working a couple of months ago, but something has changed and I'm not sure what.  I'm still on .23.1 and have enabled medibuntu for AAC.
If I run the PortableH264LowRes config against a 1280x720 mpeg2 file that is _**4.9GB**_ in size, I end up with a 480x320 h.264 file that is _**4.9GB**_.  In the past it would have been less than 500 MB.
I'm attaching a snippet from my mythexport.log.
Can anyone see what's going on?  Or give me some troubleshooting ideas?
I can't fit a 5GB TV show on my iPod.
Thanks.
```

FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavdevice configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mpegts, from '/recordings1/2217_20100704190000.mpg':
  Duration: 00:59:56.88, start: 87825.776611, bitrate: 11989 kb/s
  Program 1
    Stream #0.0[0xf61]: Video: mpeg2video, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 20000 kb/s, 59.96 fps, 59.94 tbr, 90k tbn, 119.88 tbc
    Stream #0.1[0xf62](eng): Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s
[libx264 @ 0x9be120]max bitrate less than average bitrate, assuming CBR
[libx264 @ 0x9be120]using SAR=32/27
[libx264 @ 0x9be120]frame MB size (30x20) > level limit (396)
[libx264 @ 0x9be120]VBV bitrate (1500) > level limit (768)
[libx264 @ 0x9be120]VBV buffer (3000) > level limit (2000)
[libx264 @ 0x9be120]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x9be120]profile Baseline, level 1.3
[libx264 @ 0x9be120]264 - core 98 Ubuntu_2:0.98.1653+git88b90d9-3ubuntu1 - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=cbr mbtree=1 bitrate=1500 ratetol=0.7 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 vbv_maxrate=1500 vbv_bufsize=3000 ip_ratio=1.41 aq=1:1.00 nal_hrd=none
Output #0, ipod, to '/var/lib/mythtv/HSTRYHD-America_the_Story_of_Us-Millennium-20100704190000.m4v':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 1, 1500 kb/s, 60k tbn, 59.94 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[mpeg2video @ 0x9bcd50]Warning MVs not available990.82 bitrate=12885.6kbits/s dup=22 drop=0
[mpeg2video @ 0x9bcd50]concealing 80 DC, 80 AC, 80 MV errors
    Last message repeated 1 times1558776kB time=991.21 bitrate=12882.8kbits/s dup=22 drop=0
[mpeg2video @ 0x9bcd50]warning: first frame is no keyframe
    Last message repeated 1 times 3304739kB time=2392.76 bitrate=11314.3kbits/s dup=25 drop=0
[mpeg2video @ 0x9bcd50]Warning MVs not available
[mpeg2video @ 0x9bcd50]concealing 80 DC, 80 AC, 80 MV errors
    Last message repeated 1 times 3718285kB time=2652.48 bitrate=11483.7kbits/s dup=26 drop=0
[mpeg2video @ 0x9bcd50]mb incr damaged
[mpeg2video @ 0x9bcd50]Warning MVs not available
[mpeg2video @ 0x9bcd50]concealing 80 DC, 80 AC, 80 MV errors
[mpeg2video @ 0x9bcd50]Warning MVs not available=3300.73 bitrate=11873.0kbits/s dup=26 drop=0
[mpeg2video @ 0x9bcd50]concealing 160 DC, 160 AC, 160 MV errors
[mpeg2video @ 0x9bcd50]concealing 31 DC, 31 AC, 31 MV errorsrate=11761.5kbits/s dup=26 drop=0
[mpeg2video @ 0x9bcd50]ac-tex damaged at 23 37me=3596.09 bitrate=11788.3kbits/s dup=26 drop=0
[mpeg2video @ 0x9bcd50]concealing 640 DC, 640 AC, 640 MV errors
frame=215601 fps= 50 q=-1.0 Lsize= 5178521kB time=3596.94 bitrate=11794.0kbits/s dup=26 drop=0
video:5175987kB audio:0kB global headers:0kB muxing overhead 0.048946%
[libx264 @ 0x9be120]frame I:1585  Avg QP:10.23  size: 47557
[libx264 @ 0x9be120]frame P:214016 Avg QP:10.23  size: 24413
[libx264 @ 0x9be120]mb I  I16..4: 18.8%  0.0% 81.2%
[libx264 @ 0x9be120]mb P  I16..4:  2.3%  0.0% 11.6%  P16..4: 40.1% 22.1% 15.8%  0.0%  0.0%    skip: 8.0%
[libx264 @ 0x9be120]coded y,uvDC,uvAC intra: 96.2% 94.9% 94.3% inter: 74.4% 55.0% 52.0%
[libx264 @ 0x9be120]i16 v,h,dc,p: 19% 13% 13% 55%
[libx264 @ 0x9be120]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 21% 18% 14%  6%  8%  9%  8%  8%  8%
[libx264 @ 0x9be120]i8c dc,h,v,p: 54% 18% 18% 10%
[libx264 @ 0x9be120]kb/s:196.67
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavdevice configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6-2ubuntu3+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mpegts, from '/recordings1/2217_20100704190000.mpg':
  Duration: 00:59:56.88, start: 87825.776611, bitrate: 11989 kb/s
  Program 1
    Stream #0.0[0xf61]: Video: mpeg2video, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 20000 kb/s, 59.96 fps, 59.94 tbr, 90k tbn, 119.88 tbc
    Stream #0.1[0xf62](eng): Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s
[libx264 @ 0x2167130]max bitrate less than average bitrate, assuming CBR
[libx264 @ 0x2167130]using SAR=32/27
[libx264 @ 0x2167130]frame MB size (30x20) > level limit (396)
[libx264 @ 0x2167130]DPB size (4 frames, 921600 bytes) > level limit (3 frames, 912384 bytes)
[libx264 @ 0x2167130]VBV bitrate (1500) > level limit (768)
[libx264 @ 0x2167130]VBV buffer (3000) > level limit (2000)
[libx264 @ 0x2167130]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x2167130]target: 1500.00 kbit/s, expected: 196.69 kbit/s, avg QP: 10.0000
[libx264 @ 0x2167130]try reducing target bitrate or reducing qp_min (currently 10)
[libx264 @ 0x2167130]profile Baseline, level 1.3
[libx264 @ 0x2167130]264 - core 98 Ubuntu_2:0.98.1653+git88b90d9-3ubuntu1 - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=0 ref=4 deblock=1:0:0 analyse=0x1:0x111 me=umh subme=8 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=2pass mbtree=1 bitrate=1500 ratetol=0.7 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 cplxblur=20.0 qblur=0.5 vbv_maxrate=1500 vbv_bufsize=3000 ip_ratio=1.41 aq=1:1.00 nal_hrd=none
Output #0, ipod, to '/var/lib/mythtv/HSTRYHD-America_the_Story_of_Us-Millennium-20100704190000.m4v':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 2, 1500 kb/s, 60k tbn, 59.94 tbc
    Stream #0.1(eng): Audio: libfaac, 48000 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[mpeg2video @ 0x2165d50]Warning MVs not available91.30 bitrate=12824.6kbits/s dup=22 drop=0
[mpeg2video @ 0x2165d50]concealing 80 DC, 80 AC, 80 MV errors
    Last message repeated 1 times
[mpeg2video @ 0x2165d50]warning: first frame is no keyframe
    Last message repeated 1 times 3303956kB time=2392.92 bitrate=11310.9kbits/s dup=25 drop=0
[mpeg2video @ 0x2165d50]Warning MVs not available
[mpeg2video @ 0x2165d50]concealing 80 DC, 80 AC, 80 MV errors
    Last message repeated 1 times 3713638kB time=2652.63 bitrate=11468.7kbits/s dup=26 drop=0
[mpeg2video @ 0x2165d50]mb incr damaged
[mpeg2video @ 0x2165d50]Warning MVs not available
[mpeg2video @ 0x2165d50]concealing 80 DC, 80 AC, 80 MV errors
[mpeg2video @ 0x2165d50]Warning MVs not available3301.06 bitrate=11813.9kbits/s dup=26 drop=0
[mpeg2video @ 0x2165d50]concealing 160 DC, 160 AC, 160 MV errors
[mpeg2video @ 0x2165d50]concealing 31 DC, 31 AC, 31 MV errorsate=11702.1kbits/s dup=26 drop=0
[mpeg2video @ 0x2165d50]ac-tex damaged at 23 37e=3596.31 bitrate=11725.7kbits/s dup=26 drop=0
[mpeg2video @ 0x2165d50]concealing 640 DC, 640 AC, 640 MV errors
[ac3 @ 0x2166590]incomplete frame
frame=215601 fps= 31 q=-1.0 Lsize= 5153043kB time=3596.42 bitrate=11737.7kbits/s dup=26 drop=0
video:5075911kB audio:72623kB global headers:0kB muxing overhead 0.087587%
[libx264 @ 0x2167130]frame I:1585  Avg QP:10.23  size: 49274
[libx264 @ 0x2167130]frame P:214016 Avg QP:10.23  size: 23922
[libx264 @ 0x2167130]mb I  I16..4: 18.9%  0.0% 81.1%
[libx264 @ 0x2167130]mb P  I16..4:  1.8%  0.0%  9.5%  P16..4: 36.6% 24.4% 19.7%  0.0%  0.0%    skip: 8.1%
[libx264 @ 0x2167130]coded y,uvDC,uvAC intra: 96.4% 95.0% 94.4% inter: 72.9% 54.5% 51.5%
[libx264 @ 0x2167130]i16 v,h,dc,p: 20% 13% 10% 57%
[libx264 @ 0x2167130]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 14% 13%  8%  9% 12% 12% 11% 11% 11%
[libx264 @ 0x2167130]i8c dc,h,v,p: 59% 16% 16%  8%
[libx264 @ 0x2167130]ref P L0: 76.8% 14.1%  6.6%  2.4%
[libx264 @ 0x2167130]kb/s:192.86


```

---

### Post by ian dobson on 2011-01-13
Hi 

I think this should be a big tip

**WARNING: library configuration mismatch**

Looks as if ffmpeg has a problem, not sure what but that looks like the smoking gun. Have a look here [http://ubuntuforums.org/showthread.php?t=1553321](http://ubuntuforums.org/showthread.php?t=1553321) or maybe here [http://ubuntuforums.org/showthread.php?t=1472308](http://ubuntuforums.org/showthread.php?t=1472308) that might help.

Regards
Ian Dobson

---

### Post by rburt on 2011-01-16
Just wanted to close the loop on this.
The problem seems to have been related to this bug in the x264 library that was reverted:
[https://bugs.launchpad.net/ubuntu/+source/x264/+bug/690296](https://bugs.launchpad.net/ubuntu/+source/x264/+bug/690296)

After performing an apt-get upgrade:
Exporting a file that last week resulted in a 4.9GB file, now exports a 700MB file.

---

