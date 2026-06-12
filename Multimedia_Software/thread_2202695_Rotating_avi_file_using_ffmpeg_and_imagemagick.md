---
title: "Rotating avi file using ffmpeg and imagemagick"
date: 2014-01-30
forum: Multimedia Software
---

### Post by rioguia2 on 2014-01-30
I am following the example for rotating movies 90 degrees using ffmpeg and imagemagick as suggested in another [thread]("http://ubuntuforums.org/showthread.php?t=1505084&p=9436397#post9436397"). The question I am asking how can I use ffmpeg to reassemble a movie clip from the images that is compatible with the original movies from which they were derived. 

i am making a movie out of many avi clips.  The movies were all shot with the same camera.  One of the clips was rotated at a 90 degree angle.  I need to rotate it.  I've tried many solutions like avidemux, etc. to rotate the films but the video frames become very uneven and the sound is far out of sync.  I am trying to export the avi movie to images using ffmpeg, editing them using imagemagick, and then reassembling them as an avi in a mode that matches the orginal movie.  After that i hope to add the sound back in like a sound track.

The question I am asking how can I use ffmpeg to create a movie from the images that is compatible with the originals.  The orginal movies have the following specifications:

```
ffmpeg -i MVI_0183.AVI

Input #0, avi, from 'MVI_0183.AVI':
  Metadata:
    creation_time   : 2003-08-16 11:02:42
    encoder         : CanonMVI01
  Duration: 00:00:03.19, start: 0.000000, bitrate: 2361 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 15 tbr, 15 tbn, 15 tbc
    Stream #0.1: Audio: pcm_u8, 11024 Hz, 1 channels, u8, 88 kb/s
```

In case you are interested, here are my steps to date.

1. strip individual images out of the movie (images are now 320x240)
```
ffmpeg -i MVI_0183.AVI image_dump/%d.png
```

2.  turn them on their side (images are now 240 x 320)
```
mogrify -rotate 90 image_dump/*.png
```

3. Then I made a directory temp inside directory image_dump so that I could preserve the above work and experiment a little.  I wanted to crop the bottom off the bottom of the image to make it 240x240 and then add a black border so that the rotated image returned to a 320x240 frame size.  When i was satisfied that the images were right, i used this command below:
```
mogrify -path temp -format png -gravity south -chop 0x80 -background black -extent 320x240 *.png
```

4. My next step is to use ffmpeg to reassemble the video.  Something like this???
```
ffmpeg -i temp/%d.png -o output.avi
```




FYI.  A more complete set of specifications is provided below:





```
mediainfo MVI_0183.AVI 
General
Complete name                            : MVI_0183.AVI
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 922 KiB
Duration                                 : 3s 200ms
Overall bit rate                         : 2 361 Kbps
Mastered date                            : Sat Aug 16 11:02:42 2003
Writing application                      : CanonMVI01

Video
ID                                       : 0
Format                                   : JPEG
Codec ID                                 : MJPG
Duration                                 : 3s 200ms
Bit rate                                 : 2 265 Kbps
Width                                    : 320 pixels
Height                                   : 240 pixels
Display aspect ratio                     : 4:3
Frame rate                               : 15.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:2
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 1.966
Stream size                              : 885 KiB (96%)

Audio
ID                                       : 1
Format                                   : PCM
Format settings, Sign                    : Unsigned
Codec ID                                 : 1
Duration                                 : 3s 200ms
Bit rate mode                            : Constant
Bit rate                                 : 88.2 Kbps
Channel(s)                               : 1 channel
Sampling rate                            : 11.024 KHz
Bit depth                                : 8 bits
Stream size                              : 34.4 KiB (4%)
Interleave, duration                     : 800 ms (12.00 video frames)
Interleave, preload duration             : 1000 ms
```

---

### Post by sudodus on 2014-01-30
It is possible to rotate the frames (picture) directly in ***ffmpeg***

See ```
man ffmpeg
```

Under the section

```
VIDEO FILTERS
       When you configure your Libav build, you can disable any of the existing filters using
       --disable-filters.  The configure output will show the video filters included in your
       build.

       Below is a description of the currently available video filters.

```

