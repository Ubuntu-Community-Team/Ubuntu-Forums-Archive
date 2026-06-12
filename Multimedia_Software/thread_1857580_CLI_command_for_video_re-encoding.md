---
title: "CLI command for video re-encoding?"
date: 2011-10-10
forum: Multimedia Software
---

### Post by Roger Allott on 2011-10-10
Until now, I've been most impressed with PiTiVi for creating videos, but I think it's got one or two drawbacks for me in some situations.

Certainly, if I need to do any splitting of videos or adding effects and transitions, I'd still use PiTiVi in its 0.15 guise, but I'm thinking more about what's most pressing for me at the moment, which is simply re-encoding some video files to a smaller size with a reduced bitrate.

My first issue is that I'm rather resource poor. My PC is a laptop with just 2Gb of RAM and a tendency to just give up the ghost when it gets a bit too hot (i.e. when I'm asking it to do a bit too much). Surely, I figure, the GUI interface of PiTiVi must be using some RAM resource that I wouldn't have if I were to just throw a CLI command at Terminal.

The second issue is that I've got a few videos that I want to downsize, and PiTiVi can only deal with them one at a time as far as I can tell. Again, CLI strikes me as being the answer, as I can just add a '&&' between two commands and when it's done the first one it will automatically go off to do the next one.

The videos that I have are 720p (i.e. 1280x720 px) at 4000 bps and audio at 256 bps. I want to produce lighter videos at a resolution of 752x424 px at 1024 bps with audio at 80 bps.

My settings in PiTiVi adjust the defaults only in those areas, so I'm going to guess that whatever CLI command I need will also just use the built-in defaults of GStreamer.

I want my output files to be an mp4 container with h264 video codec and mp3 audio codec.

Let's say that my starting video is named bigvideo.mp4 and my desired output is to be named smallvideo.mp4

What would be the CLI code that I should use to do what I hope I've explained above?

---

### Post by thatguruguy on 2011-10-10
ffmpeg can do everything you want.  

You can also install winff from the software center.  It is a frontend for ffmpeg, and has several different presets, including dvd-ready mpg and xvid-format avi.  I use it almost every day.

---

### Post by Lisiano on 2011-10-10
^--- +1
Also while not possible to do lists, you can take a look at Avidemux, it's a GUI app but without the bells and whistles of a full-blown video-editor. But yes, ffmpeg is your best bet if you want to do it in big amounts.

---

### Post by nothingspecial on 2011-10-10
Moved to Multimedia & Video

You are likely to get more specific help here :)

---

### Post by Roger Allott on 2011-10-10
> **thatguruguy said:**
> ffmpeg can do everything you want.  

Sure, but there are no instructions on how to use it. All I've ever got from this forum about it is one or more people saying
```
man ffmpeg
```
which is about as useful as a chocolate teapot to someone who isn't fluent in Geek.


> **thatguruguy said:**
> You can also install winff from the software center.  It is a frontend for ffmpeg, and has several different presets, including dvd-ready mpg and xvid-format avi.  I use it almost every day.
I've used winff a number of times, or tried to, and it always throws up error messages that prevent it being any use whatsoever.

---

### Post by Roger Allott on 2011-10-10
> **Lisiano said:**
> ^--- +1
Also while not possible to do lists, you can take a look at Avidemux, it's a GUI app but without the bells and whistles of a full-blown video-editor.

Avidemux would be fine if I were happy with the sound synchronisation being wayward, which I'm not. It's a known bug, which as far as I can tell hasn't yet been fixed. Lots of promises that it'll be fine when 2.6 comes out, but that's been the case for well over a year now.

PiTiVi is, I've found, by far the most reliable and bullet-proof video editor/re-encoder that's available for linux (or Windows, for that matter).

---

### Post by Lisiano on 2011-10-10
AFAIK the man pages are in English so they aren't greek :-\"
```
FFMPEG(1)                                                                                                                                                                  FFMPEG(1)

NAME
       ffmpeg - FFmpeg video converter

SYNOPSIS
       ffmpeg [[infile options][-i infile]]... {[outfile options] outfile}...
...
EXAMPLES
...
   Video and Audio file format conversion
       * FFmpeg can use any supported file format and protocol as input:

       Examples:

       * You can use YUV files as input:

               ffmpeg -i /tmp/test%d.Y /tmp/out.mpg
...
``` It's written with green, on semi-transparent with blur applied background, letters (YMMV regarding how it looks).
To use ffmpeg, you type ffmpeg, any option to the input file (For example it detects it at 24fps but really its a 30fps, etc), then the input file, the options to the output file (The size, etc) and the output file itself.
In your case you want to use this.
```
ffmpeg -i $INPUTFILE -b 1024k -s 752x424 -vcodec libx264 -vpre default $OUTPUTFILE
```
Personally I wouldn't recommend touching audio since you won't gain any real space benefit and will save your ears from bad noise, but if you really want to torture your ears, prepend "-acodec mp3 -ab 80k" (No quotes) before the $OUTPUTFILE. Ofc replace $INPUTFILE with a input file, say Movie.mkv, and replace $OUTPUTFILE with how the file should come out, also here you specify the container, say [Re-Enc]Movie.mp4

