---
title: "video tag in IE9 won't play mp4"
date: 2013-10-09
forum: Multimedia Software
---

### Post by coldraven on 2013-10-09
I created this short video (26 seconds, 5.2 MB) from a larger .avi in several versions and put them on the web.
```
<!DOCTYPE html>
<html lang="en-GB">
<head>
  <meta charset="utf-8">
  <link rel="stylesheet" href="../styles/lb_boats.css" type="text/css">
  <title>Launch!</title>
</head>
<body>

<video width="600" height="370" controls="controls" autoplay="yes" preload="none" poster="tmc-poster.png">
  <source src="tmc.mp4" type="video/mp4">
  <source src="tmc.m4v" type="video/mp4">
  <source src="tmc.webm" type="video/webm">
  <source src="tmc.ogg" type="video/ogg">  
</video>
<p>The &quot;Thomas McCunn&quot; is launched.</p>
<br>
<p><a href="javascript:history.back()">Back</a></p>
</body>
</html>


```

They seem to work in Firefox and Chromium and on an iPad (Safari?) but not in IE9
I read that IE9 only plays H.264 but is that not the same as AVC? See attached mediainfo.txt
The file can be found here. I also created a copy, renamed  to tmc.mp4 in the hope that IE would play it. maybe that was a mistake.
P.S. I'm not Mary :)
[URL="http://ubuntuone.com/6inVNsGZB1C9xFiAd2v4z5"]http://ubuntuone.com/6inVNsGZB1C9xFiAd2v4z5



[/URL]

---

### Post by evilsoup on 2013-10-09
It's sort of a stab in the dark, but it's probably that the MP4 files aren't ready for the internet.

Basically, the MP4 file format is broken into 'atoms'; one atom of the file that is required for playing the video is the 'moov atom' -- this contains a bunch of vital information that is needed to decode the file in a media player. Although it focuses on Adobe products, [this link](http://www.adobe.com/devnet/video/articles/mp4_movie_atom.html) gives a reasonable enough overview. 

By default most encoders will place the moov atom at the *end* of the file, because it can only be generated after the rest of the encoding is finished. For internet video purposes, you will have to move the moov atom to the *beginning* of the file, so that it can be used to decode the rest of the file without downloading the whole thing. One way to do this is with ffmpeg:

```

ffmpeg -i input.mp4 -c copy -movflags faststart output.mp4

```

This will result in no loss, since the actual bitstreams are being copied. To save yourself time in the future, if you are using ffmpeg to encode, you can just add '-movflags faststart' as an option.

This should work with the fake ffmpeg in the repositories, but if not then you can download an up-to-date static build from [here](http://ffmpeg.org/download.html#LinuxBuilds), or you can [compile your own](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) -- useful if you would like to have a decent AAC encoder with ffmpeg (libfdk_aac, which cannot be included in any distributed ffmpeg binary for licensing reasons).

---

### Post by coldraven on 2013-10-09
> By default most encoders will place the moov atom at the *end* of  the file, because it can only be generated after the rest of the  encoding is finished. For internet video purposes, you will have to move  the moov atom to the *beginning* of the file, so that it can be  used to decode the rest of the file without downloading the whole thing.  One way to do this is with ffmpeg:


Thanks evilsoup, I have not read that anywhere in my searches. I will try your tip later.
I did discover one error that I made. I created a .htaccess file with these MIME types in it.
```
AddType video/ogg .ogv
AddType video/mp4 .mp4
AddType video/webm .webm
```

But I put it in the root of the web-site instead of in the public_html folder. The problem is that I cannot test this as I do not have any Windows machines.
I'll have to ring a friend, so I will get back with a result tomorrow.

Edit: Good links!

---

### Post by coldraven on 2013-10-09
I installed from Jon Severinsson's ppa but get errors re: faststart
Do I need to compile ffmpeg myself? I see no reference to -movflags or faststart on the guide to compiling page or in the ffmpeg man pages.

```
[mp4 muxer @ 0x2139da0] [Eval @ 0x7fff62272ea0] Undefined constant or missing '(' in 'faststart'
[mp4 muxer @ 0x2139da0] Unable to parse option value "faststart"
[mp4 muxer @ 0x2139da0] Error setting option movflags to value faststart.


```


```
ffmpeg version 0.10.9-7:0.10.9-1~precise1 Copyright (c) 2000-2013 the FFmpeg developers
  built on Oct  4 2013 06:37:30 with gcc 4.6.3
  configuration: --arch=amd64 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='7:0.10.9-1~precise1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avcodec     configuration: --arch=amd64 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='7:0.10.9-1~precise1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-aacenc --enable-libvo-amrwbenc
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100


```

---

### Post by evilsoup on 2013-10-10
I don't know how up to date the version in the PPA is. You can compile your own (which, as I put in my other post, might be useful if you want a high-quality AAC encoder), or you can grab a static build [from the ffmpeg website](ffmpeg.org/download.html) and run that locally (just unpack the executable into your current directory and run it like './ffmpeg', or put it in your $PATH). I can confirm that the static build I just downloaded specifically to test this works perfectly with the command I posted above.

---

### Post by coldraven on 2013-10-10
Thanks evilsoup, I'm too tired now. will have a go tomorrow.

---

