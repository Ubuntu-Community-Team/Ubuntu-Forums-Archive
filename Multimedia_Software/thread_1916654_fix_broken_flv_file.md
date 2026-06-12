---
title: "fix broken flv file"
date: 2012-01-28
forum: Multimedia Software
---

### Post by mungatsuma on 2012-01-28
I have this problem with a particular .flv video which can only play in GOM media player in windows 7. I would like to convert it to AVI format, but the result will not play. Stops after five minutes playback. When I play in terminal this is what i get.
> nicholas@nicholas-Aspire-5551:/media/2F06-D9A1/Videos/Videos$ cvlc 'Fearless.flv'
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x16d6af0] dummy interface: using the dummy interface module...
error while decoding MB 23 20, bytestream (-4)
slice type too large (2) at 23 20
decode_slice_header errorI tried converting it and i get this output
> 
nicholas@nicholas-Aspire-5551:/media/2F06-D9A1/Videos/Videos$ ffmpeg -i "Fearless.flv" "Fearless.avi"
FFmpeg version SVN-r26402, Copyright (c) 2000-2011 the FFmpeg developers
  built on Nov 21 2011 02:09:55 with gcc 4.6.1
  configuration: --enable-libmp3lame --enable-libvorbis --disable-mmx --enable-shared --enable-version3 --enable-nonfree --enable-libtheora
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 1 /  0.16. 1
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.93. 0 / 52.93. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.74. 0 /  1.74. 0
  libswscale     0.12. 0 /  0.12. 0
[flv @ 0x261f510] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'Fearless.flv':
  Metadata:
    duration        : 6186
    starttime       : 33
    totalduration   : 6219
    width           : 480
    height          : 350
    videodatarate   : 333
    audiodatarate   : 97
    totaldatarate   : 437
    framerate       : 24
    bytelength      : 338848879
    canseekontime   : true
    sourcedata      : BADC20583MH1295382880074985
    purl            : 
    pmsg            : 
  Duration: 01:43:05.78, start: 33.135000, bitrate: 439 kb/s
    Stream #0.0: Video: h264, yuv420p, 480x350 [PAR 1:1 DAR 48:35], 340 kb/s, 24 tbr, 1k tbn, 48 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 98 kb/s
[buffer @ 0x2632a30] w:480 h:350 pixfmt:yuv420p
Output #0, avi, to 'Fearless.avi':
  Metadata:
    duration        : 6186
    starttime       : 33
    totalduration   : 6219
    width           : 480
    height          : 350
    videodatarate   : 333
    audiodatarate   : 97
    totaldatarate   : 437
    framerate       : 24
    bytelength      : 338848879
    canseekontime   : true
    sourcedata      : BADC20583MH1295382880074985
    purl            : 
    pmsg            : 
    ISFT            : Lavf52.93.0
    Stream #0.0: Video: mpeg4, yuv420p, 480x350 [PAR 1:1 DAR 48:35], q=2-31, 200 kb/s, 24 tbn, 24 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 2403 fps= 37 q=25.3 size=    3458kB time=100.21 bitrate= 282.7kbits/s   frame= 2422 fps= 37 q=28.1 size=    3482kB time=100.99 bitrate= 282.5kbits/s   
......................
frame= 5223 fps= 34 q=31.0 size=    7679kB time=217.81 bitrate= 288.8kbits/s   frame= 5241 fps= 34 q=31.0 size=    7701kB time=218.59 bitrate= 288.6kbits/s    frame= 6302 fps= 34 q=31.0 size=    9340kB time=262.82 bitrate= 291.1kbits/s   frame= 6322 fps= 34 q=24.8 size=    9366kB time=263.65 bitrate= 291.0kbits/s   [h264 @ 0x2621eb0] error while decoding MB 23 20, bytestream (-4)
[h264 @ 0x2621eb0] slice type too large (2) at 23 20
[h264 @ 0x2621eb0] decode_slice_header error
[h264 @ 0x2621eb0] concealing 86 DC, 86 AC, 86 MV errors
frame= 6334 fps= 34 q=24.8 Lsize=    9637kB time=264.18 bitrate= 298.9kbits/s    
video:7165kB audio:2064kB global headers:0kB muxing overhead 4.422979%
nicholas@nicholas-Aspire-5551:/media/2F06-D9A1/Videos/Videos$  I have cut the middle part where the periods are to reduce the text size.