For more H264 presets, go here [http://juliensimon.blogspot.com/2009/01/howto-ffmpeg-x264-presets.html](http://juliensimon.blogspot.com/2009/01/howto-ffmpeg-x264-presets.html) or read the man page and construct it yourself.

---

### Post by Roger Allott on 2011-10-10
I've just tried using winff again and this is the sort of unintelligible gobbledegook that gets outputted:

```
FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep 16 2011 17:11:24 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/media/SYSTEM/Users/Roger/Downloads/bigvideo.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 1
    compatible_brands: mp42avc1
  Duration: 00:20:17.04, start: 0.000000, bitrate: 4236 kb/s
    Stream #0.0(eng): Audio: aac, 48000 Hz, stereo, s16, 303 kb/s
    Stream #0.1(eng): Video: h264, yuv420p, 1280x720, 3927 kb/s, 25 fps, 25 tbr, 2500 tbn, 5k tbc
[libx264 @ 0x9e7f230]broken ffmpeg default settings detected
[libx264 @ 0x9e7f230]use an encoding preset (vpre)
Output #0, mp4, to '/media/SYSTEM/Users/Roger/Downloads/Output/smallvideo.mp4':
    Stream #0.0(eng): Video: libx264, yuv420p, 752x424, q=2-31, 1024 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: libfaac, 48000 Hz, stereo, s16, 80 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
Press Enter to Continue
```

All I can see from that is that something's wrong, but it gives me no idea whatsoever as to what is wrong or what I should do to remedy the situation.

---

### Post by Lisiano on 2011-10-10
```
[libx264 @ 0x9e7f230]broken ffmpeg default settings detected
[libx264 @ 0x9e7f230]**use an encoding preset (vpre)**
```
Tell WinFF to use a encoding preset for H264 somewhere in it's menu (I don't use it) or add -vpre $PRESET as a additional argument, where $PRESET is an actual preset.

Also
```
Seems stream 1 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1)
```
This looks weird to me, but it might be just me since the input data looks okay.

---

### Post by Roger Allott on 2011-10-10
> **Lisiano said:**
> ```
[libx264 @ 0x9e7f230]broken ffmpeg default settings detected
[libx264 @ 0x9e7f230]**use an encoding preset (vpre)**
```
Tell WinFF to use a encoding preset for H264 somewhere in it's menu (I don't use it) or add -vpre $PRESET as a additional argument, where $PRESET is an actual preset.
Sorry, but that's another example of language that I'm sure to you seems perfectly reasonable, but to me is just gibberish. What the heck is an "encoding preset"??? And what values are sensible?


> **Lisiano said:**
> Also
```
Seems stream 1 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1)
```
This looks weird to me, but it might be just me since the input data looks okay.
That caught my eye too. It seems that ffmpeg thinks that mp4 videos have to run at 5000 fps, which is just daft!

---

### Post by Lisiano on 2011-10-10
I assumed since you use PiTiVi that you knew about different codecs, encoders, options, presets. In short, a encoder preset is a list of defaults that are passed to the encoder, just like presets in transcoders for mobile devices.
In short, without a preset, the only thing it would give you is the Kazemir Malevich painting ["Black Square"]("http://upload.wikimedia.org/wikipedia/commons/5/57/Malevich.black-square.jpg").
Note: I'm not a video editor or someone that knows deep level stuff about codecs. I google if I don't know something.

---

### Post by Roger Allott on 2011-10-10
> **Lisiano said:**
> I assumed since you use PiTiVi that you knew about different codecs, encoders, options, presets.

I know that different codecs exist, but I've no idea what the pros and cons of each one are, and the simple reason for that is that no one seems in the slightest bit interested in explaining stuff in clear intelligible English.

I have no interest whatsoever in learning how different codecs work; I just need to know what's good about one that's not so good about another.

