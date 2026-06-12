---
title: "[Maverick REQ] FFmpeg package with '-enable-vfilters' ?"
date: 2011-01-03
forum: Multimedia Software
---

### Post by gewone on 2011-01-03
Hiya!

I have the ffmpeg build from main repositories at the moment. Everything's fine, except that I can't use '*-vf'* stuff such as rotate encoding. I know that mencoder can easily do this, but let's say I want to stick to FFmpeg and still not having to compile it manually. Any ideas? Anyone who could pinpoint me to a neat .DEB package that won't conflict with other -- up to date -- 'Buntu 10.10 dependencies? Would be awesome! ;)

Ty in adv~
Regards~

---

### Post by BicyclerBoy on 2011-01-03
Having read your post about RAR VOB subs etc ...I do not think you will have any trouble with ffmpeg installation...

The ffmpeg people do not help with problems unless you have the latest version.
The repos copies are stripped so full GPL.

The fake outdoorsman's (Lou) guide to ffmpeg install is the way to go..
This ffmpeg configuration results in binaries for ffmpeg ffplay & it does not overwrite any system dynamic or shared libraries.

I have built ffmpeg from *buntu 8.04 to now with no dependency issues.

Packages built from source & outside of the package manager seem to be self-contained & do not overwrite system files.
This comment does not cover items like nvidia x driver & alsa lirc etc..

---

### Post by andrew.46 on 2011-01-04
Hi gewone,

You will need to bite the bullet and compile the svn FFmpeg, many filters available these days:

```

andrew@skamandros~$ ffmpeg -filters
FFmpeg version SVN-r26186, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan  2 2011 08:22:51 with gcc 4.5.1
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 0 /  0.16. 0
  libavcodec    52.101. 0 / 52.101. 0
  libavformat   52.91. 0 / 52.91. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.72. 0 /  1.72. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Filters:
anull            Pass the source unchanged to the output.
anullsrc         Null audio source, never return audio frames.
anullsink        Do absolutely nothing with the input audio.
blackframe       Detect frames that are (almost) black.
copy             Copy the input video unchanged to the output.
crop             Crop the input video to width:height:x:y.
cropdetect       Auto-detect crop size.
drawbox          Draw a colored box on the input video.
fifo             Buffer input images and send them when they are requested.
format           Convert the input video to one of the specified pixel formats.
gradfun          Debands video quickly using gradients.
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
nullsrc          Null video source, never return images.
nullsink         Do absolutely nothing with the input video.
andrew@skamandros~$ 

```

Andrew

---

### Post by FakeOutdoorsman on 2011-01-04
Here's the guide BicyclerBoy mentioned:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You'll get a bunch of filters (including the *transpose* filter which is like *rotate* I think) if you compile FFmpeg, and you won't have to modify the guide at all.

---

