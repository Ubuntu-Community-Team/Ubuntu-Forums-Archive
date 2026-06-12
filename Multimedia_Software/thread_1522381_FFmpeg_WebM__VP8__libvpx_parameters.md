---
title: "FFmpeg WebM / VP8 / libvpx parameters?"
date: 2010-07-02
forum: Multimedia Software
---

### Post by seanlano on 2010-07-02
I've started playing around with using VP8 video encoding via FFmpeg and libvpx. I wanted to see if it was as good as libx264, but I'm struggling to find how to use it properly. 
For libx264 there are a bunch of options and presets available, but I don't know what they are for libvpx. 
Are there any "-vpre" things for libvpx? 
What should I do to get a good output? 
The [WebM page gives a bunch of sample commands]("http://www.webmproject.org/tools/encoder-parameters/#10_sample_command_lines"), but they don't work with FFmpeg (I think because the commands are for ivfenc, whatever that is). 

Any ideas? 
How can I produce a good quality WebM / VP8 coded video with FFmpeg? (Or just with Ubuntu in general, doesn't have to FFmpeg).

---

### Post by demizer on 2010-07-02
I have been using the following command to encode videos, and it produces excellent quality:

```


ffmpeg -y -i <INPUT_FILE> -threads 8 -f webm -aspect 16:9 -vcodec libvpx -deinterlace -g 120 -level 216 -profile 0 -qmax 42 -qmin 10 -rc_buf_aggressivity 0.95 -vb 2M -acodec libvorbis -aq 90 -ac 2 <OUTPUT_FILE.webm>


```

Notes:
[LIST]
[*]I got most of the parameters from the preset files available in the google patches. However, some of them did not work with the native FFMPEG vp8 encoder as of the latest SVN build.
[*]The deinterlace parameter can be removed if the video is not interlaced.
[*]The aspect parameter forces 16:9, change it to 4:3 if you have standard def video.
[*]The -aq parameter can safely be lowered to 60 or 70, but I am picky about having high quality audio.
[*]The -threads parameter should be lowered to the max available threads that your cpu can handle. I use a core i7 so the max treads are 8.
[/LIST]

---

### Post by FakeOutdoorsman on 2010-07-02
> **demizer said:**
> However, some of them did not work with the native FFMPEG vp8 encoder as of the latest SVN build.

There is no native FFmpeg VP8 encoder yet, but there is a native VP8 decoder though.

> **demizer said:**
> [*]The -aq parameter can safely be lowered to 60 or 70, but I am picky about having high quality audio.

I believe the *-aq* range for libvorbis via FFmpeg for stereo is -1 to 10.  Anything above 10 probably ends up about the same as what 10 would provide.  See [Recommended Vorbis Encoder Settings](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis) for a nice chart of each quality level.

---

### Post by seanlano on 2010-07-02
Thanks for this. 

What do the "-g" and "-level" settings do? Where can I find the presets on the WebM site? Some of the options mentioned look interesting. What about 2-pass encoding? Can I just specify "-pass 1" and put the video to "/dev/null" and then "-pass 2" after that? (Like with x264). 
Come to think of it, is there some sort of command I can pass to FFmpeg to have it tell me all of the acceptable arguments for the libvpx encoder? It must list them somewhere, because it obviously knows when you use one it doesn't recognise...



Also, about the Vorbis audio, I knew that it went from -1 to 10, but in some programs, such as SuondKonverter, the levels seem to be multiplied by 10, to go from 0 to 100, and I think it's then possible to specify, say, 85 which I think means 8.5 on the proper scale. Maybe FFmpeg does this?


Also, can I safely use an .mkv container? So far my computer doesn't know what to do with a .webm file (not hard to fix, but still) but it can play the VP8 codec. Is Matroska going to widely support VP8 in the future? Or should I just use the .webm container to avoid confusion?

---

### Post by andrew.46 on 2010-07-03
Hi sean,

> **seanlano said:**
> Also, can I safely use an .mkv container? So far my computer doesn't know what to do with a .webm file (not hard to fix, but still) but it can play the VP8 codec. Is Matroska going to widely support VP8 in the future? Or should I just use the .webm container to avoid confusion?

Bear in mind that a WebM container is actually a pared down Matroska container anyway, some interesting reading [here]("https://www.bunkus.org/blog/2010/05/google-open-sources-vp8-choses-matroska/") which demonstrates that mkvtoolnix accepts WebM as an *input* and also *output*. Courtesy of the work I do packaging mkvtoolnix for another distro I have the latest copy at hand and I can confirm it works beautifully. The attached screenshots shows WebM input being converted to full mkv output which MPlayer plays with no problem... The 3rd screenshot shows the option to create an output file with WebM constraints.

All the best,

Andrew

---

### Post by geo.cohn on 2010-07-07
I tried to make a .ffpreset file based on demizer's post.  It looks like this:

```
g 120
level 216
profile 0
qmax 42
qmin 10
rc_buf_aggressivity 0.95
vb 2M
```ffmpeg found the file, but did not like a single one of the arguments.  However, when I put them directly into the command line they worked OK.

I hope they get this sorted soon.  I really like using the presets for libx264.

geo.

---

### Post by FakeOutdoorsman on 2010-07-07
> **geo.cohn said:**
> I tried to make a .ffpreset file based on demizer's post.  It looks like this:

```
g 120
level 216
profile 0
qmax 42
qmin 10
rc_buf_aggressivity 0.95
vb 2M
```ffmpeg found the file, but did not like a single one of the arguments.  However, when I put them directly into the command line they worked OK.

I hope they get this sorted soon.  I really like using the presets for libx264.

geo.

You need to add = between the option and value for presets:
```
g=120
level=216
profile=0
qmax=42
qmin=10
rc_buf_aggressivity=0.95
vb=2M
```
Not all options are available for use in the presets.

---

### Post by HotshotGG on 2010-07-14
> I believe the *-aq*  range for libvorbis via FFmpeg for stereo is -1 to 10.  Anything above  10 probably ends up about the same as what 10 would provide.  See [Recommended Vorbis Encoder Settings]("http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis") for a nice  chart of each quality level. I am the co-author of that wiki page. You providing me with valuable information. Let me scrim through the manual and see what I can cook up. I will document how to do it in ffmpeg I think your on the right track though with audio in standalone encoder -q 5 more then likely maps to -aq 50 in ffmpeg!. I just did a quick test with a MPEG-2 TS file from a DVD and ivfenc encodes the file quite nicely. The thing that I don't like about the video encoder is that it does specify how to encode audio via Vorbis with the standalone encoder!? What's that all about :o!?. Let me do some digging and I will see what I can find. We can at least show folks how to do it with ffmpeg in the meantime. I think maybe --codec switch in ivfenc has something to do specify the audio, but Google did a VERY POOR job documenting it besides the --good and --best quality switches. The i420 is regular MPEG2 stream btw. It's stands for interlaced 420.

---

### Post by mike4ubuntu on 2010-08-30
The ffmpeg command didn't seem to work for me.  Obviously, I need to do more setup and prep for the libvpx.  What do you do to set this up?  I just got the following error

```
Requested output format 'webm' is not a suitable output format
```

---

### Post by andrew.46 on 2010-08-30
Hi mike,

> **mike4ubuntu said:**
> The ffmpeg command didn't seem to work for me.  Obviously, I need to do more setup and prep for the libvpx.  What do you do to set this up? 

The best way is to follow this guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and add in the optional libvpx step. You may find that x264 encoding still delivers better quality faster, that is certainly my experience...

Andrew

---

### Post by FakeOutdoorsman on 2010-08-30
Also, Ubuntu Maverick Meerkat's FFmpeg will be new enough to include the *libvpx* encoder.

> **andrew.46 said:**
> You may find that x264 encoding still delivers better quality faster, that is certainly my experience...

Yes, I agree.

---

### Post by cthlhu1987 on 2010-10-03
I did everything according to the HOWTO-Thread, but the mplayer still wont play my webm files.

---

### Post by andrew.46 on 2011-04-22
At the risk of necroposting some might be interested to know that there are some 'official' libvpx presets available in a patch against the git FFmpeg:

[http://code.google.com/p/webm/downloads/list](http://code.google.com/p/webm/downloads/list)

I have been using these presets and they produce great results :).

---

### Post by seanlano on 2011-04-23
"necroposting"

haven't heard that before. love it!



thanks, i'll take a look.

---

### Post by andrew.46 on 2011-04-23
> **seanlano said:**
> thanks, i'll take a look.

Actually I spent a quiet afternoon playing with the libvpx presets and I have extracted the sparring scene from the Matrix and encoded to webm. Does not look too bad and this scene is a good test:

```

wget http://www.andrews-corner.org/tmp/matrix_sparring.webm

```

I have cropped and scaled a little + used 2 passes. Still not the same quality as x264 but there is a huge improvement from the last time I looked at webm :).