As an example of what I mean, here's what the ffmpeg-doc says about encoding presets:
```
3.10 Preset files

A preset file contains a sequence of option=value pairs, one for each line, specifying a sequence of options which would be awkward to specify on the command line. Lines starting with the hash ('#') character are ignored and are used to provide comments. Check the `ffpresets' directory in the FFmpeg source tree for examples.

Preset files are specified with the vpre, apre, spre, and fpre options. The fpre option takes the filename of the preset instead of a preset name as input and can be used for any kind of codec. For the vpre, apre, and spre options, the options specified in a preset file are applied to the currently selected codec of the same type as the preset option.

The argument passed to the vpre, apre, and spre preset options identifies the preset file to use according to the following rules:

First ffmpeg searches for a file named arg.ffpreset in the directories `$FFMPEG_DATADIR' (if set), and `$HOME/.ffmpeg', and in the datadir defined at configuration time (usually `PREFIX/share/ffmpeg') in that order. For example, if the argument is libx264-max, it will search for the file `libx264-max.ffpreset'.

If no such file is found, then ffmpeg will search for a file named codec_name-arg.ffpreset in the above-mentioned directories, where codec_name is the name of the codec to which the preset file options will be applied. For example, if you select the video codec with -vcodec libx264 and use -vpre max, then it will search for the file `libx264-max.ffpreset'. 
```

Why on earth would it think that a typical user would be interested in knowing where it searches for its list of presets? Why on earth does it not bother telling anyone what the different preset options are and what the pros and cons of each one are?

What is the point of all of this secrecy????

---

### Post by thatguruguy on 2011-10-10
> **Roger Allott said:**
> I know that different codecs exist, but I've no idea what the pros and cons of each one are, and the simple reason for that is that no one seems in the slightest bit interested in explaining stuff in clear intelligible English.

I have no interest whatsoever in learning how different codecs work; I just need to know what's good about one that's not so good about another.

As an example of what I mean, here's what the ffmpeg-doc says about encoding presets:
```
3.10 Preset files

A preset file contains a sequence of option=value pairs, one for each line, specifying a sequence of options which would be awkward to specify on the command line. Lines starting with the hash ('#') character are ignored and are used to provide comments. Check the `ffpresets' directory in the FFmpeg source tree for examples.

Preset files are specified with the vpre, apre, spre, and fpre options. The fpre option takes the filename of the preset instead of a preset name as input and can be used for any kind of codec. For the vpre, apre, and spre options, the options specified in a preset file are applied to the currently selected codec of the same type as the preset option.

The argument passed to the vpre, apre, and spre preset options identifies the preset file to use according to the following rules:

First ffmpeg searches for a file named arg.ffpreset in the directories `$FFMPEG_DATADIR' (if set), and `$HOME/.ffmpeg', and in the datadir defined at configuration time (usually `PREFIX/share/ffmpeg') in that order. For example, if the argument is libx264-max, it will search for the file `libx264-max.ffpreset'.

If no such file is found, then ffmpeg will search for a file named codec_name-arg.ffpreset in the above-mentioned directories, where codec_name is the name of the codec to which the preset file options will be applied. For example, if you select the video codec with -vcodec libx264 and use -vpre max, then it will search for the file `libx264-max.ffpreset'. 
```Why on earth would it think that a typical user would be interested in knowing where it searches for its list of presets? Why on earth does it not bother telling anyone what the different preset options are and what the pros and cons of each one are?

What is the point of all of this secrecy????

Are you always insulting to people who are trying to help you, or is this a particularly bad day?

---

### Post by FakeOutdoorsman on 2011-10-10
1. Enable *libx264* encoding in FFmpeg. You probably already did this, but it is easy to do if you haven't already. I recommend Option C (unless you don't mind compiling then see Option A):

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

2. Encoding example using ffmpeg from the Lucid repository:
```
ffmpeg -i input.mp4 -vcodec libx264 -vpre medium -crf 24 -threads 0 -s 753x424 \
-acodec copy output.mp4
```

3. Find out the right settings. You should only need to modify the preset (*-vpre*) and your quality (*-crf*). The general method is to:
[list]
[*]use the highest crf that still gives an acceptable quality
[*]use the slowest preset that you have patience for
[*]use those settings for the rest of your "set" of inputs
[/list]

Your available presets listed from fastest to slowest: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow. A slower preset gives you better compression at the cost of slower encoding.

A sane range for crf is 18-30. A lower number is higher quality output and therefore a bigger file size. 18 can be considered to be visually lossless. 29-35 is probably most web video quality. 51 is the highest value and is the worst quality. If the output looks good then use a higher number and keep increasing it until it becomes unacceptable.

