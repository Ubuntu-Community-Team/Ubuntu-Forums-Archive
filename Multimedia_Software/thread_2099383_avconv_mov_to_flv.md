---
title: "avconv mov to flv"
date: 2012-12-29
forum: Multimedia Software
---

### Post by GrouchyGaijin on 2012-12-29
Hi Guys,

I've been using ffmpeg to convert both .avi and .mov files to .flv files which I put on a website. (These are just home movies.)

Today I noticed a blurb fly by after I entered the alias from my .Bash_aliases file into the terminal.  The blurb said that I should use avconv, so I thought I'd give it a shot.

Well I can convert .mp4 files just fine using:
```
avconv -i foo.mp4 -s 320x240 -ar 22050 bar.flv
```

but if I use:
```
avconv -i foo.mov -s 320x240 -ar 22050 bar.flv
```
with .mov files shot on an iPhone, the resulting flash video is elongated.

so I tried ```
avconv -i foo.mov -ar 22050 bar.flv
```
and the resulting flash video is jerky.

Does anyone have any recommendations?

I appreciate the help.

---

### Post by andrew.46 on 2012-12-30
Can you post the full command and terminal output from the command that does not resize the video? As an aside I should mention that there would not be any problem using FFmpeg itself particularly if you used a modern version of it:

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Highly recommended if you are a serious video converter...

---

### Post by GrouchyGaijin on 2012-12-31
I tried again going from a .mov file from the iPhone to Flash.  Below is the command and terminal output:

```
$ avconv -i foo.mov -s 320x240 -ar 22050 bar.flv
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'foo.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2012-12-31 13:19:43
  Duration: 00:00:38.80, start: 0.000000, bitrate: 5341 kb/s
    Stream #0.0(und): Video: h264 (Baseline), yuv420p, 960x540, 5235 kb/s, 30 fps, 30 tbr, 600 tbn, 1200 tbc
    Metadata:
      creation_time   : 2012-12-31 13:19:43
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 110 kb/s
    Metadata:
      creation_time   : 2012-12-31 13:19:43
[buffer @ 0x8ed9160] w:960 h:540 pixfmt:yuv420p
[scale @ 0x8ed5ee0] w:960 h:540 fmt:yuv420p -> w:320 h:240 fmt:yuv420p flags:0x4
Output #0, flv, to 'bar.flv':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2012-12-31 13:19:43
    encoder         : Lavf53.21.0
    Stream #0.0(und): Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s, 1k tbn, 30 tbc
    Metadata:
      creation_time   : 2012-12-31 13:19:43
    Stream #0.1(und): Audio: libmp3lame, 22050 Hz, stereo, s16, 200 kb/s
    Metadata:
      creation_time   : 2012-12-31 13:19:43
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> flv)
  Stream #0:1 -> #0:1 (aac -> libmp3lame)
Press ctrl-c to stop encoding
frame= 1162 fps= 80 q=3.9 Lsize=    1910kB time=38.73 bitrate= 403.9kbits/s    
video:1109kB audio:759kB global headers:0kB muxing overhead 2.238796%

```

In the second test I removed the dimensions from the command.
```
$ avconv -i foo.mov -ar 22050 bar.flv
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'foo.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2012-12-31 13:19:43
  Duration: 00:00:38.80, start: 0.000000, bitrate: 5341 kb/s
    Stream #0.0(und): Video: h264 (Baseline), yuv420p, 960x540, 5235 kb/s, 30 fps, 30 tbr, 600 tbn, 1200 tbc
    Metadata:
      creation_time   : 2012-12-31 13:19:43
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 110 kb/s
    Metadata:
      creation_time   : 2012-12-31 13:19:43
[buffer @ 0x9789160] w:960 h:540 pixfmt:yuv420p
Output #0, flv, to 'bar.flv':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2012-12-31 13:19:43
    encoder         : Lavf53.21.0
    Stream #0.0(und): Video: flv, yuv420p, 960x540, q=2-31, 200 kb/s, 1k tbn, 30 tbc
    Metadata:
      creation_time   : 2012-12-31 13:19:43
    Stream #0.1(und): Audio: libmp3lame, 22050 Hz, stereo, s16, 200 kb/s
    Metadata:
      creation_time   : 2012-12-31 13:19:43
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> flv)
  Stream #0:1 -> #0:1 (aac -> libmp3lame)
Press ctrl-c to stop encoding
frame= 1162 fps= 57 q=31.0 Lsize=    5584kB time=38.73 bitrate=1181.0kbits/s    
video:4783kB audio:759kB global headers:0kB muxing overhead 0.754517%

```