you find ***transpose***

```
   transpose
       Transpose rows with columns in the input video and optionally flip it.

       It accepts a parameter representing an integer, which can assume the values:

       0   Rotate by 90 degrees counterclockwise and vertically flip (default), that is:

                   L.R     L.l
                   . . ->  . .
                   l.r     R.r

       1   Rotate by 90 degrees clockwise, that is:

                   L.R     l.L
                   . . ->  . .
                   l.r     r.R

       2   Rotate by 90 degrees counterclockwise, that is:

                   L.R     R.r
                   . . ->  . .
                   l.r     L.l

       3   Rotate by 90 degrees clockwise and vertically flip, that is:

                   L.R     r.R
                   . . ->  . .
                   l.r     l.L

```

---

### Post by rioguia2 on 2014-01-30
thanks for your response.  I've used both ffmpeg and mencoder.  The problem is that shifting the images 90 degrees throws off the synchronization with the sound.  None of these solutions address that issue.

I'd like to see if someone can help me with the question i posed.  The question I am asking how can I use ffmpeg to create a movie from the images that is compatible with the originals?

Thanks

---

### Post by FakeOutdoorsman on 2014-01-30
You can skip imagemagick, and you can even perform the rotation losslessly:

**Get exiftran**:
```
sudo apt-get install exiftran
```