See posts #5 and #7 in this thread for a detailed explanation about some of the options: [Could someone lend me a few instructions for Mencoder and CLi encoding with ffmpeg](http://ubuntuforums.org/showthread.php?t=1847410).

Note that the information in this post refers to ffmpeg from the Lucid repository only.

---

### Post by Roger Allott on 2011-10-10
> **FakeOutdoorsman said:**
> 1. Enable *libx264* encoding in FFmpeg. You probably already did this, but it is easy to do if you haven't already. I recommend Option C (unless you don't mind compiling then see Option A):

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

2. Encoding example using ffmpeg from the Lucid repository:
```
ffmpeg -i input.mp4 -vcodec libx264 -vpre medium -crf 24 -threads 0 -s 753x424 \
-acodec copy output.mp4
```

3. Find out the right settings. You should only need to modify the preset (*-vpre*) and your quality (*-crf*). The general method is to:
[list]
[*]use the highest crf that still gives an acceptable quality
[*]use the slowest preset that you have patience for
[*]use those settings for the rest of your "set" of inputs
[/list]

Your available presets listed from fastest to slowest: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow. A slower preset gives you better compression at the cost of slower encoding.

A sane range for crf is 18-30. A lower number is higher quality output and therefore a bigger file size. 18 can be considered to be visually lossless. 29-35 is probably most web video quality. 51 is the highest value and is the worst quality. If the output looks good then use a higher number and keep increasing it until it becomes unacceptable.

See posts #5 and #7 in this thread for a detailed explanation about some of the options: [Could someone lend me a few instructions for Mencoder and CLi encoding with ffmpeg](http://ubuntuforums.org/showthread.php?t=1847410).

Note that the information in this post refers to ffmpeg from the Lucid repository only.

THANK YOU!! You've answered in clear, plain English!

(On point 1, yes I had already installed libavcodec-extra-52 from the Medibuntu repository.)

My only question (for the moment) is the -crf option. That looks to me to be pretty much the same thing as a quantiser setting, but with a different range of numbers. Is there any significant difference between what they do?

Also, I've already determined that the 'right' quality for this size of output file comes from a constant bitrate of 1024 kbps. Wouldn't it therefore be more sensible, and entail less aborted or re-done encodings, if I use the -b 1024k setting instead of the -crf 24 setting?

---

### Post by thatguruguy on 2011-10-10
> **Roger Allott said:**
> THANK YOU!! You've answered in clear, plain English!

(On point 1, yes I had already installed libavcodec-extra-52 from the Medibuntu repository.)

My only question (for the moment) is the -crf option. That looks to me to be pretty much the same thing as a quantiser setting, but with a different range of numbers. Is there any significant difference between what they do?

Also, I've already determined that the 'right' quality for this size of output file comes from a constant bitrate of 1024 kbps. Wouldn't it therefore be more sensible, and entail less aborted or re-done encodings, if I use the -b 1024k setting instead of the -crf 24 setting?

Maybe you could do a test run of each, and see which result you like better.

---

### Post by Roger Allott on 2011-10-10
Right, I'm having a run on a file I re-encoded earlier using PiTiVi to see what the difference in output is if I use ffmpeg.

The command I'm using is:
```
ffmpeg -i videobig.mp4 -vcodec libx264 -vpre slow -b 1024k -threads 0 -s 752x424 -acodec libmp3lame -ar 48000 -ab 80k -ac 2 videosmall.mp4
```
That seems pretty much identical to my settings in PiTiVi where I used its defaults primarily, although I notice that the default vpre in PiTiVi is medium. Oh well, it should mean that my file from the ffmpeg exercise is a tad smaller that my base file that came from PiTiVi, although my initial test says that the opposite is true. Where PiTiVi outputted a video that's 7.50 Mb per minute, the ffmpeg command seems to be outputting one that's about 8.52 Mb per minute.

The start of the output is still troubling me:
```
FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep 16 2011 17:11:24 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
```
So, it's telling me that I've got a "library configuration mismatch". Unfortunately, it doesn't tell me what is mismatching what, let alone what I can do about it.

Anyone got any ideas?

Later on, but still before it starts doing its crunching, I'm still getting:
```
Seems stream 1 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1)
```
To be clear to everyone, yes I have googled this and I'm drawing a blank as to what the heck it means. Again, does anyone here have any suggestions?

---