Today in my short 38 second video test. The second Flash video doesn't seem jerky, so I guess it is OK.

I'm curious why you would recommend FFmpeg over avconv?  I'm not really a "serious" video converter, I'm not ripping DVDs.  I am taking video from an iPhone and another digital camera and putting it on the web.  The video is of our kids and I post them so both sets of Grandparents can view them.  

So, why not just use YouTube, you ask?  Well, it seems that the Grandparents in Japan have had a really big problem with YouTube lagging and they say it's easier to view if I put the videos on my site.  I've tried a few different formats and the flv that I'm using seems to load the quickest and has OK quality.

I'm just flying by the seat of my pants here, so any advice from someone who actually knows what they are doing would be much appreciated.

---

### Post by andrew.46 on 2012-12-31
There are much more skilled FFmpeg users on these Forums than myself but perhaps I can make a few observations:

Firstly I note that your original file contains h264 video and aac audio both of which actually live quite comfortably in a flv container. When you accept the FFmpeg/avconv defaults you actually get flv video and mp3 sound in an flv container, not a great problem but just be aware that you could probably just transfer the existing codecs to a new container. I see from your post that you have already experimented a little with this and other containers.

If your copy of avconv has access to the video filter *scale* perhaps try something like:

```

avconv -i foo.mov \
       -c:v flv -q:v 5 -vf scale=320:-1 \
       -c:a libmp3lame -q:a 3 \
       bar.flv

```

and add any necessary embellishments to the commandline as required. This may be enough to get decent quality sound and video and certainly the syntax I have suggested with the scale filter should resize things nicely. (The -1 for height resizes as appropriate to maintain the aspect ratio.) Experiment a little with the video *-q:v 5* setting until you are happy, a setting of *1* will be very high quality while a setting of *21* would be very low quality.

As for suggesting FFmpeg there are several reasons:

[LIST]
[*]A lot of the expert help on these Forums, and I do not include myself in this in this group of experts, comes from people using FFmpeg rather than avconv, including the maintainer of the guide I mentioned.
[*]It is better to use a cutting edge copy of FFmpeg/avconv rather than the repository offering and there is only an FFmpeg guide for this purpose.
[*]You and I would then be using the same version of FFmpeg and there would be no discrepance in terms of syntax, fiters etc.
[*]When the big fork occurred I fell down on the FFmpeg side :)
[/LIST]

Let me know how you go with this, hopefully this will make the grandparents happy :)

---

### Post by GrouchyGaijin on 2013-01-02
> **andrew.46 said:**
> 

As for suggesting FFmpeg there are several reasons:

[LIST]
[*]A lot of the expert help on these Forums, and I do not include myself in this in this group of experts, comes from people using FFmpeg rather than avconv, including the maintainer of the guide I mentioned.
[*]It is better to use a cutting edge copy of FFmpeg/avconv rather than the repository offering and there is only an FFmpeg guide for this purpose.
[*]You and I would then be using the same version of FFmpeg and there would be no discrepance in terms of syntax, fiters etc.
[*]When the big fork occurred I fell down on the FFmpeg side :)
[/LIST]

Let me know how you go with this, hopefully this will make the grandparents happy :)

Alrighty then, those reasons make sense to me.  Plus the guide is so well setup that even a hobbiest like myself can follow the steps to compile and install the dev version of ffmpeg.

So if I want to go from .mov to .flv at  320x240 with audio at 22050.  What would the command be?

Also on another note, some of our video comes from a camera that shoots mpg files.  I've been combining all the mpg files into one using the cat command.
```
cat video1.mpg video2.mpg > output.mpg
```

