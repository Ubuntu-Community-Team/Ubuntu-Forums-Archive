---
title: "To splice audio only in FFmpeg ?"
date: 2013-01-06
forum: Multimedia Software
---

### Post by shantiq on 2013-01-06
a [**while back **]("http://ubuntuforums.org/showthread.php?t=1782270&highlight=splice+audio+shantiq")i worked out how to splice most of the audio formats;  and it worked fine on aac with cat  [as does for mp3]

but trying this recently on files made with new codecs [libaacplus fdk_aac] it says it does not find the headers [i think]


so i really want to nail this with ffmpeg once and for all

i tried a few things but got nowhere fast 

so what would the syntax be?  just audio and in this case aac/m4a predominently    thanx in advance

---

### Post by evilsoup on 2013-01-06
You might be able to use the concat *protocol* - I've had no problems using this with just audio files.

```

ffmpeg -i "concat:input1.m4a|input2.m4a|input3.m4a" -c copy output.m4a

```

If that doesn't work, you could try using the concat *demuxer* (currently requires you to compile yourself, from git; the jon-severinsson PPA isn't quite up to date).

First, create a plaintext file containing the following:

```

file 'input1.m4a'
file 'input2.m4a'
file 'input3.m4a'

```

Call it 'inputs.txt', and then use this command:

```

ffmpeg -f concat -i inputs.txt -c copy output.m4a

```

---

### Post by shantiq on 2013-01-06
thanx esoup for reply


had already found and tried both of those and sadly they both yield same result on m4a


> Output #0, ipod, to 'output.m4a':
  Metadata:
    date            : 2010
    major_brand     : mp42
    minor_version   : 0
............................
    Stream #0:0: Video: mjpeg, yuvj420p, 500x500 [SAR 96:96 DAR 1:1], q=2-31, 90k tbn, 90k tbc
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, 37 channels (FL+FR), 63 kb/s
    Metadata:
      creation_time   : 2012-10-06 09:14:24
      handler_name    : Sound Media Handler
Stream mapping:
  Stream #0:1 -> #0:0 (copy)
  Stream #0:2 -> #0:1 (copy)
**Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted**


======
tested on flac it still does not work for me and does what cat does; which is to tell you it has worked and then you find the output file only contains the first audio;   but for flac i have sox which does work for splicing


puzzling business........ there has to be a way...

---

### Post by evilsoup on 2013-01-06
I just tested on some files I have... the concat protocol doesn't work on M4As, for me, but the demuxer works perfectly well. Neither works for -c:a copy for flac inputs, but if I use -c:a flac with the demuxer I can losslessly join them up.

Please put up the actual command you are using, and the full terminal output. I *suspect* that your problem is that you're using mjpeg video. I have no idea if that is supported in the MP4 container format (the error there may indicate 'no'), and besides you wrote that you wanted to concatenate audio only, so try it with the audio on its own.

---

### Post by shantiq on 2013-01-06
hi again


from the first command complete terminal output is


> **ffmpeg -i "concat:1.m4a|2.m4a" -c copy output.m4a**
ffmpeg version git-2012-12-22-e749b5d Copyright (c) 2000-2012 the FFmpeg developers
  built on Dec 22 2012 20:45:07 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3 --enable-libaacplus
  libavutil      52. 12.100 / 52. 12.100
  libavcodec     54. 81.100 / 54. 81.100
  libavformat    54. 49.102 / 54. 49.102
  libavdevice    54.  3.102 / 54.  3.102
  libavfilter     3. 29.101 /  3. 29.101
  libswscale      2.  1.103 /  2.  1.103
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x31f7760] stream 0, timescale not set
    Last message repeated 1 times
[aac @ 0x32096a0] Sample rate index in program config element does not match the sample rate index configured by the container.
[aac @ 0x32096a0] channel element 2.2 is not allocated
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x31f7760] max_analyze_duration 5000000 reached at 5015510
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'concat:1.m4a|2.m4a':
  Metadata:
 

[metadata info]
                    : 
                    : 
  Duration: 00:03:11.33, start: 0.000000, bitrate: 147 kb/s
    Chapter #0.0: start 0.105941, end 191.332422
    Metadata:
      title           : Heartbeat
    Stream #0:0(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 63 kb/s
    Metadata:
      creation_time   : 2012-10-06 09:13:36
      handler_name    : Sound Media Handler
    Stream #0:1: Video: mjpeg, yuvj420p, 500x500 [SAR 96:96 DAR 1:1], 90k tbr, 90k tbn, 90k tbc
    Stream #0:2(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, 37 channels (FL+FR), fltp, 63 kb/s
    Metadata:
      creation_time   : 2012-10-06 09:14:24
      handler_name    : Sound Media Handler
    Stream #0:3: Video: mjpeg, yuvj420p, 500x500 [SAR 96:96 DAR 1:1], 90k tbr, 90k tbn, 90k tbc
[ipod @ 0x3284800] track 0: could not find tag, codec not currently supported in container
Output #0, ipod, to 'output.m4a':
  Metadata:
  
[metadata info]


    Stream #0:0: Video: mjpeg, yuvj420p, 500x500 [SAR 96:96 DAR 1:1], q=2-31, 90k tbn, 90k tbc
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, 37 channels (FL+FR), 63 kb/s
    Metadata:
      creation_time   : 2012-10-06 09:14:24
      handler_name    : Sound Media Handler
Stream mapping:
  Stream #0:1 -> #0:0 (copy)
  Stream #0:2 -> #0:1 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted



and second


> **ffmpeg -f concat -i inputs.txt -c copy output.m4a**
ffmpeg version git-2012-12-22-e749b5d Copyright (c) 2000-2012 the FFmpeg developers
  built on Dec 22 2012 20:45:07 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3 --enable-libaacplus
  libavutil      52. 12.100 / 52. 12.100
  libavcodec     54. 81.100 / 54. 81.100
  libavformat    54. 49.102 / 54. 49.102
  libavdevice    54.  3.102 / 54.  3.102
  libavfilter     3. 29.101 /  3. 29.101
  libswscale      2.  1.103 /  2.  1.103
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x32462c0] stream 0, timescale not set
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x32462c0] max_analyze_duration 5000000 reached at 5015510
[concat @ 0x323d7a0] max_analyze_duration 5000000 reached at 5015510
[concat @ 0x323d7a0] Estimating duration from bitrate, this may be inaccurate
Input #0, concat, from 'inputs.txt':
  Duration: 00:00:00.00, start: 0.000000, bitrate: 63 kb/s
    Stream #0:0: Audio: aac (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 63 kb/s
    Stream #0:1: Video: mjpeg, yuvj420p, 500x500 [SAR 96:96 DAR 1:1], 90k tbr, 90k tbn, 90k tbc
[ipod @ 0x328f740] track 0: could not find tag, codec not currently supported in container
Output #0, ipod, to 'output.m4a':
  Metadata:
    encoder         : Lavf54.49.102
    Stream #0:0: Video: mjpeg, yuvj420p, 500x500 [SAR 96:96 DAR 1:1], q=2-31, 90k tbn, 90k tbc
    Stream #0:1: Audio: aac (mp4a / 0x6134706D), 44100 Hz, stereo, 63 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (copy)
  Stream #0:0 -> #0:1 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted




in both cases a video stream is discussed altho there isnt one....   probably where the kink appears when trying to splice... if extension changed for aac instead same result tho

**if i work from libfaac aac no problem then with either cat or ffmpeg**   but not what i seek :::]]

---

