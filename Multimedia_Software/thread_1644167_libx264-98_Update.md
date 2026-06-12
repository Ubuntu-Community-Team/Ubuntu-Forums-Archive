---
title: "libx264-98 Update"
date: 2010-12-12
forum: Multimedia Software
---

### Post by gelepawa on 2010-12-12
Hi All,

I use mencoder, ffmpeg and avidemux to encode videos onto my PSP however when I updated my 10.10 yesterday I received updates for libx264-98 and x264 which are listed here [http://www.ubuntuupdates.org/packages/show/257736]("http://www.ubuntuupdates.org/packages/show/257736").

Subsequently I am not able to encode videos to my PSP as it appears to change the video to 1 FPS and when I run ffmpeg to convert it to the psp format I get a "non monotone timestamps" error.  I've downgraded the libx264 packages back to the previous versions and run the encoding again and everything appears to be back to normal.

From my very limited knowledge it appears to be related to CRF or something to do with the timebase however I don't know how to troubleshoot this problem.  I'm not really sure what information to start posting but I'd be happy to go through whatever is necessary to fix the issue.

Thanks

---

### Post by FakeOutdoorsman on 2010-12-13
Can you show your command that you use to encode your videos for your PSP? If you're using FFmpeg, also show the complete output.

---

### Post by gelepawa on 2010-12-13
Here's the command I use to encode the video only.

```
mencoder \
        input.m2v \
        -sws 9 \
        -nosound \
        -fps 25 \
        -vf dsize=480:272,format=yv12,scale=480:272,harddup \
        -ovc x264 \
        -x264encopts crf=20:level_idc=30:me=umh:subq=7:partitions=all:no8x8dct:frameref=2:mixed_refs:bframes=0:b_pyramid=none:nopsnr:nossim:threads=auto \
        -of rawvideo \
        -mc 0 \
        -noskip \
        -ofps 25 \
        -o output.264 
```

I then encode the audio using faac using the following

```
faac --mpeg-vers 4 -b 128 -R 48000 -C 2 -X input.wav -o output.aac
```

I use MP4Box to multiplex the video and audio using

```
MP4Box -fps 25 -add output.264 output.mp4
MP4Box -fps 25 -add output.aac output.mp4

```

lastly I use ffmpeg to convert the file into psp format

```
ffmpeg -r 25 -i output.mp4 -f psp -metadata title="Title" -vcodec copy -acodec copy -r 25 maqxxxxx.mp4
```

I should mention that the file MP4Box produces is playable in mplayer.  Furthermore the video file mencoder produces is playable as well however it seems to detect the FPS as 1.  When I tried the playing the mencoder file before the update, it would play at 25 FPS so I'm not sure if this means anything.

The part that fails is the ffmpeg command however I'll have to run the process again (which will take some time) to get the output so I can post it here.  Before the update I remember the output from ffmpeg had a tbc 25 and after the update it was tbc 2 which led me to think it had something to do with the way ffmpeg interprets the timebase however I have no idea what I'm talking about.

I have run the windows file AtomChanger.exe in wine on the file MP4Box produces and it is playable on my psp which suggests to me maybe ffmpeg can't handle the new changes to libx264?

---

### Post by FakeOutdoorsman on 2010-12-13
That's a lot of steps and I think it can be simplified.  I recommend following this:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

...and then trying the one-pass example in the [PSP video guide](http://rob.opendot.cl/index.php/useful-stuff/psp-video-guide/).

---

### Post by gelepawa on 2010-12-13
Yep you are correct there are lots of steps and thanks for the link as I will definitely try compiling the latest ffmpeg and x264.

There are 3 reasons why I use these steps.

1.  I couldn't work out a way to use video filters like in mencoder in ffmpeg.
2.  Audio is really soft on the psp which is why I separate the audio stream for normalisation.
3.  I wanted a command line solution so I could script this.

Haven't had time to play with handbrake (maybe I should) but I've tried ffmpeg and avidemux with mixed results like audio sync issues.  The above method although complicated just works and has been working for a long time.  I am aware of the psp link you sent however the settings are a bit outdated and don't produce the best quality/size but thanks for the suggestion.

---

### Post by FakeOutdoorsman on 2010-12-13
> **gelepawa said:**
> 1.  I couldn't work out a way to use video filters like in mencoder in ffmpeg.
What kind of filters are you looking for? Once you compile FFmpeg you will have access to the *-vf* option which is not available currently in the repository FFmpeg:
```
$ ffmpeg -filters list
...
anull            Pass the source unchanged to the output.
anullsrc         Null audio source, never return audio frames.
anullsink        Do absolutely nothing with the input audio.
blackframe       Detect frames that are (almost) black.
crop             Crop the input video to width:height:x:y.
cropdetect       Auto-detect crop size.
drawbox          Draw a colored box on the input video.
fifo             Buffer input images and send them when they are requested.
format           Convert the input video to one of the specified pixel formats.
frei0r           Apply a frei0r effect.
hflip            Horizontally flip the input video.
hqdn3d           Apply a High Quality 3D Denoiser.
noformat         Force libavfilter not to use any of the specified pixel formats for the input to the next filter.
null             Pass the source unchanged to the output.
overlay          Overlay a video source on top of the input.
pad              Pad input image to width:height[:x:y[:color]] (default x and y: 0, default color: black).
pixdesctest      Test pixel format definitions.
scale            Scale the input video to width:height size and/or convert the image format.
setdar           Set the frame display aspect ratio.
setpts           Set PTS for the output video frame.
setsar           Set the pixel sample aspect ratio.
settb            Set timebase for the output link.
slicify          Pass the images of input video on to next video filter as multiple slices.
transpose        Transpose input video.
unsharp          Sharpen or blur the input video.
vflip            Flip the input video vertically.
yadif            Deinterlace the input image
buffer           Buffer video frames, and make them accessible to the filterchain.
color            Provide an uniformly colored input, syntax is: [color[:size[:rate]]]
frei0r_src       Generate a frei0r source.
nullsrc          Null video source, never return images.
nullsink         Do absolutely nothing with the input video.
```

> **gelepawa said:**
> 2.  Audio is really soft on the psp which is why I separate the audio stream for normalisation.
I didn't see this process in your original post. There are several methods to do this. Try the **normalize-audio** package. Or try SoX as described here: [FFmpeg and 'Fist of Fury'](http://www.andrews-corner.org/fist.html). You may be able to pipe your input to sox and then back to your encoder to avoid an intermediate file.

> **gelepawa said:**
> I am aware of the psp link you sent however the settings are a bit outdated and don't produce the best quality/size but thanks for the suggestion.
Try it at least, and if it works I can give you some suggestions to update the command.

---

### Post by gelepawa on 2010-12-14
Wow I did not realise that ffmpeg does video filters.  I installed x264 and ffmpeg using the link to the guide.  I'm going to have a play with the settings from the psp link and my settings in the mencoder command to get like for like values.

Yes I use sox to normalize the audio using the compand however my concern now is whether the video and audio are in sync when I multiplex the streams using ffmpeg as I haven't had much luck in the past.

For posterity I tried again using the latest versions of x264 and ffmpeg and I still get the error below.

```
FFmpeg version SVN-r25943, Copyright (c) 2000-2010 the FFmpeg developers
  built on Dec 14 2010 13:35:20 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.34. 0 / 50.34. 0
  libavcore      0.16. 0 /  0.16. 0
  libavcodec    52.99. 1 / 52.99. 1
  libavformat   52.88. 0 / 52.88. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.69. 0 /  1.69. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 2.00 (2/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'output.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
    creation_time   : 2010-12-13 05:50:42
  Duration: 01:50:03.68, start: 0.000000, bitrate: 1372 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 480x272 [PAR 1:1 DAR 30:17], 1226 kb/s, 25 fps, 25 tbr, 25k tbn, 2 tbc
    Metadata:
      creation_time   : 2010-12-13 05:50:42
    Stream #0.1(und): Audio: aac, 48000 Hz, 5.1, s16, 434 kb/s
    Metadata:
      creation_time   : 2010-12-13 05:51:55
Output #0, psp, to '_maqxxxxx.mp4':
  Metadata:
    title           : title
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
    creation_time   : 2010-12-13 05:50:42
    encoder         : Lavf52.88.0
    Stream #0.0(und): Video: libx264, yuv420p, 480x272 [PAR 1:1 DAR 30:17], q=2-31, 1226 kb/s, 1 tbn, 1 tbc
    Metadata:
      creation_time   : 2010-12-13 05:50:42
    Stream #0.1(und): Audio: libfaac, 48000 Hz, 5.1, 434 kb/s
    Metadata:
      creation_time   : 2010-12-13 05:51:55
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[psp @ 0x9480ba0] st:0 error, non monotone timestamps 1 >= 1
av_interleaved_write_frame(): Operation not permitted 
```

---

### Post by FakeOutdoorsman on 2010-12-14
> **gelepawa said:**
> I'm going to have a play with the settings from the psp link and my settings in the mencoder command to get like for like values.
Are you planning to copy the x264encopts from MEncoder to use in FFmpeg? This not recommended because, as you have just experienced, updates to x264 may break your command. Use the presets instead as shown in the PSP link I gave you and then build from them. x264 and FFmpeg development is very active, but the presets are kept up to date with any changes.

> **gelepawa said:**
> For posterity I tried again using the latest versions of x264 and ffmpeg and I still get the error below.
What was the command?

---

### Post by gelepawa on 2010-12-14
I was going to try to find like for like values for the video filter.  Sometimes I use eq2 (brightness,hue...), smoothblur in addition to the ones mentioned in the above command but I was reading the filters for ffmpeg and couldn't locate an equivalent.

The command used to get the output from ffmpeg is the same as that was mentioned above.

```
ffmpeg -r 25 -i output.mp4 -f psp -metadata title="Title" -vcodec copy -acodec copy -r 25 maqxxxxx.mp4
```

However I also tried

```
ffmpeg -i output.mp4 -vcodec copy -acodec copy maqxxxxx.mp4
```

and get the same error.

I'll give the psp settings a go without the filters just to see if it works.  In past experience the presets have not worked on the psp so it would be interesting to find out.

---

### Post by zigzag77 on 2010-12-22
Maybe the following ffmpeg command line works for PSP with the december 2010 build of ffmeg:
```
ffmpeg  -i  $1                          \
   -acodec libfaac -ar 44100 -ab 128k         \
   -vcodec libx264 -vpre fast -vpre baseline  \
   -b 1000k -maxrate 2000k -bufsize 2000k     \
   -f psp -vf "scale=480:272"                 \
   -threads 0                                 \
   -y $1-psp.mp4 
```
If your audio and video sources are in separate files, you can use an additional -i input.wav parameter.

Your ffmpeg output reads:
```
Stream #0.1(und): Audio: libfaac, 48000 Hz, 5.1, 434 kb/s
```That's 5.1 surround sound. You might want to specify -ac 2 to downmix it to stereo.

---

### Post by zigzag77 on 2010-12-23
The above combination of -vpre fast and -vpre baseline works fine for PS3 and HTC Desire (Android 2.2). The trick seems to be to avoid B-Frames for devices with limited performance.

---

### Post by zigzag77 on 2010-12-24
Just had a PSP 2004 here for test. The following command produces nice output with the current ffmpeg and libx264 (December 2010). Video source is a Panasonic DMR-EH PAL hard disk / DVD recorder. Scaling and cropping removes black portions of source image.

```
ffmpeg  -i $1                     \
    -t 20                     \
    -deinterlace                \
    -acodec libfaac -ar 48000 -ab 128k     \
    -vcodec libx264 -vpre fast -vpre baseline    \
    -vf "scale=480:368,crop=480:272"    \
    -b 1000k -maxrate 2000k -bufsize 2000k    \
    -threads 0                \
    -y $1-pana2psp-16_9-in-4_3-frame-crop-480x272-fast+base-1max2mbps.mp4
```

**-t 20** stops the conversion after 20 seconds of input video, of course only for quick testing.

Can any other Ubuntu user confirm that this works? :D

---