How can it be fixed since it plays in GOM media player.

---

### Post by andrew.46 on 2012-01-29
Bear in mind that Forum's rules discourage downloading from youtube. But I am sure we can talk in general terms about a ?broken flv :). Is there a special reason you wish to change container and codecs? You can see from the FFmpeg output that you are changing from h264 video and aac sound to mpeg4 video and mp2 sound, a downgrade in anybody's terms. Can you upload the original somewhere?

---

### Post by mungatsuma on 2012-01-29
There is a reason, to watch the said video on my home dvd player, which does not support flv videos.

---

### Post by FakeOutdoorsman on 2012-01-29
> **mungatsuma said:**
> FFmpeg version SVN-r26402, Copyright (c) 2000-2011 the FFmpeg developers
It appears that you compiled FFmpeg yourself. This first thing I would try is a newer version. There have been at least 10,000 revisions since your version and perhaps may improve H.264 decoding.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

> **mungatsuma said:**
> configuration: --enable-libmp3lame --enable-libvorbis --disable-mmx --enable-shared --enable-version3 --enable-nonfree --enable-libtheora
Is there a particular reason to *--disable-mmx*? This option will probably result in decreased encoding speed for some encoders.

Also, I recommend editing your post to avoid the thread closers who are often zealous about a particular forbidden word.

---

### Post by mungatsuma on 2012-02-03
Thank you @FakeOutdoorsman. Followed your earlier post and reinstalled ffmpeg, but I still get errors when I try to convert. This is the output;

> nicholas@nicholas-Aspire-5551:~/Videos$ ffmpeg -i Fearless.flv -acodec libfaac -aq 100 -vcodec libx264 -preset slow -crf 22 fearless.mp4
ffmpeg version git-2012-02-03-d77294c Copyright (c) 2000-2012 the FFmpeg developers
  built on Feb  3 2012 20:20:55 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab --enable-libvpx
  libavutil      51. 37.100 / 51. 37.100
  libavcodec     54.  0.102 / 54.  0.102
  libavformat    54.  0.100 / 54.  0.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, flv, from 'Fearless.flv':
  Metadata:
    starttime       : 33
    totalduration   : 6219
    totaldatarate   : 437
    bytelength      : 338848879
    canseekontime   : true
    sourcedata      : BADC20583MH1295382880074985
    purl            : 
    pmsg            : 
  Duration: 01:43:05.78, start: 33.135000, bitrate: 438 kb/s
    Stream #0:0: Video: h264 (Main), yuv420p, 480x350 [SAR 1:1 DAR 48:35], 340 kb/s, 24 tbr, 1k tbn, 48 tbc
    Stream #0:1: Audio: aac, 44100 Hz, stereo, s16, 98 kb/s
File 'fearless.mp4' already exists. Overwrite ? [y/N] y
And after that;
> purl            : 
    pmsg            : 
    encoder         : Lavf54.0.100
    Stream #0:0: Video: h264 (![0][0][0] / 0x0021), yuv420p, 480x350 [SAR 1:1 DAR 48:35], q=-1--1, 24 tbn, 24 tbc
    Stream #0:1: Audio: aac (@[0][0][0] / 0x0040), 44100 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libx264)
  Stream #0:1 -> #0:1 (aac -> libfaac)
