---
title: "Mencoder trouble when creating timelapse (i need HD video output)"
date: 2011-09-20
forum: Multimedia Software
---

### Post by nahuel_89p on 2011-09-20
Hi, the thing is, I installed every package related to codecs, MPEG4, h264,x264, etc, but as try to create a video from few hundred JPG in mpeg4 and h264 codec i get an error.

This code, for example, works:
mencoder -nosound mf://*.JPG -mf w=1037:h=691:type=jpg:fps=30 -ovc lavc -lavcopts vcodec=msmpeg4:vbitrate=10000 -o out2.avi

how do i have to change these parameters to get a high definition video? (It goes beyond the width and height,im talking about keeping the jpg frames detail, avoiding any type of pixelation, etc)

Thanks in advance!

---

### Post by David Andersson on 2011-09-20
> **nahuel_89p said:**
> 
This code, for example, works:
mencoder -nosound mf://*.JPG -mf w=1037:h=691:type=jpg:fps=30 -ovc lavc -lavcopts vcodec=msmpeg4:vbitrate=10000 -o out2.avi

how do i have to change these parameters to get a high definition video? (It goes beyond the width and height,im talking about keeping the jpg frames detail, avoiding any type of pixelation, etc)


To retain as much details as possible I would recommend using the same resolution in the video as was in the jpegs. If the jpegs are 1037x691 then -mf w=1037:h=691 is alright, but you can skip the w= and h= arguments and the resolution should be autodetected.

As to what -lavcopts settings to optimize quality, see [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html) , the table in section "Encoding setting examples". (There are similar tables for the x264 and xvid codecs [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html) , [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html) ).

Two pass generally allow for better quality for a given bitrate, compared to one pass. For two pass encoding, issue the mencoder command twice. The first time add ":vpass=1:turbo" to the -lavcopts and set output to -o /dev/null. The second time add ":vpass=2" and set output to what you want (e.g. -o out2.avi).

---

### Post by nahuel_89p on 2011-09-20
> **David Andersson said:**
> To retain as much details as possible I would recommend using the same resolution in the video as was in the jpegs. If the jpegs are 1037x691 then -mf w=1037:h=691 is alright, but you can skip the w= and h= arguments and the resolution should be autodetected.

As to what -lavcopts settings to optimize quality, see [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html) , the table in section "Encoding setting examples". (There are similar tables for the x264 and xvid codecs [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html) , [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html) ).

Two pass generally allow for better quality for a given bitrate, compared to one pass. For two pass encoding, issue the mencoder command twice. The first time add ":vpass=1:turbo" to the -lavcopts and set output to -o /dev/null. The second time add ":vpass=2" and set output to what you want (e.g. -o out2.avi).

Thanks for the quick reply! Honestly i know nothing about all this codecs issue, sure i want to learn in the near future, but now im needing an effective command that outputs a good quality video. As for now, im googling. It seems that FFMPEG can do the same stuff, though again, im havin troubles.

---

### Post by David Andersson on 2011-09-20
> **nahuel_89p said:**
> Honestly i know nothing about all this codecs issue, sure i want to learn in the near future, but now im needing an effective command that outputs a good quality video.

The mencoder-command you have in the first post is almost there, isn't it? For good quality per bitrate you need some extra parameters in the -lavcopts option. What parameters to add there are stated verbatim in the table I mentioned, for different trade-offs between quality and speed. Choose best quality. You need to add bitrate parameter ":vbitrate=10000", but you already know that. Skip the two-pass bit if it is too complicated. Then you don't need to add any more parameters.

> **nahuel_89p said:**
> As for now, im googling. It seems that FFMPEG can do the same stuff, 

Yes, I think it can, but I am less experienced with it.

> **nahuel_89p said:**
> though again, im havin troubles.

You mentioned an error in the first post, but also that the command worked. What *is* the trouble? (The two elements of a proper error report is "what I did", "what I expected for result" and "what I got instead". No, thats three. Maybe it's four. I've forgotten.)

---

### Post by David Andersson on 2011-09-20
> **David Andersson said:**
> Then you don't need to add any more parameters.