**Get ffmpeg**. Ubuntu doesn't use the real ffmpeg but you can easily download it:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
```

**Output the frames**. MJPEG is basically just a bunch of jpg images. This will use [stream copy](http://ffmpeg.org/ffmpeg-bitstream-filters.html#mjpeg2jpeg) mode and extract the actual jpg images (in addition to using the [mjpeg2jpeg bitstream filter](http://ffmpeg.org/ffmpeg-bitstream-filters.html#mjpeg2jpeg)) instead of re-encoding them. Notice the "./" before the "ffmpeg":
```
mkdir frames
./ffmpeg -i MVI_0183.AVI -codec:v copy -bsf:v mjpeg2jpeg frames/frame_%d.jpg
```

**Rotate the images**. You can do this losslessly with exiftran:
```
exiftran -i -9 frames/frame*.jpg
```

**Mux** the images into a video, and mux the audio from MVI_0183.AVI (again, no re-encoding is needed). Default input frame rate is 25, so you may have to change it to match your original input:
```
./ffmpeg -framerate 15 -i frames/frame_%d.jpg -i MVI_0183.AVI -codec copy -map 0:v -map 1:a rotated.avi
```

**Delete** the frames if you like:
```
rm -rf frames
```

---

### Post by rioguia2 on 2014-01-31
Thanks FakeOutdoorsman that's an amazing response. I noticed that the thread I used to start my project included your work as well.


I just added a step after rotating the .jpgs. The rotated.jpgs are oriented 240 wide X 320 high.  Because I'm trying to splice this onto an standard 320 wide x 240 high avi, i chop the bottom off (temporarily making the image 240 x 240) and then add side borders to provide the standard 320 wide x 240 high avi (an inelegant solution).  However, you copy codec made the frames match up perfectly.  I'm testing now to see if I can convert the output into a standard .vob DVD output.


```
mogrify -format jpg -gravity south -chop 0x80 -background black -extent 320x240 *.jpg
```

---

### Post by FakeOutdoorsman on 2014-01-31
You can also crop losslessly with jpegtran, but I'm not sure how to add the borders without re-encoding. Since re-encoding is required (because of the padding and because you want DVD video) you can just use ffmpeg to do everything:

```
ffmpeg -i MVI_0183.AVI -vf "transpose=1,crop=iw:240:0:0,pad=320:240:(ow-iw)/2:0" -target ntsc-dvd output.mpg
```

[list]
[*]This uses the [transpose](http://ffmpeg.org/ffmpeg-filters.html#transpose), [crop](http://ffmpeg.org/ffmpeg-filters.html#crop), and [pad](http://ffmpeg.org/ffmpeg-filters.html#pad) video filters. crop usually centers the cropping, but this example will cut off the bottom.
[*]If you want a PAL output, use "-target pal-dvd".
[*]You can then [use dvdauthor](http://ubuntuforums.org/showthread.php?t=2109334) to [assemble the mpeg program streams](http://ubuntuforums.org/showthread.php?p=12351726#post12351726) into a suitable DVD filesystem.
[/list]

I forgot to mention "-framerate" in my last post but I updated it. Don't forgot the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code) for your commands and console outputs.

---

### Post by rioguia2 on 2014-01-31
I can't wait to try it.  i love going directly to mpeg.

 I was working on my own solution but its in no way as elegant as yours.  

Here is what i did to assemble several clips into a single avi file.  The problem was that some clips were shot in portrait (i.e. at a 90 degree angle).  In needed to rotate them, making them 240 wide x 320 high).  In order for them to match the other clips, i had resize the rotated clips to the standard format (320 wide x 240 high), and conconcatinate them into a single avi file.  The basic problem I ran into was that despite all my best efforts, I was unable to match the rotated file to the original specifications for the files and, as a result, the sound was always wildly out of sequence. As a compromise, I ran all the files through the same basic process and got a single avi with the audio in sync with the video.

 Here are my notes on a successful attempt. 
[B]
for files that were shot in portrait (90 degree angle)[/B].  **i used the [COLOR=#ff0000]-ovc lavc[/COLOR] because i could not make mencoder simply copy and needed to pick some codec.  There may be better options but this one worked for me.**  [COLOR=#ff0000]the -vf invokes the scale video filter[/COLOR] which actually rotates and crops the clip)
```
mencoder MVI_0184.AVI -ovc lavc -oac copy -vf rotate=1,scale=320:-2,crop=320:240 -o mvi_0184.avi
```

**I used nearly the same processing for clips that were shot in standard format.  [COLOR=#ff0000]Note the: "-vf scale=320:-2,crop=320:240"[/COLOR] below.  Unlike above, we shouldn't need to use this bit since these files are already the correct size.  I suspect that this should be unnecssary ****[B](but it was the only way this amateur got this to work)**.[/B]
```
mencoder MVI_0462.AVI -ovc lavc -oac copy -vf scale=320:-2,crop=320:240 -o mvi_0462.avi
```

**after we have processed all the clips, I need to make a list so that I can conveniently concatenate the clips into a single file without all the typing.  Note that the file is created in the directory above the working directory.**
```
ls *.avi > ../list_avi.txt
```

**now I print the list of the processed clips to the screen in a single line that I can cut and paste into the terminal**.
```
tr '\n' ' ' < ../list_avi.txt
```

**now concatinatinate the processed clips**.
```
cat mvi_0007.avi mvi_0008.avi mvi_0014.avi mvi_0015.avi mvi_0016.avi mvi_0017.avi mvi_0147.avi mvi_0175.avi mvi_0182.avi mvi_0183.avi mvi_0184.avi mvi_0209.avi mvi_0210.avi mvi_0211.avi mvi_0212.avi mvi_0218.avi mvi_0219.avi mvi_0462.avi > movie_collection_05.avi
```

**copy the video and audio streams and generate an index for our final product.**
```
mencoder -forceidx -oac copy -ovc copy movie_collection_05.avi -o movie_collection_indexed_05.avi
```

---

### Post by rioguia2 on 2014-02-01
Thanks for sharing your answers with me.  It's great when people who obviously know what they are doing shine a light for us amateurs.

I've found that there might be some issues in how ffmpeg calculates the padding.  I looked at the examples at the FFMPEG site and the code you provided should work.  I am looking at some options to work around it but need to get some sleep first.  I think this approach makes so much sense I think i'm just missing something because I'm tired.

```
~/Videos/oldmovies4$ ffmpeg -i MVI_0469.AVI -vf "transpose=1,crop=iw:240:0:0,pad=320:240:(ow-iw)/2:0" -target ntsc-dvd output.mpg
ffmpeg version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:12:07 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, avi, from 'MVI_0469.AVI':
  Metadata:
    creation_time   : 2003-09-14 18:25:07
    encoder         : CanonMVI01
  Duration: 00:00:28.99, start: 0.000000, bitrate: 1561 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 15 tbr, 15 tbn, 15 tbc
    Stream #0.1: Audio: pcm_u8, 11024 Hz, 1 channels, u8, 88 kb/s
