---
title: "Question about encoding to make it work with iTunes/iPhone"
date: 2013-05-01
forum: Multimedia Software
---

### Post by dralban7 on 2013-05-01
Hi,

I´m seeking help in regards playing screencasted files on iPhone after encoding. I´m not an expert in encoding matters and would be grateful if one of you could help me.

Based on "HOWTO: Proper Screencasting on Linux" ([http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)) I installed FFmpeg on my Ubuntu 12.04.

I started to record my screen based on the information in the aforementioned link:
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv 

This works fine.

Afterwards I encoded the output.mkv file:
ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -preset slow -crf 22 -threads 0 our-final-product.mp4 

But unfortunately this file can NOT be imported into iTunes. When doing so iTunes is saying:
"our-final-product.mp4" was not copied to the iPhone because it cannnot be played on this iPhone.

Would be great to get a hint how to do the encoding to make it work with iTunes/iPhone.

Great thx.

Greetings.
Karl

---

### Post by evilsoup on 2013-05-01
You could try adding '-profile main' or '-profile baseline' in there. I believe that the recent iPhones support the High profile (which is used by default with x264 in ffmpeg, IIRC), but older ones may not. This will give you lesser-quality video, though it should still be good enough.

See [the appropriate Wikipedia page](http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC#Profiles) for some more information on h.264 profiles. Basically, the less-complicated profiles (like Baseline) are easier to decode, but have access to less-advanced functions, and so will not have as good quality compared to the more advanced profiles (like High)

---

### Post by dralban7 on 2013-05-01
Hi Evilsoup,

thank you for your fast reply.

Command:
ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -preset slow -crf 22 -threads 0 -profile:v main our-final-product.mp4 
I tried "main" and "baseline". In both cases I get following error...


Stream mapping:
Stream #0:0 -> #0:0 (h264 -> libx264)
Stream #0:1 -> #0:1 (pcm_s16le -> libfaac)
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height

Is this error related to the screencasted file output.mkv?

Thank you.

Greetings
Karl

---

### Post by SeijiSensei on 2013-05-01
I'd use [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases") for this since it has built-in profiles for the iPhone.

---

### Post by dralban7 on 2013-05-01
Hi SeijiSensei,

good idea, but my intention was to make it work with ffmpeg and create a batch script.

Idea is to start a batch script which starts recording a screen and afterwards encodes it for watching it on iPhone.

Any further ideas here in the thread?

Thank you.

Greetings
Karl

---

### Post by JohnAStebbins on 2013-05-01
HandBrake has a CLI that can be used in scripts
```

HandBrakeCLI -i input.mkv -Z "iPhone 4" -o output.mp4

```

---

### Post by dralban7 on 2013-05-01
Thank you. 

I will try this also.

But is there anyone facing the same issue with ffmpeg?
I would like to stick to ffmpeg.

Thank you.

---

### Post by andrew.46 on 2013-05-01
> **dralban7 said:**
> 

```
Stream mapping:
Stream #0:0 -> #0:0 (h264 -> libx264)
Stream #0:1 -> #0:1 (pcm_s16le -> libfaac)
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height
```



You will need to give the full terminal output to find that error...

---

### Post by dralban7 on 2013-05-01
Hi,

I solved it by adding "-pix_fmt yuv420p" to the ffmpeg command.

ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 **[COLOR=#008000]-pix_fmt yuv420p[/COLOR]** -preset slow -crf 22 -threads 0 -profile:v main our-final-product.mp4

The error message andrew.46 was asking for was as following:
ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -preset slow -crf 22 -threads 0 -profile:v main our-final-product.mp4

######################
ffmpeg version git-2013-04-28-124244e Copyright (c) 2000-2013 the FFmpeg develop                                            ers
  built on Apr 28 2013 13:50:32 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-a                                            ac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --e                                            nable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-l                                            ibvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 27.101 / 52. 27.101
  libavcodec     55.  6.100 / 55.  6.100
  libavformat    55.  3.100 / 55.  3.100
  libavdevice    55.  0.100 / 55.  0.100
  libavfilter     3. 61.101 /  3. 61.101
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  3.100 / 52.  3.100
[COLOR=#ff8c00]Guessed Channel Layout for  Input Stream #0.1 : stereo
[/COLOR]Input #0, matroska,webm, from 'output.mkv':
  Metadata:
    ENCODER         : Lavf55.3.100
  Duration: 00:00:53.10, start: 0.000000, bitrate: 9337 kb/s
    Stream #0:0: Video: h264 (High 4:4:4 Predictive), yuv444p, 444x294, SAR 1:1                                             DAR 74:49, 30 fps, 30 tbr, 1k tbn, 60 tbc (default)
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s (default)
No pixel format specified, yuv444p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
x264 [error]: main profile doesn't support 4:4:4
[COLOR=#00ffff][libx264 @ 0xa688fe0][/COLOR] [COLOR=#ff0000]Error setting profile main.
[/COLOR][COLOR=#00ffff][libx264 @ 0xa688fe0][/COLOR] Possible profiles: baseline main high high10 high422 high4                                            44
Output #0, mp4, to 'our-final-product.mp4':
  Metadata:
    ENCODER         : Lavf55.3.100
    Stream #0:0: Video: h264, yuv444p, 444x294 [SAR 1:1 DAR 74:49], q=-1--1, 90k                                             tbn, 30 tbc (default)
    Stream #0:1: Audio: aac, 48000 Hz, stereo, s16, 128 kb/s (default)
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libx264)
  Stream #0:1 -> #0:1 (pcm_s16le -> libfaac)
[COLOR=#ff0000]Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height
[/COLOR][COLOR=#000000]#################

As mentioned by adding "[COLOR=#008000]**-pix_fmt yuv420p**[/COLOR]" it is solved now. But please let me know if you have any further information.

Greetings
Karl[/COLOR]

---

### Post by andrew.46 on 2013-05-01
> **dralban7 said:**
> 
```
Use -pix_fmt yuv420p for compatibility with outdated media players.
```
But please let me know if you have any further information.



No, Looks like you have solved the problem, but you can see how the terminal output usually shows the way...

---