Maybe one more thing. You may need to supply the frame rate both in the -mf option and in an -ofps option. That is *-mf type=jpg:fps=30 -ofps 30*

---

### Post by nahuel_89p on 2011-09-21
Thanks David, adding some extra parameters and incresing bitrate did it very well. However, i want to encode using h264 codec.

I particularly have troubles with this code i found (this worked for the guy that posted it):

```
mencoder "mf://*.JPG" -vf scale=1920:1080 -o 256.avi -ovc x264 -x264encopts pass=1:bitrate=20000:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:threads=4
```



It returns:

```
MEncoder 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
Option x264encopts: Bad argument b_pyramid=(null)
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.JPG
[mf] number of files: 1190 (4760)
[demux_mf] file type was not set! trying 'type=JPG'...
VIDEO:  [IJPG]  0x0  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps:25.000  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=1920 h=1080]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xbbd180]BICUBIC scaler, from yuv422p to yuv420p using MMX2
FATAL: Cannot initialize video driver.
Movie-Aspect is undefined - no prescaling applied.
FATAL: Cannot initialize video driver.

Exiting...driver.

Exiting...
```

---

### Post by nahuel_89p on 2011-09-21
As i found some instructions in the web you suggested me to read, i tried to follow:

> 2.5.2. x264

x264 is a library for creating H.264 video. MPlayer sources are updated whenever an x264 API change occurs, so it is always suggested to use MPlayer from Subversion.

If you have a GIT client installed, the latest x264 sources can be gotten with this command:

git clone git://git.videolan.org/x264.git
Then build and install in the standard way:

./configure && make && make install
Now rerun ./configure for MPlayer to pick up x264 support.

Is there any missing step there? I mean, i need literally, every command to be put, in the right order.

How do i "rerun" ./configure for mplayer? It's kinda confusing, im using mencoder, though i think both share the same libs, etc.

---

### Post by nahuel_89p on 2011-09-21
I also have problems with this x264 command:

```
mencoder mf://*.JPG -mf fps=30:type=jpeg -noskip -of lavf -lavfopts format=mov -ovc lavc -lavcopts vglobal=1:coder=0:vcodec=libx264:vbitrate=5000 -vf scale=1280:-2 -o la.mov
```

as i get:

```
MEncoder 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.JPG
[mf] number of files: 1190 (4760)
VIDEO:  [IJPG]  0x0  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps:30.000  ftime:=0.0333
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B-frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit.
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=1280 h=-2]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x96eac70]BICUBIC scaler, from yuv422p to yuv420p using MMX2
videocodec: libavcodec (1280x854 fourcc=34363268 [h264])
[COLOR="red"][libx264 @ 0x96db3f0]broken ffmpeg default settings detected
[libx264 @ 0x96db3f0]use an encoding preset (vpre)[/COLOR]
Could not open codec.
FATAL: Cannot initialize video driver.
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (1280x854 fourcc=34363268 [h264])
[COLOR="Red"][libx264 @ 0x96db3f0]broken ffmpeg default settings detected
[libx264 @ 0x96db3f0]use an encoding preset (vpre)[/COLOR]
Could not open codec.
FATAL: Cannot initialize video driver.

Exiting...

```

