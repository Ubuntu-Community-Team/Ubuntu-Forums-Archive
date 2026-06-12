---
title: "Encode video with alpha channel"
date: 2013-08-13
forum: Multimedia Software
---

### Post by xxlray on 2013-08-13
I have a sequence of images with transparency which I want to convert into a video with alpha channel. The following attempts did not work:

```
ffmpeg -f image2 -pattern_type glob -i '*.png' -vcodec png chromakeyed.mov
```

```
ffmpeg -f image2 -pattern_type glob -i '*.png' -vcodec vp6a chromakeyed.flv
```

```
ffmpeg -f image2 -pattern_type glob -i '*.png' -vcodec huffyuv chromakeyed.avi
```

```
ffmpeg -f image2 -pattern_type glob -i '*.png' -vcodec ffvhuv chromakeyed.avi
```

```
ffmpeg -f image2 -pattern_type glob -i '*.png' -vcodec qtrle chromakeyed.mov
```

All returned:
```
[image2 @ 0x1cb68c0] Could not find codec parameters for stream 0 (Video: png): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
*.png: could not find codec parameters
```

The files are named "Fire0000.png" counting up.

I furthermore tried

```
ffmpeg -f image2 -i Fire%04d.png -vcodec png chromakeyed.mov
```

and

```
ffmpeg -f image2 -i Fire%04d.png -s 720x480 -vcodec png chromakeyed.mov
```

Both return

```
[image2 @ 0x1cb68c0] Could not find codec parameters for stream 0 (Video: png): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Fire%04d.png: could not find codec parameters
```

The message "*.png: could not find codec parameters" only comes with ffmpeg 2.0.1. "glob -i '*.png'" worked with version N-53430-g2c2e69b from May 25 2013 05:26:47 but the results were crappy.

---

### Post by lukeiamyourfather on 2013-08-13
For starters I'd go with Libav. What are you trying to do with the videos? Some codecs are better than others depending on who/what needs to be able to decode the videos.

---

### Post by xxlray on 2013-08-14
> **lukeiamyourfather said:**
> For starters I'd go with Libav.
Is this just a guess or do you know it will work?

> **lukeiamyourfather said:**
> What are you trying to do with the videos?
It's a muzzle blast (gun fire) effect which I need to join to a video file for re-using it in one of my films. I know that this works in principle as I have another effect which has such an alpha channel.

> **lukeiamyourfather said:**
> Some codecs are better than others depending on who/what needs to be able to decode the videos.
As you can see I already tried different codecs. From the error message I guess that the error is in the file selection.

---

### Post by FakeOutdoorsman on 2013-08-15
Please provide a sample input PNG file.

---

### Post by xxlray on 2013-08-16
I'll attach some. These are the first frames from the CC BY licensed video "Machine_Gun_Muzzle_Flash_Final.mov" by footagecrate.com . I extracted them via avidemux and added the alpha channel in gimp.

---

### Post by FakeOutdoorsman on 2013-08-20
```
ffmpeg -i Fire%04d.png -codec:v qtrle output.mov
```
or
```
ffmpeg -pattern_type glob -i '*.png' -codec:v qtrle output.mov
```

Should both work with recent ffmpeg (not the old, buggy, fake "ffmpeg" from the repo). You can follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) or simply download and use a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds).