---

### Post by brontosaurusrex on 2011-10-03
andrew.46:

Two things that are interesting with your sample:
1. it does not play with correct aspect ration in chrome :D (works in ff)
2. You did not provide your encoding parameters? thanks.

---

### Post by andrew.46 on 2011-10-04
I will admit that I have never viewed this file in a web browser so I am not sure what is going on there... The parameters I have dug out though. First I extracted the specific section of the Matrix:

```

tccat -i /dev/dvd -T 1,15,1 > fight.vob

```

Next I calculated the best cropping figures:

```

ffmpeg -y -i fight.vob -vf cropdetect=24:16:0 -f rawvideo -an /dev/null

```

and tested with MPlayer:

```

mplayer -vf rectangle=720:416:0:80 fight.vob

```

and then ran a 2 pass FFmpeg command:

```

ffmpeg -i fight.vob -vf crop=720:416:0:80 \
       -vpre libvpx-720p -pass 1 \
       -acodec libvorbis -ab 192k  -ac 2 \
       -f rawvideo -y /dev/null && \
ffmpeg -i fight.vob -vf crop=720:416:0:80 \
       -vpre libvpx-720p -pass 2 \
       -acodec libvorbis -ab 192k -ac 2 \
       -y matrix_sparring.webm

```

Probably did not need to encode the sound on the first pass but I was off having a cup of lemongrass tea anyway :). I have taken the liberty of replacing the old *matrix_sparring.webm* file with a new one (same filename) encoded today. This one uses the latest FFmpeg and libvpx 0.9.7 and I am trying to convince myself it looks a little a better? Looks pretty respectable anyway on my setup...  You will note that if you run mediainfo across the file:

```

andrew@skamandros~/Desktop$ mediainfo matrix_sparring.webm 
General
Unique ID                                : 135481506964462030876865855661090110250 (0x65ECCA039856FCDC463B998270F97B2A)
Complete name                            : matrix_sparring.webm
Format                                   : WebM
Format version                           : Version 2
File size                                : 52.9 MiB
Duration                                 : 4mn 22s
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 693 Kbps
Writing application                      : Lavf53.13.0
Writing library                          : Lavf53.13.0

Video
ID                                       : 1
Format                                   : VP8
Codec ID                                 : V_VP8
Duration                                 : 4mn 22s
Bit rate                                 : 1 425 Kbps
Width                                    : 720 pixels
Height                                   : 416 pixels
Display aspect ratio                     : 2.462
Frame rate                               : 25.000 fps
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.190
Stream size                              : 44.6 MiB (84%)
Language                                 : English

Audio
ID                                       : 2
Format                                   : Vorbis
Format settings, Floor                   : 1
Codec ID                                 : A_VORBIS
Duration                                 : 4mn 22s
Bit rate mode                            : Variable
Bit rate                                 : 192 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 6.00 MiB (11%)
**[COLOR="Red"]Writing library                          : aoTuV 20110424 (UTC 2011-04-24)[/COLOR]**
Language                                 : English
Writing application                      : Lavc53.19.0

```

that I am using the AoTuV modified libvorbis but I guess that is a whole 'nother story :).

---

### Post by dudefire on 2012-02-10
> **andrew.46 said:**
> At the risk of necroposting some might be interested to know that there are some 'official' libvpx presets available in a patch against the git FFmpeg:

[http://code.google.com/p/webm/downloads/list](http://code.google.com/p/webm/downloads/list)

I have been using these presets and they produce great results :).

Can I please know the command to download and apply these presets ?
Clearly I am a noob. Can you please help me out on this ?

---

### Post by FakeOutdoorsman on 2012-02-10
Recent versions of FFmpeg now include several libvpx presets including:
```
libvpx-1080p50_60.ffpreset
libvpx-1080p.ffpreset
libvpx-360p.ffpreset
libvpx-720p50_60.ffpreset
libvpx-720p.ffpreset
```

---