(i put the red words because that's the way the are shown in my console)

---

### Post by FakeOutdoorsman on 2011-09-21
FFmpeg can do this as you've mentioned. Note that your input images must be in sequential order starting with "1": such as *img0001.jpg*, or *1.png* and so on.

First you may need to enable the libx264 encoder in the repository ffmpeg. You just need to install one package as shown here in Option B or C:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

The current syntax for the repository ffmpeg is:
```
ffmpeg -i img%04d.jpg -vcodec libx264 -vpre medium -crf 24 -threads 0 output.mp4
```

General practice for using the presets and crf is:
[list=1]
[*]use the slowest preset that you have patience for. In order of speed the presets are: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow.
[*]use the highest crf that still gives an acceptable quality
[*]use those settings for the rest of your "set" of inputs
[/list]

FFmpeg will use a default frame rate of 25 for the input (and subsequently the output) if you don't tell it otherwise with the *-r* option. This option can be independently applied to both the input and output, but frames may be dropped or duplicated to reach your desired rates.

See [FFmpeg FAQ: How do I encode single pictures into movies?](http://ffmpeg.org/faq.html#SEC14) for more info.

As of Natty, Ubuntu has moved from FFmpeg to the libav fork, so "ffmpeg" from the repo refers to the binary of the same name from libav due to the (personal?) preference of the maintainer. The binary been renamed from *ffmpeg* to *avconv* upstream. Ubuntu has yet to provide a binary from FFmpeg and I'm unsure if it will be anytime soon.

---

### Post by nahuel_89p on 2011-09-21
Thanks a lot to both!
I just find that this mencoder works for me:
```
mencoder "mf://*.JPG" -nosound -ovc x264 -x264encopts pass=1:bitrate=16000 -o kaaaaaaa.avi -mf type=jpg:fps=30
```

However, this is AVI. Vimeo suggests mp4 container, with H.264 codec. :S

> **FakeOutdoorsman said:**
> FFmpeg can do this as you've mentioned. Note that your input images must be in sequential order starting with "1": such as *img0001.jpg*, or *1.png* and so on.

First you may need to enable the libx264 encoder in the repository ffmpeg. You just need to install one package as shown here in Option B or C:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

The current syntax for the repository ffmpeg is:
```
ffmpeg -i img%04d.jpg -vcodec libx264 -vpre medium -crf 24 -threads 0 output.mp4
```

General practice for using the presets and crf is:
[list=1]
[*]use the slowest preset that you have patience for. In order of speed the presets are: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow.
[*]use the highest crf that still gives an acceptable quality
[*]use those settings for the rest of your "set" of inputs
[/list]

FFmpeg will use a default frame rate of 25 for the input (and subsequently the output) if you don't tell it otherwise with the *-r* option. This option can be independently applied to both the input and output, but frames may be dropped or duplicated to reach your desired rates.

See [FFmpeg FAQ: How do I encode single pictures into movies?](http://ffmpeg.org/faq.html#SEC14) for more info.

As of Natty, Ubuntu has moved from FFmpeg to the libav fork, so "ffmpeg" from the repo refers to the binary of the same name from libav due to the (personal?) preference of the maintainer. The binary been renamed from *ffmpeg* to *avconv* upstream. Ubuntu has yet to provide a binary from FFmpeg and I'm unsure if it will be anytime soon.

Thanks! I will try with FFMPEG. Is there any big difference? Which is better (mencoder vs ffmpeg)?

My aim is to compose really HD videos out of single jpg photographies. A time lapse, as i said. I see i have plenty of things and parameters to test yet.

Is there any difference between AVI and MP4 as containers of H.264 codec??

---

### Post by FakeOutdoorsman on 2011-09-21
> **nahuel_89p said:**
> Thanks! I will try with FFMPEG. Is there any big difference? Which is better (mencoder vs ffmpeg)?
I heard that MEncoder development isn't very active, but I haven't really followed it closely. FFmpeg/libav development is so active that an annoying side effect is the occasional syntax change. My preference is FFmpeg, but of course you should try them both and decide for yourself.

> **nahuel_89p said:**
> I see i have plenty of things and parameters to test yet.
The presets were designed to save time for the end user. They will provide the proper options automatically. You didn't provide any details on how you're planning on using the output so my example may need to changes to give you what you want.

> **nahuel_89p said:**
> Is there any difference between AVI MP4 as containers of H.264 codec??
Yes. AVI doesn't properly support b-frames, and my example will utilize b-frames. AVI is probably fine if you avoid using b-frames. AVI is an aging container format and I don't often recommend it.

---

### Post by nahuel_89p on 2011-09-21
> **FakeOutdoorsman said:**
> FFmpeg can do this as you've mentioned. Note that your input images must be in sequential order starting with "1": such as *img0001.jpg*, or *1.png* and so on.

First you may need to enable the libx264 encoder in the repository ffmpeg. You just need to install one package as shown here in Option B or C:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

The current syntax for the repository ffmpeg is:
```
ffmpeg -i img%04d.jpg -vcodec libx264 -vpre medium -crf 24 -threads 0 output.mp4
```

General practice for using the presets and crf is:
[list=1]
[*]use the slowest preset that you have patience for. In order of speed the presets are: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow.
[*]use the highest crf that still gives an acceptable quality
[*]use those settings for the rest of your "set" of inputs
[/list]

FFmpeg will use a default frame rate of 25 for the input (and subsequently the output) if you don't tell it otherwise with the *-r* option. This option can be independently applied to both the input and output, but frames may be dropped or duplicated to reach your desired rates.

See [FFmpeg FAQ: How do I encode single pictures into movies?](http://ffmpeg.org/faq.html#SEC14) for more info.

As of Natty, Ubuntu has moved from FFmpeg to the libav fork, so "ffmpeg" from the repo refers to the binary of the same name from libav due to the (personal?) preference of the maintainer. The binary been renamed from *ffmpeg* to *avconv* upstream. Ubuntu has yet to provide a binary from FFmpeg and I'm unsure if it will be anytime soon.

I followed:
```
ffmpeg -i img%04d.jpg -vcodec libx264 -vpre medium -crf 24 -threads 0 output.mp4
```

But i got:

```
ffmpeg version N-32748-g358d837, Copyright (c) 2000-2011 the FFmpeg developers
  built on Sep 21 2011 01:08:44 with gcc 4.5.2
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
  libavutil    51. 16. 1 / 51. 16. 1
  libavcodec   53. 16. 0 / 53. 16. 0
  libavformat  53. 12. 0 / 53. 12. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 43. 2 /  2. 43. 2
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, image2, from 'img%04d.jpg':
  Duration: 00:00:05.76, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 1728x1152, 25 fps, 25 tbr, 25 tbn, 25 tbc
File for preset 'medium' not found

```

Somehow, the presets aren't installed.
Previously, i had followed the instructions here [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) And no problem showed up, apparently. Every instruction succeded. I entered every single instruction.

P.D: I also have installed  libavcodec-extra-52 and did the medibuntu stuff.

---

### Post by nahuel_89p on 2011-09-21
[B][COLOR="Red"]SOLVED IT!
[/COLOR][/B]
I dived to \usr\local\share\ffmpeg  and found the presets, which aren't named as you said! I guess it must be one of those syntax changes, right??

They are named:
libvpx-360p
libvpx-720p
libvpx-720p50_60
libvpx-1080p
libvpx-1080p50_60
libx264-ipod320
libx264-ipod640
libx264-lossless_fast
libx264-lossless_max
libx264-lossless_medium
libx264-lossless_slow
libx264-lossless_slower
libx264-lossless_ultrafast

I tested one so far, it works!

Thanks! Now i finally got my mp4 encoded with H.264!

---

### Post by nahuel_89p on 2011-09-21
One last question, how do i set properly the bitrate and fps? They aren't included in the presets. So far i don't get the same quality i did with mencoder and AVI. Less contrast and saturation, looks poor.

And what about 2 pass encoding? :S

---

### Post by FakeOutdoorsman on 2011-09-21
> **nahuel_89p said:**
> Somehow, the presets aren't installed.
Previously, i had followed the instructions here [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
I assumed you were using ffmpeg from the repository and didn't know you compiled it. Yes, there is currently a syntax difference between the older ffmpeg from the repository and ffmpeg compiled from "Git HEAD" when it comes to using x264 presets. The older ffmpeg uses text files in */usr/share/ffmpeg* that roughly approximated the x264 presets, while a more recent ffmpeg is directly mapped to the standard x264 presets.

> **nahuel_89p said:**
> P.D: I also have installed  libavcodec-extra-52 and did the medibuntu stuff.
This shouldn't affect your compiled ffmpeg so you don't really need it, but I doubt it will cause any issues.

> **nahuel_89p said:**
> So far i don't get the same quality i did with mencoder and AVI. Less contrast and saturation, looks poor.
I'm guessing your command is probably wrong because my first example was designed for ffmpeg from the repository. Since you compiled it then your command may look like:
```
ffmpeg -i img%04d.jpg -vcodec libx264 -preset medium -crf 24 -threads 0 output.mp4
```

> **nahuel_89p said:**
> One last question, how do i set properly the bitrate and fps?
Change the quality (and thus the bitrate) with the *crf* option. A lower value is a higher quality. Start at *-crf 24* and go up or down depending on your needs.

> **FakeOutdoorsman said:**
> FFmpeg will use a default frame rate of 25 for the input (and subsequently the output) if you don't tell it otherwise with the *-r* option. This option can be independently applied to both the input and output, but frames may be dropped or duplicated to reach your desired rates.
An example. If you have 450 input images and want a 10 second long movie with an output frame rate of 30 fps. 450/10=[color=#009900]45[/color].
```
ffmpeg -r [color=#009900]45[/color] -i img%04d.jpg -vcodec libx264 -preset medium -crf 24 -threads 0 -r 30 output.mp4
```

> **nahuel_89p said:**
> And what about 2 pass encoding? :S
Two pass encoding is generally used when you are attempting to make your output file a specific file size. If you don't really care about that then you don't need to spend the extra time performing an additional pass. Single-pass CRF mode (as all of my examples in this thread are) uses as many (or few) bits as needed to reach the specified quality, while conversely, a two-pass encode will vary CRF value to reach a requested file size. To Generalize: you use single-pass CRF when you want a specific quality (controlled with the *crf* option), and use two-pass when you want a specific output file size.

---

### Post by nahuel_89p on 2011-09-22
Thanks a lot! It works, really. You are awesome!!

Here i uploaded two versions of the same video, a 4 seconds timelapse, using both MEncoder AVI and FFMPEG H.264.

What do you think? The H.264 seems to lose contrast and saturation, but it keeps more detail in the shadows.
In any case, in these photographs i set wrong the white balance and everything looks too red. A better comparison can take place with a different scenario, daylight, more colors, etc.
 

[http://vimeo.com/29444058](http://vimeo.com/29444058) - mencoder "mf://*.jpg" -mf fps=30 -o output1.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=6000

[http://vimeo.com/29443952](http://vimeo.com/29443952) - ffmpeg -r 30 -i img%04d.jpg -vcodec libx264 -preset slower -crf 22 -threads 0 -r 30 limado2.mp4

What do you think?

---

### Post by FakeOutdoorsman on 2011-09-22
I believe Vimeo will re-encode whatever you upload, so the videos on Vimeo can't be considered a direct comparison. Does the avi or the mp4 look more like the source images? Higher contrast can mean less detail and may be a result of comparatively more data loss due to the encoding process.

Now that you got a working command you can try lossless H.264. I'm not sure if Vimeo supports it, but you can try:
```
ffmpeg -r 30 -i img%04d.jpg -vcodec libx264 -vpre lossless_slow -threads 0 limado_lossless.mp4
```
This can create a relatively large file size. I removed the *-r 30* for the output because FFmpeg will inherit the input frame rate unless you tell it otherwise, but it doesn't really matter if you give it the same value for input and output.

---

### Post by nahuel_89p on 2011-09-22
That lossless command works. However, the video file can't be played by totem or VLC properly, it looks really really choppy (i think choppy is the right word in english, opposed to smooth, interrupted play). Exactly the same happens when i decrease the crf value in the other command. Unplayable large video.
I'm not sure, but it kinda makes sense. 130MB for a 4 seconds video is crazy. I guess it also must be the fact that I'm working with 1700*1100 px photographs. An unnecesary high-res level. It's a matter of batch resizing, however.

Regarding the comparison, the AVI file looks almost identical to the original photographs. That's not the case with the H.264. Lacks contrast :S  (i compared from my computer video files, not vimeo, in any case, it's the same result).

---

### Post by nahuel_89p on 2011-09-22
Here you can compare: The original, the AVI, and the H.264.

[IMG]http://i475.photobucket.com/albums/rr112/nahuel_89p/img0000.jpg[/IMG]

[IMG]http://i475.photobucket.com/albums/rr112/nahuel_89p/Pantallazo-1-1.jpg[/IMG]

[IMG]http://i475.photobucket.com/albums/rr112/nahuel_89p/Pantallazo.jpg[/IMG]



There are 2 threads here: [http://community.avid.com/forums/t/64027.aspx](http://community.avid.com/forums/t/64027.aspx) [http://www.dvinfo.net/forum/digital-compositing-effects/73197-h-264-brightness-contrast-issue.html](http://www.dvinfo.net/forum/digital-compositing-effects/73197-h-264-brightness-contrast-issue.html) 

In the second thread i found this explanation: "maybe you didn't use the RGB color levels? if you use 601/709 black is at "16" and white at "235". this gives you a reduced contrast."

This kinda applies to my issue. It seems, clearly, that there is a shorter dynamic range in the H.264 output. It's clear that for example, it doesn't clip highlight pixels (I myself measured with GIMP: RGB value takes 235,235,235 values in the highlights, while in the AVI file the highlights take the value of 255,255,255) in the sky area and in the street light.

---

### Post by FakeOutdoorsman on 2011-09-22
> **nahuel_89p said:**
> That lossless command works. However, the video file can't be played by totem or VLC properly, it looks really really choppy (i think choppy is the right word in english, opposed to smooth, interrupted play). Exactly the same happens when i decrease the crf value in the other command. Unplayable large video.
I'm not sure, but it kinda makes sense. 130MB for a 4 seconds video is crazy.
A lossless video may not play smoothly, but that does not matter if Vimeo can use it as an input. Since Vimeo re-encodes anything you upload you generally want to give it the best quality you can. If Vimeo supports a lossless input, and if you have a suitable internet connection then uploading a lossless video makes sense.

The lossless video in your case is not intended for playback, but as a lossless intermediate file that Vimeo can use to re-encode.

> **nahuel_89p said:**
> I guess it also must be the fact that I'm working with 1700*1100 px photographs. An unnecesary high-res level. It's a matter of batch resizing, however.
You can use the scale filer as an output option to tell ffmpeg to scale your images. This allows you to keep the input images at their original size. Examples:
```
-vf scale=1280:828
-vf scale=1280:-1
```
These two scale examples would both resize your 1700x1100 input to 1280x828. The -1 tells ffmpeg to scale the height automatically while keeping the aspect ratio. With your input size and the requested 1280 output width the height would end up being 828.

---

### Post by nahuel_89p on 2011-09-22
I see. Ok, thanks a lot! I bet this thread will be useful for more people.

Now, i couldn't solve the dynamic range issue, though Im investigating against a very steep learning curve. It's a serious issue, FFMPEG is shortening the dynamic range of the picture. The whitest pixel is 235,235,235, and the darkest is 16,16,16, while it should be 255,255,255 0,0,0. The result is a greyish video. It's unuseful at all!

---

### Post by nahuel_89p on 2011-09-22
Update:

Given the fact that i still can't make FFMPEG output a mp4 H.264 video without the short dynamic range issue, i managed to do it with MEncoder.

This is the command:
```
mencoder "mf://*.jpg" -nosound -of lavf -lavfopts format=mp4 -ovc x264 -x264encopts pass=1:bitrate=8000:crf=20 -o lights.mp4 -mf type=jpg:fps=30
```
No shortened dynamic range here. Looks just fine.
Note: To change quality, change the parameters bitrate and crf. The higher the bitrate, the better. The lower the crf, the better.

However, i would really like to have FFMPEG doing the same... looks a better app overall.

:-k

---

### Post by FakeOutdoorsman on 2011-09-22
Are you sure it's not your player? What player are you using? Does *ffplay* work as expected?

---

### Post by nahuel_89p on 2011-09-22
Sure. Check the vimeo links. I bet it look like that on every computer.

One last question, just not to open another thread. I want to put a mp3 or aac track to a video. There are apps like pitivi or openshot, but im afraid they will re-encode my video, losing quality. How do i just add a music track without re-encoding video again?
I know ffmpeg or mencoder can do that, but im afraid it will make both tracks (audio and video) starts at the same time, and i want the sound track to start playing few seconds before the video track starts.

---

