---
title: "ffmpeg Error"
date: 2010-02-08
forum: Multimedia Software
---

### Post by AmbiguousOutlier on 2010-02-08
Hello does anyone know what I need to install to get this to work.
 
```
rhys@Melon:~/Videos$ ffmpeg -i title03.mkv
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[matroska @ 0x92dd700]Unknown/unsupported CodecID S_HDMV/PGS.
title03.mkv: memory allocation error occurred
```

I'm trying to run ffmpeg on a mkv file made from a BD using makeMKV. However it appears as if I don't have a codec called S_HDMV/PGS. I've searched for this on google but can't find any solutions.

Any ideas?

---

### Post by DeanFX on 2010-02-08
> **RhysGM said:**
> Hello does anyone know what I need to install to get this to work.
 
```
rhys@Melon:~/Videos$ ffmpeg -i title03.mkv
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[matroska @ 0x92dd700]Unknown/unsupported CodecID S_HDMV/PGS.
title03.mkv: memory allocation error occurred
```

I'm trying to run ffmpeg on a mkv file made from a BD using makeMKV. However it appears as if I don't have a codec called S_HDMV/PGS. I've searched for this on google but can't find any solutions.

Any ideas?

What are you trying to convert the MKV file to?

---

### Post by AmbiguousOutlier on 2010-02-08
I've figured out it's the subtitles so I don't necessarily need them, however if I have forced subtitles then I'm thinking I will lose them if I stick them in an avi.

---

### Post by DeanFX on 2010-02-08
> **RhysGM said:**
> I've figured out it's the subtitles so I don't necessarily need them, however if I have forced subtitles then I'm thinking I will lose them if I stick them in an avi.

So you are trying to convert MKV to AVI.

Did you try doing it this way:

> ffmpeg -i filename.mkv newfilename.avi

---

### Post by AmbiguousOutlier on 2010-02-08
I'm trying it now, first time using ffmpeg. It's taking a while. And I'm going to have to test it with a disc with subtitles.

Do you know of guide with all the options. I can't find a complete list only bits and pieces all over the place.

---

### Post by DeanFX on 2010-02-08
To convert a file, just type it exactly how I wrote it in my previous reply.

You should be able to see a list of ffmpegs commands by just typing ffmpeg in the CLI.

Let me know if that works.

---

### Post by AmbiguousOutlier on 2010-02-08
that's a lot of options. 

My MKV is 30gb I want to compress it slightly down to about 5 or 6gb. I'll play around with until I get what I need.

---

### Post by DeanFX on 2010-02-08
Damn. Big video.

Not to familiar with video compression, but thats how to convert it.

Let me know if you get any feedback/good results on the compression. Curious about that.

---

### Post by AmbiguousOutlier on 2010-02-08
I ripped a Bluray using makeMKV. And now I want to convert them into a more reasonable size.

---

### Post by warp99 on 2010-02-08
Do you have the "dirty" codecs installed? Those would be packages libavcodec-extra-52, libavformat-extra-52, and libavdevice-extra-52.

Edit: I found a solution based on this thread:

[http://forum.doom9.org/showthread.php?t=146472](http://forum.doom9.org/showthread.php?t=146472)

---

### Post by AmbiguousOutlier on 2010-02-08
> **warp99 said:**
> Do you have the "dirty" codecs installed? Those would be packages libavcodec-extra-52, libavformat-extra-52, and libavdevice-extra-52.

I used this to install it

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

It didn't tell me about any of those 'extra' codecs.

---

### Post by no2498 on 2010-02-08
im thinking ( tragtor ) may help you

---

### Post by warp99 on 2010-02-08
> **RhysGM said:**
> I used this to install it

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

It didn't tell me about any of those 'extra' codecs.

It wouldn't matter because this is a subtitle issue, which I found out after posting. I would install the extra codecs anyway if you get a chance. The link in my previous post had a solution to convert the BD subtitle to a vobsub then you could remux the subs back into the format of your choosing. 

If you don't need the subtitles you could just omit them during conversion. According to the ffmpeg documentation you can use the -sn parameter to drop the subs:

[http://ffmpeg.org/ffmpeg-doc.html#SEC13](http://ffmpeg.org/ffmpeg-doc.html#SEC13)

Just use trial and error to get the correct string for conversion. If you do a search there's a ton on information on doing this both here and on the Doom9 boards. :D

---

### Post by FakeOutdoorsman on 2010-02-08
> **RhysGM said:**
> Hello does anyone know what I need to install to get this to work.
 
```
rhys@Melon:~/Videos$ ffmpeg -i title03.mkv
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[matroska @ 0x92dd700]Unknown/unsupported CodecID S_HDMV/PGS.
title03.mkv: memory allocation error occurred
```

I'm trying to run ffmpeg on a mkv file made from a BD using makeMKV. However it appears as if I don't have a codec called S_HDMV/PGS. I've searched for this on google but can't find any solutions.

Any ideas?

I recommend compiling FFmpeg.  Because FFmpeg development very active and there is a chance that you won't get these errors or messages with a recent version of FFmpeg, and by compiling it yourself you're getting the most recent version available:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Now you can try re-encoding the video and copying the audio and subtitles (and hopefully with your compiled FFmpeg you won't get the same errors):
```
ffmpeg -i input_video.mkv -vcodec libx264 -vpre hq -crf 22 -acodec copy -scodec copy -threads 0 output.mkv
```
The important options are *-vpre* and *-crf*.  If your encoding is too slow, you can change to *-vpre default*.  It will result in a lower quality output file, but encoding will be faster.  If it is still too slow, change to *-vpre normal*.  The *-crf* option is the rate control method and controls the quality.  A sane range is 18-30 with a smaller number being higher quality, but with a larger output file size.

The *-t* option allows you to perform test encodes without encoding the whole video.  The following example will create an output that is 30 seconds long:
```
ffmpeg -t 30 -i input_video.mkv -vcodec libx264 -vpre hq -crf 22 -acodec copy -scodec copy -threads 0 output.mkv
```
You can then cut out 30 seconds of your original and use it to make a rough comparison with re-encoded video:
```
ffmpeg -t 30 -i input_video.mkv -acodec copy -vcodec copy -scodec copy output2.mkv
```

---

### Post by AmbiguousOutlier on 2010-02-09
> **FakeOutdoorsman said:**
> I recommend compiling FFmpeg.  Because FFmpeg development very active and there is a chance that you won't get these errors or messages with a recent version of FFmpeg, and by compiling it yourself you're getting the most recent version available:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

I've installed the latest ffmpeg as per the thread.

> **FakeOutdoorsman said:**
> The *-t* option allows you to perform test encodes without encoding the whole video.  The following example will create an output that is 30 seconds long:
```
ffmpeg -t 30 -i input_video.mkv -vcodec libx264 -vpre hq -crf 22 -acodec copy -scodec copy -threads 0 output.mkv
```

I thought this was a very good idea to take a 30 sec sample for me to play around with, however I now get this error;

```
rhys@Melon:~/Videos/The_Dark_Knight$ ffmpeg -i title03.mkv -vcodec libx264 -vpre hq -crf 22 -acodec copy -scodec copy -threads 0 test30sec.mkv
FFmpeg version SVN-r21705, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  9 2010 17:51:30 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.53. 0 / 52.53. 0
  libavformat   52.51. 0 / 52.51. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x9d7a3a0]Estimating duration from bitrate, this may be inaccurate
Input #0, matroska, from 'title03.mkv':
  Metadata:
    original_writing_app: MakeMKV v1.4.12 beta linux(x86-release)
  Duration: 02:32:13.33, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: vc1, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 23.98 tbr, 1k tbn, 23.98 tbc
    Metadata:
      FPS             : 23.976 (24000/1001)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 6 channels, s16
    Metadata:
      title           : 3/2+1
    Stream #0.2(eng): Audio: truehd, 48000 Hz, 6 channels, s32
    Metadata:
      title           : 5.1
    Stream #0.3(eng): Audio: ac3, 48000 Hz, 6 channels, s16
    Metadata:
      title           : 3/2+1
    Stream #0.4(eng): Audio: ac3, 48000 Hz, 2 channels, s16
    Metadata:
      title           : 2/0
[libx264 @ 0x9dff8c0]using SAR=1/1
[libx264 @ 0x9dff8c0]using cpu capabilities: MMX2 SSE2Slow
[libx264 @ 0x9dff8c0]profile High, level 4.0
Output #0, matroska, to 'test30sec.mkv':
    Stream #0.0(eng): Video: libx264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=10-51, 200 kb/s, 1k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 6 channels
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   16 fps=  0 q=-10140524.7 size=       1kB time=1.31 bitrate=   3.6kbits/[matroska @ 0xa0b1750]st:1 error, non monotone timestamps 2048 >= 2048
av_interleaved_write_frame(): Error while opening file
```

---

### Post by AmbiguousOutlier on 2010-02-09
Ok, it's because I've got copy for the -acodec option. The error is probably because I have multiple streams or it can't decode truehd. 

In either case if I put ac3 it just copies the last stream which is 2 channel. How do I specify the 3/2.1 channel. I'm assuming this is DD5.1? I would prefer 2 channel and 5.1 so if I play it on a device without a DD decoder it can still play with stereo. Is this possible?

EDIT:
I've found the -map option however even if I select a stream with more than 2 channels it still only outputs 2 channels I've tried multiple audio codecs. Also if I map the TrueHD audio stream then can I output this in a lossless format like flac? I have tried this codec but it's downmixing it to 2 channel. So I'm not sure if it's doing it correctly.

EDIT: 
Is -ac 6 the same as 5.1?

---

### Post by FakeOutdoorsman on 2010-02-09
> **RhysGM said:**
> I thought this was a very good idea to take a 30 sec sample for me to play around with, however I now get this error;

```
[matroska @ 0xa0b1750]st:1 error, non monotone timestamps 2048 >= 2048
av_interleaved_write_frame(): Error while opening file
```

You're correct that something to do with the audio seems to be the problem.  Probably related to:
[Issue 807: codec = copy causes problems on some files](https://roundup.ffmpeg.org/roundup/ffmpeg/issue807)

I was able to duplicate this error (or something very similar) and was able to fix it with a patch included in the bug report:
```
sudo apt-get remove ffmpeg
cd ffmpeg
make distclean
svn up
wget --no-check-certificate https://roundup.ffmpeg.org/roundup/ffmpeg/file771/matroska_ac3_needs_parsing_v1.patch
patch -p0 -i matroska_ac3_needs_parsing_v1.patch
```
Then ./configure, make, checkinstall as shown in the compilation guide.

---

### Post by AmbiguousOutlier on 2010-02-09
Thanks, whatever you did now means my output has 5.1 sound. Quick question would this automatically downmix to stereo if I play with no 5.1 decoder? If not can I encode with 2 audio streams?

---

### Post by FakeOutdoorsman on 2010-02-09
> **RhysGM said:**
> Thanks, whatever you did now means my output has 5.1 sound. Quick question would this automatically downmix to stereo if I play with no 5.1 decoder?
I'm not sure.  Seems to play fine through my headphones, but maybe that's not what you mean.
> If not can I encode with 2 audio streams?
Using the *-map* option should allow you to choose which audio streams you want to keep.  Here's a good description of [mapping channels in FFmpeg](http://howto-pages.org/ffmpeg/#map).  That way you can have a 5.1 stream and a stereo stream if your input file already contains these.

> Is -ac 6 the same as 5.1?
I'm unsure if *-ac 6* is equivalent to 5.1.

Or if you want to add audio from a second input you can use the *-newaudio* option:
```
ffmpeg -i input.mkv -i audio.mp3 -vcodec copy -acodec copy output.mkv -acodec copy -newaudio
```

---

### Post by AmbiguousOutlier on 2010-02-10
Thank you Outdoorsman for all your help.

Another question, am I dropping every other frame? I'm not that great with the whole interlaced and progressive scanning thing. But was the orginal at 48fps interlaced and now it's 24fps progressive?

Also my file size is around 3gb for the total file, however it took more than 12 hours (not sure exactly, I was at work when it finished). If I change the -vbre option will this effect quality or is it just speed and file size?

```
ffmpeg -i title03.mkv -map 0:0 -map 0:1 -vcodec libx264 -vpre hq -crf 22 -acodec copy -scodec copy -threads 0 The_Dark_Knight.mkv
```


```
rhys@Melon:~/Videos/The_Dark_Knight$ ffmpeg -i The_Dark_Knight.mkv
FFmpeg version SVN-r21714, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  9 2010 22:38:29 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.53. 0 / 52.53. 0
  libavformat   52.51. 0 / 52.51. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0xa5ba3a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from 'The_Dark.mkv':
  Duration: 02:32:13.37, start: 0.000000, bitrate: 640 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 47.62 fps, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 640 kb/s
At least one output file must be specified
```

---

### Post by FakeOutdoorsman on 2010-02-10
> **RhysGM said:**
> Thank you Outdoorsman for all your help.

Another question, am I dropping every other frame? I'm not that great with the whole interlaced and progressive scanning thing. But was the orginal at 48fps interlaced and now it's 24fps progressive?

Also my file size is around 3gb for the total file, however it took more than 12 hours (not sure exactly, I was at work when it finished). If I change the -vbre option will this effect quality or is it just speed and file size?
Does it play back fine despite the fps messages?

I ran a few short tests and the various presets didn't affect output file size as much as I thought and results were inconsistent between sources.  I generally just use hq.

So basically, If you want to encode faster use other presets: default, normal, (or maybe even fastfirstpass).  If you want a smaller file size, raise the crf value. Raising crf +6 is equivalent to roughly half the bitrate.

---

### Post by AmbiguousOutlier on 2010-02-10
> **FakeOutdoorsman said:**
> Does it play back fine despite the fps messages?

Playback was fine although I haven't tested it on my TV yet.

> **FakeOutdoorsman said:**
> default, normal, (or maybe even fastfirstpass).  If you want a smaller file size, raise the crf value. Raising crf +6 is equivalent to roughly half the bitrate.

I'll do some samples with default and normal. I actually meant 3gb was small. So hey I'll lower that number. Ultimately I want the best picture I can get in no more than about 5 or 6gb. Obviously I'd prefer it to be quicker but not at the cost to quality.

Anyway I think you've given me all the information I need to get my blu-rays onto my HDD. Thank you very much. 

Actually one last question. Upscaling compressed files isn't going to work, as not enough data. So if I put some DVD's on my hdd using the methods we've been discussing then upscale using either a player or the TV itself it wont look that great. However if I upscale them from the original uncompressed data on the DVD itself then obviously it wont look as good a 1080p but should still look better then DVD quality.

What do you think? Can I just use the -s 1920x1080 option?  Will it work even if the original is only 720x480?

---

### Post by FakeOutdoorsman on 2010-02-10
> **RhysGM said:**
> Playback was fine although I haven't tested it on my TV yet.



I'll do some samples with default and normal. I actually meant 3gb was small. So hey I'll lower that number. Ultimately I want the best picture I can get in no more than about 5 or 6gb. Obviously I'd prefer it to be quicker but not at the cost to quality.

Anyway I think you've given me all the information I need to get my blu-rays onto my HDD. Thank you very much. 

Actually one last question. Upscaling compressed files isn't going to work, as not enough data. So if I put some DVD's on my hdd using the methods we've been discussing then upscale using either a player or the TV itself it wont look that great. However if I upscale them from the original uncompressed data on the DVD itself then obviously it wont look as good a 1080p but should still look better then DVD quality.

What do you think? Can I just use the -s 1920x1080 option?  Will it work even if the original is only 720x480?

I've never tried anything like that and I'm unsure how effective an upscaled re-render would be.  I would guess that they wouldn't look too different because they are both working with the same input and both upscaling a limited amount of data, although you do lose quality on re-encoded video with lossy encoders (most people won't notice if you use decent settings).  There is also the effectiveness of the upscaling on the decoding side.  I don't know.  It would be an interesting test but I probably wouldn't bother with re-encoding just to upscale though.

Note that DVD is using non-square pixels (pixel aspect ratio or PAR) while your videos from makeMKV are square pixels (1:1 PAR), so some cropping or padding may be involved to get things to look correctly.  This stuff confuses me so I always have to make a bunch of test encodes before I eventually figure it out.

---

### Post by AmbiguousOutlier on 2010-02-11
I decided I should come back to DVD ripping at a later date. 

I've been playing around with some of the options -vbre and -crf.

However even on the best settings the encoded stuff is a little jerky. And the orignal is so much better. Also the higher the -crf then the sound seems to go out of sync. Because I have a small sample it may get worse further into the film. Is this all because I'm dropping a lot of frames?

Here are some samples of my efforts. 

[Orginal](http://www5.zippyshare.com/v/85595122/file.html)

[-vpre hq -crf 12](http://www5.zippyshare.com/v/77085929/file.html)

[-vpre hq -crf 22](http://www5.zippyshare.com/v/4558210/file.html)

The file sizes;
```
 rhys@Melon:~/Videos/The_Dark_Knight$ ls -l
total 33485524
-rw-r--r-- 1 rhys rhys    10820076 2010-02-11 19:04 sample_default_22.mkv
-rw-r--r-- 1 rhys rhys    53054139 2010-02-11 19:12 sample_hq_12.mkv
-rw-r--r-- 1 rhys rhys    20679723 2010-02-11 19:01 sample_hq_18.mkv
-rw-r--r-- 1 rhys rhys    14771403 2010-02-11 18:57 sample_hq_20.mkv
-rw-r--r-- 1 rhys rhys    10673008 2010-02-11 18:48 sample_hq_22.mkv
-rw-r--r-- 1 rhys rhys     4790313 2010-02-11 19:07 sample_hq_30.mkv
-rw-r--r-- 1 rhys rhys    10384098 2010-02-11 18:51 sample_normal_22.mkv
-rw-r--r-- 1 rhys rhys    78684620 2010-02-09 21:55 sample_org.mkv
-rw-r--r-- 1 rhys rhys  3271369928 2010-02-10 13:58 The_Dark_Knight_hq_22.mkv
-rw-r--r-- 1 rhys rhys 30813918394 2010-02-08 20:13 The_Dark_Knight.mkv
```

ffmpeg -i of the sample files attached;
```
rhys@Melon:~/Videos/The_Dark_Knight$ ffmpeg -i sample_org.mkv
FFmpeg version SVN-r21714, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  9 2010 22:38:29 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.53. 0 / 52.53. 0
  libavformat   52.51. 0 / 52.51. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[truehd @ 0xab213a0]Stream parameters not seen; skipping frame.
    Last message repeated 54 times
[matroska @ 0xab133a0]Estimating duration from bitrate, this may be inaccurate
Input #0, matroska, from 'sample_org.mkv':
  Metadata:
    original_writing_app: MakeMKV v1.4.12 beta linux(x86-release)
  Duration: 00:00:24.50, start: 0.000000, bitrate: 1472 kb/s
    Stream #0.0(eng): Video: vc1, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 23.98 tbr, 1k tbn, 23.98 tbc
    Metadata:
      FPS             : 23.976 (24000/1001)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 640 kb/s
    Metadata:
      title           : 3/2+1
    Stream #0.2(eng): Audio: truehd, 48000 Hz, 6 channels, s32
    Metadata:
      title           : 5.1
    Stream #0.3(eng): Audio: ac3, 48000 Hz, 5.1, s16, 640 kb/s
    Metadata:
      title           : 3/2+1
    Stream #0.4(eng): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Metadata:
      title           : 2/0
At least one output file must be specified
```


```
rhys@Melon:~/Videos/The_Dark_Knight$ ffmpeg -i sample_hq_22.mkv
FFmpeg version SVN-r21714, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  9 2010 22:38:29 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.53. 0 / 52.53. 0
  libavformat   52.51. 0 / 52.51. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x8d593a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from 'sample_hq_22.mkv':
  Duration: 00:00:24.52, start: 0.000000, bitrate: 640 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 47.62 fps, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 640 kb/s
At least one output file must be specified
```

```
rhys@Melon:~/Videos/The_Dark_Knight$ ffmpeg -i sample_hq_12.mkv
FFmpeg version SVN-r21714, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  9 2010 22:38:29 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.53. 0 / 52.53. 0
  libavformat   52.51. 0 / 52.51. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0xa8993a0]MAX_READ_SIZE:5000000 reached
[matroska @ 0xa8993a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from 'sample_hq_12.mkv':
  Duration: 00:00:24.52, start: 0.000000, bitrate: 640 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 47.62 fps, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 640 kb/s
At least one output file must be specified
```

---

### Post by FakeOutdoorsman on 2010-02-11
> **RhysGM said:**
> I decided I should come back to DVD ripping at a later date. 

I've been playing around with some of the options -vbre and -crf.
The option is *-vpre*, not *-vbre*.

> However even on the best settings the encoded stuff is a little jerky. And the orignal is so much better. Also the higher the -crf then the sound seems to go out of sync. Because I have a small sample it may get worse further into the film. Is this all because I'm dropping a lot of frames?

12 is way overkill.  A sane range is 18-28, and 18 is considered roughly visually lossless.  I'm not sure why a higher value seems to make the audio go out of sync for you.  Does it go out of sync with ffplay (ffplay input.mkv)?  Is your computer fast enough to decode such large videos?  Maybe someone at the *#ffmpeg* IRC channel can help you.  Make sure to show your complete FFmpeg command and full FFmpeg output (use pastebin.com and give them the link).  A sample file might help too.

I forgot to mention that you should read the [FFmpeg x264 Encoding Guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for a good introduction to some of these options.

---

### Post by AmbiguousOutlier on 2010-02-12
would someone mind downloading these two files for and tell me if the compressed runs smoothly?

[Orginal](http://www5.zippyshare.com/v/85595122/file.html)

[Compressed](http://www5.zippyshare.com/v/4558210/file.html)

The original runs perfectly but is 30gb (75mb sampled) and the compressed is a tenth of the size. However it stutters quite a bit. So I am just wondering if it's my hardware not being able to keep up. Could someone with a faster computer have a go for me please?

I have a amd athlon 4850e 2.5ghz with 2gb of ram and intergrated ati radeon hd3200 graphics.

Thank you very much.

---

### Post by FakeOutdoorsman on 2010-02-12
> **RhysGM said:**
> would someone mind downloading these two files for and tell me if the compressed runs smoothly?

[Orginal](http://www5.zippyshare.com/v/85595122/file.html)

[Compressed](http://www5.zippyshare.com/v/4558210/file.html)

The original runs perfectly but is 30gb (75mb sampled) and the compressed is a tenth of the size. However it stutters quite a bit. So I am just wondering if it's my hardware not being able to keep up. Could someone with a faster computer have a go for me please?

I have a amd athlon 4850e 2.5ghz with 2gb of ram and intergrated ati radeon hd3200 graphics.

Thank you very much.

Is sample_hq_22.mkv the same file from post #24 or is this one different?

---

### Post by AmbiguousOutlier on 2010-02-14
> **FakeOutdoorsman said:**
> Is sample_hq_22.mkv the same file from post #24 or is this one different?

It is, yes. Have you had a look, what's your verdict? Do I need to play around with ffmpeg more or do I need to buy a dedicated GPU?

---

### Post by FakeOutdoorsman on 2010-02-15
My computer is too slow to decode *sample_org.mkv* in MPlayer without it slowing down, but *sample_hq_22.mkv* seems to play better.  The frame size is probably a bit too much for my hardware, but if it works for you then I don't think you'll need to make any changes.

If it is too slow you can try lowering the frame size, and/or adding *-coder 0 -flags -loop* after *-vpre hq*.  These options will most likely lower the quality, but will also decrease the effort to decode the video.

Or you can get a video card that supports GPU decoding of H.264.  I have no experience with these.

---

