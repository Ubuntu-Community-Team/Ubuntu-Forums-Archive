---
title: "Transcoding speed"
date: 2010-03-10
forum: Multimedia Software
---

### Post by aflores3 on 2010-03-10
I recently got a dell server: 16 gigs of RAM, dual quad-core processors, 6 disk raid. 

My question is, when I transcode video, I can normally only transcode at 70 frames/sec max, regardless of the method I use (mencoder or ffmpeg). Should this run faster? Am I missing something? What other information do you need to help diagnose?

Thanks.

---

### Post by FakeOutdoorsman on 2010-03-10
What version of Ubuntu are you using?  Is this 32 or 64-bit?  What is the FFmpeg command and complete FFmpeg output?  For comparison re-encoding an [Iron Man](http://mirror05.x264.nl/Dark/x264clips/IronMan.mkv) test clip (720p, 1:48 duration):
```
$ time ffmpeg -i IronMan.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre slow -crf 20 -threads 0 output.mp4
FFmpeg version SVN-r22368, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar  8 2010 16:32:17 with gcc 4.4.3
  configuration: --prefix=/usr/local --enable-nonfree --enable-gpl --enable-version3 --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-pthreads --enable-x11grab
  libavutil     50.11. 0 / 50.11. 0
  libavcodec    52.58. 0 / 52.58. 0
  libavformat   52.55. 0 / 52.55. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
[matroska @ 0x13623c0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (10000000/208541) -> 24.00 (24/1)
Input #0, matroska, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 24.39 fps, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
[libx264 @ 0x1411820]using SAR=115/87
[libx264 @ 0x1411820]using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x1411820]profile High, level 3.1
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf52.55.0
    Stream #0.0: Video: libx264, yuv420p, 1280x720 [PAR 115:87 DAR 1840:783], q=10-51, 200 kb/s, 24 tbn, 24 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 2599 fps= 17 q=-1.0 Lsize=   73048kB time=108.33 bitrate=5523.8kbits/s dup=0 drop=1    
video:70777kB audio:2191kB global headers:0kB muxing overhead 0.109766%
[libx264 @ 0x1411820]frame I:44    Avg QP:18.56  size:106649
[libx264 @ 0x1411820]frame P:1049  Avg QP:21.70  size: 34854
[libx264 @ 0x1411820]frame B:1506  Avg QP:23.79  size: 20731
[libx264 @ 0x1411820]consecutive B-frames: 11.3% 21.1% 27.8% 39.8%
[libx264 @ 0x1411820]mb I  I16..4:  5.2% 81.6% 13.2%
[libx264 @ 0x1411820]mb P  I16..4:  8.6% 41.4%  2.8%  P16..4: 28.1%  9.9%  5.2%  0.0%  0.0%    skip: 4.0%
[libx264 @ 0x1411820]mb B  I16..4:  1.8% 14.0%  1.3%  B16..8: 44.9%  2.9%  2.7%  direct: 6.7%  skip:25.7%  L0:46.2% L1:45.5% BI: 8.3%
[libx264 @ 0x1411820]8x8 transform intra:79.6% inter:77.0%
[libx264 @ 0x1411820]direct mvs  spatial:99.5% temporal:0.5%
[libx264 @ 0x1411820]coded y,uvDC,uvAC intra: 70.0% 83.9% 36.7% inter: 31.9% 32.0% 2.2%
[libx264 @ 0x1411820]i16 v,h,dc,p: 25% 13%  8% 53%
[libx264 @ 0x1411820]i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 12%  7%  7%  9% 14% 16% 12% 13% 11%
[libx264 @ 0x1411820]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 14%  7%  6%  9% 15% 16% 12% 11% 10%
[libx264 @ 0x1411820]Weighted P-Frames: Y:1.3%
[libx264 @ 0x1411820]ref P L0: 59.1% 17.1%  9.9%  7.4%  5.1%  1.4%  0.0%
[libx264 @ 0x1411820]ref B L0: 77.4% 15.1%  6.1%  1.4%
[libx264 @ 0x1411820]ref B L1: 95.1%  4.9%
[libx264 @ 0x1411820]kb/s:5354.04

real	[color=#FF0000]2m37.882s[/color]
user	17m59.996s
sys	0m26.325s
```
With the above FFmpeg command using the *slow* preset I am getting an average of about 16.5 fps.  With the ultrafast preset I get ~104 fps.  This is using Arch Linux 64-bit, 8 GB RAM, i7 860 CPU with a compiled x264 and FFmpeg as shown here:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by aflores3 on 2010-03-10
Faker,
I appreciate your willingness to help.

I am running Mythbuntu 9.10 64 bit with two of these: [http://products.amd.com/en-US/OpteronCPUDetail.aspx?id=415](http://products.amd.com/en-US/OpteronCPUDetail.aspx?id=415)

I downloaded your comparison file, compiled x264 and FFmpeg as per the tutorial, and this is what I got

```
$ time ffmpeg -i IronMan.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre slow -crf 20 -threads 0 output.mp4
FFmpeg version SVN-r22437, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 10 2010 16:07:20 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.11. 0 / 50.11. 0
  libavcodec    52.58. 0 / 52.58. 0
  libavformat   52.55. 0 / 52.55. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x14853c0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (10000000/208541) -> 24.00 (24/1)
Input #0, matroska, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 24.39 fps, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
[libx264 @ 0x14d65a0]using SAR=115/87
[libx264 @ 0x14d65a0]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x14d65a0]profile High, level 3.1
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf52.55.0
    Stream #0.0: Video: libx264, yuv420p, 1280x720 [PAR 115:87 DAR 1840:783], q=10-51, 200 kb/s, 24 tbn, 24 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 2599 fps= 11 q=-1.0 Lsize=   73048kB time=108.33 bitrate=5523.8kbits/s dup=0 drop=1    
video:70777kB audio:2191kB global headers:0kB muxing overhead 0.109766%
[libx264 @ 0x14d65a0]frame I:44    Avg QP:18.56  size:106649
[libx264 @ 0x14d65a0]frame P:1049  Avg QP:21.70  size: 34854
[libx264 @ 0x14d65a0]frame B:1506  Avg QP:23.79  size: 20731
[libx264 @ 0x14d65a0]consecutive B-frames: 11.3% 21.1% 27.8% 39.8%
[libx264 @ 0x14d65a0]mb I  I16..4:  5.2% 81.6% 13.2%
[libx264 @ 0x14d65a0]mb P  I16..4:  8.6% 41.4%  2.8%  P16..4: 28.1%  9.9%  5.2%  0.0%  0.0%    skip: 4.0%
[libx264 @ 0x14d65a0]mb B  I16..4:  1.8% 14.0%  1.3%  B16..8: 44.9%  2.9%  2.7%  direct: 6.7%  skip:25.7%  L0:46.2% L1:45.5% BI: 8.3%
[libx264 @ 0x14d65a0]8x8 transform intra:79.6% inter:77.0%
[libx264 @ 0x14d65a0]direct mvs  spatial:99.5% temporal:0.5%
[libx264 @ 0x14d65a0]coded y,uvDC,uvAC intra: 70.0% 83.9% 36.7% inter: 31.9% 32.0% 2.2%
[libx264 @ 0x14d65a0]i16 v,h,dc,p: 25% 13%  8% 53%
[libx264 @ 0x14d65a0]i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 12%  7%  7%  9% 14% 16% 12% 13% 11%
[libx264 @ 0x14d65a0]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 14%  7%  6%  9% 15% 16% 12% 11% 10%
[libx264 @ 0x14d65a0]Weighted P-Frames: Y:1.3%
[libx264 @ 0x14d65a0]ref P L0: 59.1% 17.1%  9.9%  7.4%  5.1%  1.4%  0.0%
[libx264 @ 0x14d65a0]ref B L0: 77.4% 15.1%  6.1%  1.4%
[libx264 @ 0x14d65a0]ref B L1: 95.1%  4.9%
[libx264 @ 0x14d65a0]kb/s:5354.04

real	4m1.843s
user	21m32.330s
sys	0m2.590s

```

---

### Post by andrew.46 on 2010-03-10
Well, you may be interested in the statistics from a *much* more modest system running 32 bit slackware, Intel Core2 Duo Mobile Processor T5500 with 2 gig RAM:

```

andrew@skamandros~/Desktop$ time ffmpeg -i IronMan.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre slow -crf 20 -threads 0 output.mp4
FFmpeg version SVN-r22413, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 10 2010 10:29:13 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libfaad --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50.11. 0 / 50.11. 0
  libavcodec    52.58. 0 / 52.58. 0
  libavformat   52.55. 0 / 52.55. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.17. 0 /  1.17. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x80793a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (10000000/208541) -> 24.00 (24/1)
Input #0, matroska, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 24.39 fps, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
[libx264 @ 0x8139fd0]using SAR=115/87
[libx264 @ 0x8139fd0]using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x8139fd0]profile High, level 3.1
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf52.55.0
    Stream #0.0: Video: libx264, yuv420p, 1280x720 [PAR 115:87 DAR 1840:783], q=10-51, 200 kb/s, 24 tbn, 24 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 2599 fps=  3 q=-1.0 Lsize=   72083kB time=108.29 bitrate=5452.9kbits/s dup=0 drop=1    
video:69812kB audio:2191kB global headers:0kB muxing overhead 0.111215%
[libx264 @ 0x8139fd0]frame I:44    Avg QP:18.56  size:106668
[libx264 @ 0x8139fd0]frame P:1049  Avg QP:21.70  size: 34346
[libx264 @ 0x8139fd0]frame B:1506  Avg QP:23.80  size: 20428
[libx264 @ 0x8139fd0]consecutive B-frames: 11.3% 21.1% 27.8% 39.8%
[libx264 @ 0x8139fd0]mb I  I16..4:  5.2% 81.6% 13.2%
[libx264 @ 0x8139fd0]mb P  I16..4:  8.3% 39.6%  2.6%  P16..4: 29.7% 10.4%  5.3%  0.0%  0.0%    skip: 4.2%
[libx264 @ 0x8139fd0]mb B  I16..4:  1.7% 13.3%  1.3%  B16..8: 45.4%  2.9%  2.7%  direct: 6.6%  skip:26.2%  L0:47.0% L1:44.9% BI: 8.1%
[libx264 @ 0x8139fd0]8x8 transform intra:79.7% inter:77.1%
[libx264 @ 0x8139fd0]direct mvs  spatial:99.9% temporal:0.1%
[libx264 @ 0x8139fd0]coded y,uvDC,uvAC intra: 69.9% 84.1% 37.0% inter: 31.5% 31.9% 2.1%
[libx264 @ 0x8139fd0]i16 v,h,dc,p: 26% 13%  9% 53%
[libx264 @ 0x8139fd0]i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 12%  7%  7%  9% 14% 16% 12% 13% 11%
[libx264 @ 0x8139fd0]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 14%  7%  6%  9% 15% 16% 12% 11% 10%
[libx264 @ 0x8139fd0]Weighted P-Frames: Y:1.3%
[libx264 @ 0x8139fd0]ref P L0: 59.4% 17.4%  9.6%  7.3%  4.9%  1.2%  0.0%
[libx264 @ 0x8139fd0]ref B L0: 77.2% 15.3%  6.2%  1.3%
[libx264 @ 0x8139fd0]ref B L1: 95.1%  4.9%
[libx264 @ 0x8139fd0]kb/s:5281.09

real	16m25.453s
user	26m26.968s
sys	0m26.914s

```

This is with compiled FFmpeg and x264. Runs about *3-4fps* on this setting, mind you I run most of my encoding jobs overnight so this is not too much of a problem... So now you can see how the other half lives :).

All the best,

Andrew

---

### Post by aflores3 on 2010-03-11
Andrew,
Thank you for sharing your results. The machine that I used to run wasn't much faster than that. I now use it as a myth frontend. Since I wanted to put together a dedicated myth backend / media server, I wanted to get the best I could afford since I knew i was going to be dealing a lot with video. 

What I can't figure out now, though, is why did my transcode take twice the time of fakeoutdoorsman (according to the real time)

---

### Post by FakeOutdoorsman on 2010-03-11
aflores3,

Your limiting factor may be the kernel.  A bug was fixed in the kernel scheduler in 2.6.32 that has dramatically increased encoding speed in some cases.  I believe Karmic is using 2.6.31 and therefore may not be taking advantage of this fix.  Ubuntu Lucid users should see a difference in encoding speed because it uses 2.6.32 (unless the fix has been backported to Karmic and I'm not really sure of the process or how that works).  With 2.6.31 you may be seeing a performance penalty of up to 80%.

Perhaps you can compile your own recent kernel, try a new kernel supplied by a PPA, move on to Lucid, or even try another Linux distro with a more recent kernel.  I don't know the status of your machine, but I generally don't recommend kernel upgrades for an active production server, especially PPA packages, but it might be worth a try.

More info:

[Open source collaboration done right](http://x264dev.multimedia.cx/?p=185)

**Update:** I forgot to mention in my test encode above I am using 2.6.32.

---

### Post by verb3k on 2010-03-11
After reading the article (see FakeOutdoorsman's post above) about the scheduler bug in kernel 31 (which is the default in karmic) I asked in #ubuntu about getting a new kernel. I was directed to a ppa for daily builds, from which I installed the latest development version 34.

Here is the PPA:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/)
choose the latest date, download the packages that are marked for your processor (amd64 or i368 ) and the one marked "all" (except the source package, you don't need it) and install them with sudo dpkg -i package1 package2 package3 (replace with package names) and after installation finishes, restart your computer. I'm not responsible for anything if these instructions end up eating your valuable data :D
So do at your own risk.

---

### Post by mocha on 2010-03-12
I happened to bump into this thread and enjoy these benchmarks for fun.  I need to update my ffmpeg, but here are my results using an older ffmpeg and "lossless_slow" x264 preset (essentially very similar to "slow" on newer builds?).  This is from my Phenom quad core box with Karmic 32 bit, stock 2.6.31-20 kernel.

```
$ time ffmpeg -i IronMan.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre lossless_slow -crf 20 -threads 0 output.mp4
FFmpeg version SVN-r20544, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 16 2009 23:59:37 with gcc 4.4.1
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-zlib --enable-libvorbis --enable-postproc --enable-x11grab
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
[libx264 @ 0x9e95370]using SAR=115/87
[libx264 @ 0x9e95370]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x9e95370]profile High, level 3.1
Output #0, mp4, to 'output.mp4':
    Stream #0.0: Video: libx264, yuv420p, 1280x720 [PAR 115:87 DAR 1840:783], q=10-51, 200 kb/s, 24k tbn, 23.98 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   20 fps=  0 q=-10990028.7 size=       0kB time=1.62 bitrate=   0.2kbits/frame= 2585 fps= 13 q=25.0 Lsize=   75779kB time=108.40 bitrate=5726.7kbits/s    
video:73527kB audio:2190kB global headers:0kB muxing overhead 0.080966%
[libx264 @ 0x9e95370]frame I:67    Avg QP:18.76  size: 76832
[libx264 @ 0x9e95370]frame P:2518  Avg QP:22.17  size: 27857
[libx264 @ 0x9e95370]mb I  I16..4:  9.5% 81.2%  9.3%
[libx264 @ 0x9e95370]mb P  I16..4:  4.5% 28.8%  2.1%  P16..4: 41.3%  7.8%  4.9%  0.2%  0.2%    skip:10.2%
[libx264 @ 0x9e95370]8x8 transform intra:81.4% inter:64.8%
[libx264 @ 0x9e95370]coded y,uvDC,uvAC intra: 69.5% 83.3% 36.5% inter: 31.2% 30.1% 2.0%
[libx264 @ 0x9e95370]i16 v,h,dc,p: 26% 13%  7% 53%
[libx264 @ 0x9e95370]i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 18% 11% 15%  7% 10% 12%  9% 10%  8%
[libx264 @ 0x9e95370]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 22% 12% 12%  7% 12% 13%  8%  9%  6%
[libx264 @ 0x9e95370]Weighted P-Frames: Y:1.1%
[libx264 @ 0x9e95370]ref P L0: 58.1% 20.2% 21.7%
[libx264 @ 0x9e95370]kb/s:5586.63

real	3m13.844s
user	8m42.277s
sys	0m10.593s

```

Does this mean I'm faster than a Core i7 processor??  Why such low user time?  Maybe I'll update my ffmpeg and rerun the test using the exact same preset.

---

### Post by FakeOutdoorsman on 2010-03-12
> **mocha said:**
> I happened to bump into this thread and enjoy these benchmarks for fun.  I need to update my ffmpeg, but here are my results using an older ffmpeg and "lossless_slow" x264 preset (essentially very similar to "slow" on newer builds?).
The *slow* preset is different than *lossless_slow*.  A bunch of [additional presets](http://ubuntuforums.org/showpost.php?p=8905745&postcount=895) that attempt to emulate the x264 presets were applied to FFmpeg on February 26.

---

### Post by mocha on 2010-03-12
> **FakeOutdoorsman said:**
> The *slow* preset is different than *lossless_slow*.  A bunch of [additional presets](http://ubuntuforums.org/showpost.php?p=8905745&postcount=895) that attempt to emulate the x264 presets were applied to FFmpeg on February 26.

Cool.  Time to update and get back to encoding.

---

### Post by mocha on 2010-03-13
Okay here is mine with latest ffmpeg pull.  AMD Phenom II X4 945, stock clock 3 GHz.

```
$ time ffmpeg -i IronMan.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre slow -crf 20 -threads 0 output.mp4
FFmpeg version SVN-r22500, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 12 2010 23:21:00 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-zlib --enable-libvorbis
  libavutil     50.11. 0 / 50.11. 0
  libavcodec    52.58. 0 / 52.58. 0
  libavformat   52.55. 0 / 52.55. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x96203a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (10000000/208541) -> 24.00 (24/1)
Input #0, matroska, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 24.39 fps, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
[libx264 @ 0x96e0fd0]using SAR=115/87
[libx264 @ 0x96e0fd0]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x96e0fd0]profile High, level 3.1
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf52.55.0
    Stream #0.0: Video: libx264, yuv420p, 1280x720 [PAR 115:87 DAR 1840:783], q=10-51, 200 kb/s, 24 tbn, 24 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   34 fps=  0 q=-11665884.7 size=       0kB time=1.47 bitrate=   0.3kbits/frame= 2599 fps=  8 q=-2.0 Lsize=   72188kB time=108.29 bitrate=5460.9kbits/s dup=0 drop=1    
video:69917kB audio:2191kB global headers:0kB muxing overhead 0.111053%
[libx264 @ 0x96e0fd0]frame I:44    Avg QP:18.56  size:106652
[libx264 @ 0x96e0fd0]frame P:1049  Avg QP:21.70  size: 34437
[libx264 @ 0x96e0fd0]frame B:1506  Avg QP:23.81  size: 20436
[libx264 @ 0x96e0fd0]consecutive B-frames: 11.3% 21.1% 27.8% 39.8%
[libx264 @ 0x96e0fd0]mb I  I16..4:  5.2% 81.6% 13.2%
[libx264 @ 0x96e0fd0]mb P  I16..4:  8.4% 40.1%  2.6%  P16..4: 29.2% 10.3%  5.3%  0.0%  0.0%    skip: 4.1%
[libx264 @ 0x96e0fd0]mb B  I16..4:  1.7% 13.3%  1.3%  B16..8: 45.4%  2.9%  2.7%  direct: 6.6%  skip:26.1%  L0:46.8% L1:45.1% BI: 8.2%
[libx264 @ 0x96e0fd0]8x8 transform intra:79.6% inter:77.0%
[libx264 @ 0x96e0fd0]direct mvs  spatial:99.7% temporal:0.3%
[libx264 @ 0x96e0fd0]coded y,uvDC,uvAC intra: 69.8% 84.0% 36.9% inter: 31.5% 31.8% 2.1%
[libx264 @ 0x96e0fd0]i16 v,h,dc,p: 25% 13%  9% 53%
[libx264 @ 0x96e0fd0]i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 12%  7%  7%  9% 14% 16% 12% 13% 11%
[libx264 @ 0x96e0fd0]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 14%  7%  6%  9% 15% 16% 12% 11% 10%
[libx264 @ 0x96e0fd0]Weighted P-Frames: Y:1.3%
[libx264 @ 0x96e0fd0]ref P L0: 59.5% 17.3%  9.8%  7.3%  4.9%  1.3%  0.0%
[libx264 @ 0x96e0fd0]ref B L0: 77.4% 15.1%  6.1%  1.3%
[libx264 @ 0x96e0fd0]ref B L1: 95.1%  4.9%
[libx264 @ 0x96e0fd0]kb/s:5289.03

real	5m11.381s
user	14m31.674s
sys	0m10.977s

```

I'm slightly perplexed by the user time compared to you guy's results, I also would've expected the real time to be longer compared to the Core i7... Comments?

---