Press [q] to stop, [?] for help
frame=   62 fps=  0 q=27.0 size=      11kB time=00:00:00.12 bitrate= 751.1kbits/frame=   86 fps= 83 q=27.0 size=      57kB time=00:00:01.12 bitrate= 413.9kbits/frame=   98 fps= 63 q=27.0 size=      90kB time=00:00:01.62 bitrate= 451.3kbits/frame=  107 fps= 52 q=27.0 size=     133kB time=00:00:02.00 bitrate= 544.3kbits/frame=  119 fps= 46 q=27.0 size=     187kB time=00:00:02.50 bitrate= 611.8kbits/frame=  131 fps= 42 q=27.0 size=     227kB time=00:00:03.00 bitrate= 619.7kbits/frame=  140 fps= 39 q=27.0 size=     260kB time=00:00:03.37 bitrate= 630.5kbits/frame=  152 fps= 37 q=27.0 size=     295kB time=00:00:03.87 bitrate= 624.6kbits/.....................
............................20525kB time=00:04:20.58 bitrate= 645.3kbits/frame= 6326 fps= 26 q=27.0 size=   20567kB time=00:04:21.12 bitrate= 645.2kbits/frame= 6336 fps= 26 q=27.0 size=   20609kB time=00:04:21.54 bitrate= 645.5kbits/error while decoding MB 23 20, bytestream (-6)
[h264 @ 0x2ebbf40] slice type too large (2) at 23 20
[h264 @ 0x2ebbf40] decode_slice_header error
[h264 @ 0x2ebbf40] concealing 86 DC, 86 AC, 86 MV errors
[flv @ 0x263c3e0] Stream discovered after head already parsed
frame= 6340 fps= 25 q=-1.0 Lsize=   20989kB time=00:04:24.08 bitrate= 651.1kbits/s dup=6 drop=0    
video:17160kB audio:3635kB global headers:0kB muxing overhead 0.933778%
[libx264 @ 0x263cf20] frame I:110   Avg QP:18.72  size: 11290
[libx264 @ 0x263cf20] frame P:2731  Avg QP:22.95  size:  3636
[libx264 @ 0x263cf20] frame B:3499  Avg QP:26.98  size:  1829
[libx264 @ 0x263cf20] consecutive B-frames: 19.7% 10.6% 28.9% 40.8%
[libx264 @ 0x263cf20] mb I  I16..4: 11.5% 41.8% 46.7%
[libx264 @ 0x263cf20] mb P  I16..4:  4.1% 10.4%  5.0%  P16..4: 33.9% 14.8%  5.7%  0.0%  0.0%    skip:26.0%
[libx264 @ 0x263cf20] mb B  I16..4:  0.8%  2.4%  2.5%  B16..8: 42.0% 10.0%  2.0%  direct: 1.8%  skip:38.4%  L0:55.0% L1:38.9% BI: 6.1%
[libx264 @ 0x263cf20] 8x8 transform intra:49.3% inter:64.2%
[libx264 @ 0x263cf20] direct mvs  spatial:99.0% temporal:1.0%
[libx264 @ 0x263cf20] coded y,uvDC,uvAC intra: 65.0% 50.1% 9.1% inter: 15.3% 14.0% 0.1%
[libx264 @ 0x263cf20] i16 v,h,dc,p: 35% 30% 12% 23%
[libx264 @ 0x263cf20] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 19% 18% 12%  6%  7%  9%  9%  8% 12%
[libx264 @ 0x263cf20] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 19% 18% 10%  6% 10% 10% 10%  8% 10%
[libx264 @ 0x263cf20] i8c dc,h,v,p: 59% 20% 15%  6%
[libx264 @ 0x263cf20] Weighted P-Frames: Y:4.1% UV:1.5%
[libx264 @ 0x263cf20] ref P L0: 73.4%  9.0% 12.0%  2.8%  1.9%  0.9%  0.0%
[libx264 @ 0x263cf20] ref B L0: 90.6%  7.0%  1.8%  0.5%
[libx264 @ 0x263cf20] ref B L1: 96.6%  3.4%
[libx264 @ 0x263cf20] kb/s:532.13
nicholas@nicholas-Aspire-5551:~/Videos$ 
So still no way forward.

---