### Post by FakeOutdoorsman on 2011-10-11
> **Roger Allott said:**
> My only question (for the moment) is the -crf option. That looks to me to be pretty much the same thing as a quantiser setting, but with a different range of numbers. Is there any significant difference between what they do?
I'm sorry, but I'm not sure what you're asking here.

> **Roger Allott said:**
> Also, I've already determined that the 'right' quality for this size of output file comes from a constant bitrate of 1024 kbps. Wouldn't it therefore be more sensible, and entail less aborted or re-done encodings, if I use the -b 1024k setting instead of the -crf 24 setting?
Probably not. To generalize you use *-b* if you're targeting a specific output file size. Use *-crf* if you are trying to get a specific quality for your output. Do you care more about having your output be a certain file size, or do you want to be able to control exactly how your video will look? Secondly, if you are absolutely set on using *-b*, then you should perform two-passes. [Example](http://ubuntuforums.org/showthread.php?t=786095) (you'll have to scroll down on that page).

> **Roger Allott said:**
> The command I'm using is:
```
ffmpeg -i videobig.mp4 -vcodec libx264 -vpre slow -b 1024k -threads 0 -s 752x424 -acodec libmp3lame -ar 48000 -ab 80k -ac 2 videosmall.mp4
```
I believe MP3 isn't officially supported in MP4, but FFmpeg should have no issue with it.

> **Roger Allott said:**
> ```
FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers
```
This indicates that you're using Ubuntu Maverick. I'm not sure why I assumed Lucid earlier.

> **Roger Allott said:**
> ```
WARNING: library configuration mismatch
```
So, it's telling me that I've got a "library configuration mismatch". Unfortunately, it doesn't tell me what is mismatching what, let alone what I can do about it.
Ignore that message. It may look bad, but it's not anything to worry about. I would guess means that the ffmpeg binary and/or the libraries were compiled with different options. There's even a bug report about it: [Bug #730159 ffmpeg library configuration mismatch](https://bugs.launchpad.net/ubuntu/+source/ffmpeg-extra/+bug/730159).

> **Roger Allott said:**
> 
```
Seems stream 1 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1)
```
To be clear to everyone, yes I have googled this and I'm drawing a blank as to what the heck it means. Again, does anyone here have any suggestions?
Although it's dated this might clarify things: [[FFmpeg-user] codec frame rate differs from container frame rate](https://lists.libav.org/pipermail/ffmpeg-user/2008-December/018097.html). Basically, if the output looks fine then ignore the message.

---

### Post by Roger Allott on 2011-10-11
> **FakeOutdoorsman said:**
> I'm sorry, but I'm not sure what you're asking here.
In the past, I've used Avidemux with the 'MPEG-4 ASP (Xvid)' codec, where the quality is controlled by either bitrate or quantizer.

The quantizer is a number between 1 and 31, and just like crf, higher numbers equates to poorer quality and smaller file sizes.

So, when I come to ffmpeg, is the crf option simply the same thing as the quantizer setting in other applications (including PiTiVi), but with an extended range that, for some reason, goes from 1 to 52?

> **FakeOutdoorsman said:**
> Probably not. To generalize you use *-b* if you're targeting a specific output file size. Use *-crf* if you are trying to get a specific quality for your output. Do you care more about having your output be a certain file size, or do you want to be able to control exactly how your video will look? Secondly, if you are absolutely set on using *-b*, then you should perform two-passes. [Example](http://ubuntuforums.org/showthread.php?t=786095) (you'll have to scroll down on that page).
Ah, thanks. File size is important to me in this exercise, but it's obviously not the only consideration.

> **FakeOutdoorsman said:**
> I believe MP3 isn't officially supported in MP4, but FFmpeg should have no issue with it.
How weird! PiTiVi offers mp3 (libmp3lame) as one of the options available when creating an mp4 video, and I'm scratching my head to figure out why they do that when it's officially non-kosher.

-----

The result of my exercise last night was that ffmpeg converted the big video file down to 153.7 Mb and took just under 3 hours to do it.

PiTiVi had done the same thing earlier and the resulting file size was 152.2 Mb. I think the task took about the same amount of time.

I cannot notice any difference in the output quality.

The net result of this is that I've now got a reliable CLI command to do the process, which I think should help me with my system crashing due to overload. And being CLI, I should be able to concatenate commands to do multiple files and leave the 'puter running overnight while I do more sensible stuff, such as sleeping.

Many thanks for your help, which has been invaluable in getting me to this point. And similar to Lisiano, who was very helpful in answering questions at the start of the thread.

---