I've noticed that in Movie Player the output.mpg only plays as far as the fisrt video in the sequence.  In VLC, however, the entire output video will play, but it only displays time for the length of the first segment - thereafter the video continues to play as it should except the time has stopped moving forward.

Is this normal?

---

### Post by andrew.46 on 2013-01-03
> **GrouchyGaijin said:**
> 
So if I want to go from .mov to .flv at  320x240 with audio at 22050.  What would the command be?

Just add that into the audio line:

```

-c:a libmp3lame -q:a 3 **[COLOR="Red"]-ar 22050[/COLOR]**

```

Bear in mind that you only specify the width of the output image, avconv decides on the height while maintaining the aspect ratio.


> Also on another note, some of our video comes from a camera that shoots mpg files.  I've been combining all the mpg files into one using the cat command.
```
cat video1.mpg video2.mpg > output.mpg
```

I've noticed that in Movie Player the output.mpg only plays as far as the fisrt video in the sequence.  In VLC, however, the entire output video will play, but it only displays time for the length of the first segment - thereafter the video continues to play as it should except the time has stopped moving forward.

Is this normal?

I have not had much to do with concatenating videos although it sounds from your example that there are some pitfalls :). Have a look here for some guidance:

3.14 How can I concatenate video files?
[http://ffmpeg.mplayerhq.hu/faq.html#How-can-I-concatenate-video-files_003f](http://ffmpeg.mplayerhq.hu/faq.html#How-can-I-concatenate-video-files_003f)

I like the look of the new concat demuxer. Sorry I cannot be much help on this one...

---

### Post by GrouchyGaijin on 2013-01-03
> **andrew.46 said:**
> 
I like the look of the new concat demuxer. Sorry I cannot be much help on this one...
Thanks, that brings up another question.  What is demuxing? (What is the concat demuxer?)

---

### Post by andrew.46 on 2013-01-03
> **GrouchyGaijin said:**
> Thanks, that brings up another question.  What is demuxing? (What is the concat demuxer?)

I am sorry, I suspect I am making things a little too complex :(. A demuxer (= demu*ltiple*xer) extracts individual streams and sends them for encoding. The concat *demuxer* looks like it really should not be needed in your case as mpg files should join with *cat*. In the case where file level concatenation can be used the docs suggest you still can use the concat protocol as follows:

```

ffmpeg -i concat:"intermediate1.mpg|intermediate2.mpg" -c copy intermediate_all.mpg

```

Or perhaps simply reencode you final file with the faulty index and all will be well :)

---

### Post by FakeOutdoorsman on 2013-01-03
I recommend using *libx264* instead of *flv1* for flv container if possible. flv1 is not great, and just about everyone these days uses H.264 instead. You can get decent results with flv1, but it will require more bitrate for a similar quality which means a larger file size.

Your foo.mov contains AAC audio which can simply be copied into the flv file as Andrew mentioned. Same for the video stream, but a 25 MB video stream for a 38 second video may require re-encoding to get a more manageable size depending on your viewer's bandwidth.

---

### Post by GrouchyGaijin on 2013-01-03
> **FakeOutdoorsman said:**
> I recommend using *libx264* instead of *flv1* for flv container if possible. flv1 is not great, and just about everyone these days uses H.264 instead. You can get decent results with flv1, but it will require more bitrate for a similar quality which means a larger file size.

Your foo.mov contains AAC audio which can simply be copied into the flv file as Andrew mentioned. Same for the video stream, but a 25 MB video stream for a 38 second video may require re-encoding to get a more manageable size depending on your viewer's bandwidth.
Hey thanks!

I just tried both:
```
ffmpeg -i IMG_1770.mov \
       -c:v flv -q:v 5 -vf scale=320:-1 \
       -c:a libmp3lame -q:a 3 \
       Mov-to-flv.flv
```

and
```
ffmpeg -i IMG_1770.mov \
       -c:v libx264 -q:v 5 -vf scale=320:-1 \
       -c:a libmp3lame -q:a 3 \
       Mov-to-libx264.flv
```

In my test of a 47 second clip the flv encoded file came in at 3.1 megabytes while the H.264 encoded file came in at 1.7 megabytes.

You have given me some cool and truly useful advice!

---

### Post by FakeOutdoorsman on 2013-01-03
Andrew gave some good advice too. Although I disagree with his view that he isn't an expert.

You should change one thing: don't use *-q:v* with libx264. Use *-crf* instead. See the crf section in the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide). It has examples and explanations.

You may encounter two problems with your command, depending on your input. If -1 from your scale filter ends up being an odd value libx264 may complain, "height not divisible by 2". This can be an alternative method:
```
scale="320:trunc(ow/a/2)*2"
```
IIRC, if height ends up being an odd value it will automatically round down to an even value. You can do the same for width too:
```
scale="trunc(oh*a*2)/2:240"
```

The other potential issue is that flv container probably only accepts certain MP3 audio sample rates. ffmpeg, by default, will usually inherit the input sample rate for the output. If you end up with 48000 for example, then ffmpeg will complain:
```
FLV does not support sample rate 48000, choose from (44100, 22050, 11025)
```

---

### Post by GrouchyGaijin on 2013-01-03
> **FakeOutdoorsman said:**
> 


The other potential issue is that flv container probably only accepts certain MP3 audio sample rates. ffmpeg, by default, will usually inherit the input sample rate for the output. If you end up with 48000 for example, then ffmpeg will complain:
```
FLV does not support sample rate 48000, choose from (44100, 22050, 11025)
```

FakeOutdoorsman, you called that one!

So, I thought to myself this is great.  I saved the command as a script and put it in the aliases file and hoped I was ready to go.

Sure enough, the first time out going from mpg to flv using:
```
ffmpeg -i foo.mpg \
       -c:v libx264 -crf 5 -vf scale=320:-1 \
       -c:a libmp3lame -q:a 3 \
       MPEG-to-libx264.flv
```
I got the sample rate error.

My question is where in the command do I specify the sample rate?



Thank you for the help!  I really do appreciate it!!

---

### Post by FakeOutdoorsman on 2013-01-03
You can add "-ar" as an output option which is anywhere after "-i foo.mpg", such as:
```
ffmpeg -i foo.mpg \
       -c:v libx264 -crf 23 -vf scale=320:-1 \
       -c:a libmp3lame -q:a 3 -ar 44100 \
       MPEG-to-libx264.flv
```
I also changed your -crf value in this example. -q:v and -crf are not interchangeable, so although -q:v 5 might be a good balance for your input and the flv1 encoder, a value of -crf 5 will result in an unnecessarily large output. The link in my last post shows how to use crf. Default value is 23, which is what libx264 will use if you omit -crf. Use the highest value that still provides an acceptable quality.

---

### Post by evilsoup on 2013-01-03
What *does* -q:v do in relation to libx264?

---

### Post by FakeOutdoorsman on 2013-01-03
Probably nothing. I think it is ignored, and possibly limited to the mpeg quant scale (flv/h263/h263+/mpeg1video/mpeg2video/mpeg4/mjpeg/msmpeg*), but I might be wrong about that.

---

### Post by JimS on 2013-03-08
Why not simply get a Dropbox or other cloud account, upload your mov files, send grandparents an email with attachments.  They can download and watch mov files with vlc.

---

### Post by GrouchyGaijin on 2013-03-09
> **JimS said:**
> Why not simply get a Dropbox or other cloud account, upload your mov files, send grandparents an email with attachments.  They can download and watch mov files with vlc.

Is this a real suggestion or are you making a joke?

---

### Post by JimS on 2013-03-09
Joodan ja nai!
I've done it my way after reducing my camera images with ffmpeg.
And then I sent them to relatives via email attachments from Dropbox.
It works and it is free.  Quality isn't the best.
I'm not running a webserver, so I can't help you there.  Good luck.
MVH
JimS
...

---

### Post by 3L33T on 2013-06-17
> **GrouchyGaijin said:**
> Is this a real suggestion or are you making a joke?

It was a simple but great suggestion.  Why not?

---