File 'output.mpg' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'yuvj422p' for codec 'mpeg2video', auto-selecting format 'yuv420p'
[buffer @ 0x844f000] w:320 h:240 pixfmt:yuvj422p
[scale @ 0x844e9e0] w:320 h:240 fmt:yuvj422p -> w:720 h:480 fmt:yuv420p flags:0x4
[transpose @ 0x845ed40] w:720 h:480 dir:1 -> w:480 h:720 rotation:clockwise vflip:0
[crop @ 0x845f1c0] [FONT=arial black][SIZE=4]**w:480 h:720 -> w:480 h:240**[/SIZE][/FONT]
[pad @ 0x844ef00] [COLOR=#ff0000]Negative values are not acceptable[/COLOR].
Error opening filters!
```

---

### Post by rioguia2 on 2014-02-01
I'm making some progress through reading and experimentation.  I don't understand all the parameters and how they work. Here is an example for an .avi clip shot in portrait (i.e. at a 90 degree angle, 240 wide x 320 high).  Transpose rotates the clip 90 degrees.  Crop cuts 240 pixels off the new top of the clip and outputs to 720 x 480 mpg.

```
ffmpeg -i MVI_0469.AVI -vf "transpose=1,crop=in_w:in_h-240:0:240:in_w*9/16:(ow-iw)/2:0" -target ntsc-dvd output8.mpg
```

---

### Post by FakeOutdoorsman on 2014-02-02
> **rioguia2 said:**
> ```
~/Videos/oldmovies4$ ffmpeg -i MVI_0469.AVI -vf "transpose=1,crop=iw:240:0:0,pad=320:240:(ow-iw)/2:0" -target ntsc-dvd output.mpg
ffmpeg version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:12:07 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
...
[pad @ 0x844ef00] Negative values are not acceptable.
Error opening filters!
```

I can't duplicate this issue, but I'm not using the fake "ffmpeg" from Libav. Try a recent build of ffmpeg from FFmpeg. You can simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

---

### Post by rioguia2 on 2014-02-02
I followed the installation instructions for ffmpeg.  Very smooth installation but the same result.

I editted to highlight a number that jumped out at me from the terminal.  It look's like I'm overshooting on the crop to 240 pixels.  Is that significant?


```
[crop @ 0x845f1c0] [FONT=arial black][SIZE=4]**w:480 h:720 -> w:480 h:240**[/SIZE][/FONT]
```

---

### Post by FakeOutdoorsman on 2014-02-03
Can you provide a short input sample if possible, your full ffmpeg command, and the complete console output?

---

### Post by rioguia2 on 2014-02-03
Here's the full command and screen output

```
 ffmpeg -i MVI_0183.AVI -vf "transpose=1,crop=iw:240:0:0,pad=320:240:(ow-iw)/2:0" -target ntsc-dvd output.mpg
ffmpeg version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:12:07 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, avi, from 'MVI_0183.AVI':
  Metadata:
    creation_time   : 2003-08-16 11:02:42
    encoder         : CanonMVI01
  Duration: 00:00:03.19, start: 0.000000, bitrate: 2361 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 15 tbr, 15 tbn, 15 tbc
    Stream #0.1: Audio: pcm_u8, 11024 Hz, 1 channels, u8, 88 kb/s
Incompatible pixel format 'yuvj422p' for codec 'mpeg2video', auto-selecting format 'yuv420p'
[buffer @ 0x86d3700] w:320 h:240 pixfmt:yuvj422p
[scale @ 0x86e33e0] w:320 h:240 fmt:yuvj422p -> w:720 h:480 fmt:yuv420p flags:0x4
[transpose @ 0x86d2c60] w:720 h:480 dir:1 -> w:480 h:720 rotation:clockwise vflip:0
[crop @ 0x86cb220] w:480 h:720 -> w:480 h:240
[pad @ 0x86cb860] Negative values are not acceptable.
Error opening filters!
```

here's a [link]("http://pytivo.sourceforge.net/forum/ffmpeg-negative-values-are-not-acceptable-error-hack-f-t2462.html") to an forum discussing this issue.

---

### Post by FakeOutdoorsman on 2014-02-06
You're using the fake "ffmpeg" again. If works fine with the real ffmpeg.

[size=5]Using ffmpeg from FFmpeg[/size]
```

$ ffmpeg -i MVI_0184.AVI -vf "transpose=1,crop=iw:240:0:0,pad=320:240:(ow-iw)/2:0" -target ntsc-dvd output.mpg
ffmpeg version N-60376-g9a4a559 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb  5 2014 10:59:38 with gcc 4.8.2 (GCC) 20131219 (prerelease)
  configuration: --prefix=/usr --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 63.100 / 52. 63.100
  libavcodec     55. 49.101 / 55. 49.101
  libavformat    55. 30.100 / 55. 30.100
  libavdevice    55.  7.100 / 55.  7.100
  libavfilter     4.  1.102 /  4.  1.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Guessed Channel Layout for  Input Stream #0.1 : mono
Input #0, avi, from 'MVI_0184.AVI':
  Metadata:
    creation_time   : 2003-08-16 11:03:02
    encoder         : CanonMVI01
  Duration: 00:00:04.53, start: 0.000000, bitrate: 2239 kb/s
    Stream #0:0: Video: mjpeg (MJPG / 0x47504A4D), yuvj422p(pc), 320x240, 15 tbr, 15 tbn, 15 tbc
    Stream #0:1: Audio: pcm_u8 ([1][0][0][0] / 0x0001), 11024 Hz, mono, u8, 88 kb/s
File 'output.mpg' already exists. Overwrite ? [y/N] y
[swscaler @ 0x154a880] deprecated pixel format used, make sure you did set range correctly
[swscaler @ 0x1551f20] deprecated pixel format used, make sure you did set range correctly
Output #0, dvd, to 'output.mpg':
  Metadata:
    encoder         : Lavf55.30.100
    Stream #0:0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
    Stream #0:1: Audio: ac3, 48000 Hz, mono, fltp, 448 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg -> mpeg2video)
  Stream #0:1 -> #0:1 (pcm_u8 -> ac3)
Press [q] to stop, [?] for help
frame=  119 fps=0.0 q=2.0 size=    2460kB time=00:00:03.96 bitrate=5085.5kbits/sframe=  135 fps=0.0 q=2.0 Lsize=    2842kB time=00:00:04.53 bitrate=5129.6kbits/s dup=67 drop=0    
video:2530kB audio:248kB subtitle:0 data:0 global headers:0kB muxing overhead 2.269339%
```

[size=5]Using buggy ffalse "ffmpeg" from libavthefork[/size]
```

$ /usr/bin/ffmpeg -i MVI_0184.AVI -vf "transpose=1,crop=iw:240:0:0,pad=320:240:(ow-iw)/2:0" -target ntsc-dvd output.mpg
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, avi, from 'MVI_0184.AVI':
  Metadata:
    creation_time   : 2003-08-16 11:03:02
    encoder         : CanonMVI01
  Duration: 00:00:04.53, start: 0.000000, bitrate: 2239 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 15 tbr, 15 tbn, 15 tbc
    Stream #0.1: Audio: pcm_u8, 11024 Hz, 1 channels, u8, 88 kb/s
File 'output.mpg' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'yuvj422p' for codec 'mpeg2video', auto-selecting format 'yuv420p'
[buffer @ 0xc836a0] w:320 h:240 pixfmt:yuvj422p
[scale @ 0xc83860] w:320 h:240 fmt:yuvj422p -> w:720 h:480 fmt:yuv420p flags:0x4
[transpose @ 0xc88dc0] w:720 h:480 dir:1 -> w:480 h:720 rotation:clockwise vflip:0
[crop @ 0xc81d40] w:480 h:720 -> w:480 h:240
[pad @ 0xc823a0] Negative values are not acceptable.
Error opening filters!
```

---