I recommend [stream copying](http://ffmpeg.org/ffmpeg.html#Stream-copy) the PNG images into a MOV container:
```
ffmpeg -i Fire%04d.png -codec:v copy output.mov
```

If your other software does not accept that then try qtrle as shown in the first two commands.

Also see [How to create an uncompressed AVI from a series of 1000's of PNG images using FFmpeg](http://superuser.com/a/347434/110524).

---

### Post by xxlray on 2013-08-21
> **FakeOutdoorsman said:**
> ```
ffmpeg -i Fire%04d.png -codec:v qtrle output.mov
```
Result with ffmpeg 2.0.1 is:```
[image2 @ 0x2be5840] Could not find codec parameters for stream 0 (Video: png): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Fire%04d.png: could not find codec parameters

```
The result with ffmpeg N-53430-g2c2e69b looks crappy (see attachment).

 Similar results for
```
ffmpeg -pattern_type glob -i '*.png' -codec:v qtrle output.mov
```

> **FakeOutdoorsman said:**
> not the old, buggy, fake "ffmpeg" from the repo
I downloaded the source and compiled it myself

> **FakeOutdoorsman said:**
> You can follow a [step-by-step guide to compile ffmpeg]("http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide") or simply download and use a [Linux build of ffmpeg]("http://ffmpeg.org/download.html#LinuxBuilds").
...
Also see [How to create an uncompressed AVI from a series of 1000's of PNG images using FFmpeg]("http://superuser.com/a/347434/110524").
Thanks for the advice but in principle I know how to do it (and did multiple times before). It's "just" this particular one which does not work.

---

### Post by FakeOutdoorsman on 2013-08-21
> **xxlray said:**
> Result with ffmpeg 2.0.1 is:```
[image2 @ 0x2be5840] Could not find codec parameters for stream 0 (Video: png): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Fire%04d.png: could not find codec parameters

```

Are the attached images from your earlier post all of the input images? I would need each of your input images to attempt to duplicate the issue.

> **xxlray said:**
> The result with ffmpeg N-53430-g2c2e69b looks crappy (see attachment).
According to which player(s)? It does not look great in ffplay, but it looks better in an After Effects composition, so it may still be usable in your other software.

---

### Post by xxlray on 2013-08-22
> **FakeOutdoorsman said:**
> Are the attached images from your earlier post all of the input images? I would need each of your input images to attempt to duplicate the issue.
I will attach all (and have to devide them into multiple posts to overcome forum limitations).


> **FakeOutdoorsman said:**
> According to which player(s)? It does not look great in ffplay
 It looks bad in VLC and is not even playable in avidemux (screen stays green). I use openshot for cutting my videos and the effect's background is white instead of transparent (covering the rest of the scene). Here is a comparison how I see it:

[ATTACH=CONFIG]245565[/ATTACH]

---

### Post by xxlray on 2013-08-22
Here is the rest and thanks for your efford.

---

### Post by FakeOutdoorsman on 2013-08-24
> **xxlray said:**
> 
```
[image2 @ 0x1cb68c0] Could not find codec parameters for stream 0 (Video: png): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
*.png: could not find codec parameters
```


I could not duplicate this behavior. Do you have an extra png file in there that is not part of the sequence but is being picked up by the glob pattern?

```
$ ffmpeg -f image2 -pattern_type glob -i '*.png' -c:v qtrle out.mov
ffmpeg version N-55663-g78d2a78 Copyright (c) 2000-2013 the FFmpeg developers
  built on Aug 20 2013 09:56:02 with gcc 4.8.1 (GCC) 20130725 (prerelease)
  configuration: --prefix=/usr --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libvorbis --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 42.100 / 52. 42.100
  libavcodec     55. 28.100 / 55. 28.100
  libavformat    55. 14.100 / 55. 14.100
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 82.100 /  3. 82.100
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
  libpostproc    52.  3.100 / 52.  3.100
Input #0, image2, from '*.png':
  Duration: 00:00:02.80, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: png, gray8a, 720x480 [SAR 2835:2835 DAR 3:2], 25 fps, 25 tbr, 25 tbn, 25 tbc
Output #0, mov, to 'out.mov':
  Metadata:
    encoder         : Lavf55.14.100
    Stream #0:0: Video: qtrle (rle  / 0x20656C72), argb, 720x480 [SAR 1:1 DAR 3:2], q=2-31, 200 kb/s, 12800 tbn, 25 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (png -> qtrle)
Press [q] to stop, [?] for help
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8  
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
Input stream #0:0 frame changed from size:720x480 fmt:gray8a to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:pal8
Input stream #0:0 frame changed from size:720x480 fmt:pal8 to size:720x480 fmt:rgba
Input stream #0:0 frame changed from size:720x480 fmt:rgba to size:720x480 fmt:gray8a
frame=   70 fps=0.0 q=0.0 Lsize=    7877kB time=00:00:02.80 bitrate=23044.9kbits/s    
video:7876kB audio:0kB subtitle:0 global headers:0kB muxing overhead 0.014260%
```
Notice that your input frames have varied pixel formats: rgba, pal8, and gray8a.

The qtrle output works ok for me (in After Effects), but it does not appear to be completely transparent. Of course I forgot to check a single PNG image to determine if it is the source that is the cause or the encoding.

---

### Post by xxlray on 2013-08-26
Now that I set also the filling frames to RGB the video looks still crappy in VLC but seems to work well in openshot. I still have the issue that ffmpeg 2.0.1 does not take the file pattern but the old version worked with the command "ffmpeg -f image2 -pattern_type glob -i '*.png' -vcodec qtrle chromakeyed.mov". Thanks for your effort.

---

