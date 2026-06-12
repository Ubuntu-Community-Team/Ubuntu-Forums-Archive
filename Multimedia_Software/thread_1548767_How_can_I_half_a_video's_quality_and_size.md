---
title: "How can I half a video's quality and size?"
date: 2010-08-08
forum: Multimedia Software
---

### Post by menachem on 2010-08-08
I have a 500MB video that is 720x400. I want to half the size of the video while retaining the same relative quality.

My main goal is to half the filesize of the video, but to do that and keep the same relative quality I will have to also make the resolution smaller.

I can't seem to find a way to do this.

I would preferer to use ffmpeg, but any solution would be good at this point. I would really like to be able to do this from the command line, but if there is a gui program that will also give me the command line it uses, that's great too.

Does any one know of a way to half the file size of a video while maintaining the same relative quality?

[COLOR="Blue"]EDITED TO ADD: SOLUTION (thanks to FakeOutdoorsman):
[As suggested below]("http://ubuntuforums.org/showpost.php?p=9696776&postcount=8"), I converted the video to h264 using the following ffmpeg command:
```
ffmpeg -i input.foo -acodec copy -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mkv
```

The input file was an 551MB avi with the following information:
```
Duration: 00:56:48.67, start: 0.000000, bitrate: 1354 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
```

The output file was a 188MB mkv with the following information:
```
Duration: 00:56:48.69, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 624x352, PAR 1:1 DAR 39:22, 23.98 tbr, 1k tbn, 2k tbc
```

The quality was still very good.[/COLOR]

---

### Post by Rumpty on 2010-08-08
Basically you have to re-encode it using a codec which will compress it more, like x264. What type of file is it now? Do you want to keep the same resolution?

---

### Post by menachem on 2010-08-08
> **Rumpty said:**
> What type of file is it now? Do you want to keep the same resolution?

It is an avi.

I don't mind if it is a smaller resolution, as long as the relative quality is the same.

For example, the file is now 720x400. I don't mind if it is 540x300, but the quality still needs to be good.

In a way, it's like the videos on youtube. There are a bunch of different quality levels available, but they are all the same relative quality. 

(I don't know if I'm explaining myself well when I say "relative quality". You can see [a list of all the video resolutions available on Youtube here]("http://en.wikipedia.org/wiki/YouTube#Quality_and_codecs"). Even though they are obviously different resolutions and qualities, they step down in an orderly fashion.)

 My problem is that when I try to lower the quality, I just get a really bad pixelated video. I'm obviously doing something wrong.

---

### Post by linux18 on 2010-08-08
```

#!/bin/bash
# Encoding Script
ffmpeg -y -i $1 -pass 1 -threads 0 -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -an -r ntsc /dev/null

ffmpeg -y -i $1 -pass 2 -threads 0 -s 640x480 -vcodec h264 -b 384k -bt  192k -f mp4 -flags +loop -cmp +chroma -partitions  +parti4x4+partp4x4+partp8x8+partb8x8 -me_method umh -subq 7 -trellis 2  -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40  -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)'  -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -acodec aac -ab 96k -ac 1  -r ntsc $2

```save it to a script, chmod it, and run it like so
```
  ./YOURSCRIPT INFILE OUTFILE  
```
you'll need the latest ffmpeg and x264 codecs, instrustions here:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by menachem on 2010-08-09
> **linux18 said:**
> ```

#!/bin/bash
# Encoding Script
ffmpeg -y -i $1 -pass 1 -threads 0 -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -an -r ntsc /dev/null

ffmpeg -y -i $1 -pass 2 -threads 0 -s 640x480 -vcodec h264 -b 384k -bt  192k -f mp4 -flags +loop -cmp +chroma -partitions  +parti4x4+partp4x4+partp8x8+partb8x8 -me_method umh -subq 7 -trellis 2  -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40  -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)'  -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -acodec aac -ab 96k -ac 1  -r ntsc $2

```save it to a script, chmod it, and run it like so
```
  ./YOURSCRIPT INFILE OUTFILE  
```
you'll need the latest ffmpeg and x264 codecs, instrustions here:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Holy crap, that's a lot of flags.

Question: Will setting '-s 640x480' change the aspect ratio to 640x480, or will it keep my existing aspect ratio?

---

### Post by linux18 on 2010-08-09
it will sort of squish your aspect ratio into 640x480,but honestly i'm not sure, I copy/pasted this from a post from 2008 by Fakeoutdoorsman

---

### Post by dtfinch on 2010-08-09
How about:
```
ffmpeg -i infile -vcodec libx264 -pass 1 -vpre fastfirstpass -g 300 -b 500k -an -y out.mp4
ffmpeg -i infile -vcodec libx264 -pass 2 -vpre hq -g 300 -b 500k -acodec libfaac -ab 96k -y out.mp4
```

-vpre specifies quality preset
-g specifies keyframe interval. 300 is about 10 seconds. Smaller values would make precise seeking easier, but at a cost of size/quality.
-ab is target audio bitrate
-b is the target video bitrate. You'll want to adjust this so total bitrate is half the original.
change "infile" to match your input file.

---

### Post by FakeOutdoorsman on 2010-08-09
> **linux18 said:**
> it will sort of squish your aspect ratio into 640x480,but honestly i'm not sure, I copy/pasted this from a post from 2008 by Fakeoutdoorsman

I'm glad people notice my examples, but unfortunately that's an incredibly outdated FFmpeg encoding command.  It won't even work.

The first step is to enable some additional encoders in FFmpeg that aren't installed by default.  There are several methods explained here:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

Here's a more recent example:
```
ffmpeg -i input.foo -acodec copy -vcodec libx264 -vpre fast -crf 24 -threads 0 output.mkv
```

The important options to monkey around with are *-vpre* (the preset) and *-crf* (the quality level).  A lower number is a higher quality and a sane range is something like 18-28.  Read more about that at the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

This command will copy the audio from the input video (named *input.foo* in my example) and re-encode to H.264 video using the *fast* preset and then will dump everything into a MKV container file which just happens to be my personal favorite.  This example is suitable for FFmpeg that you compiled yourself.  If you use FFmpeg from the repository instead then change *-vpre fast* to *-vpre hq* (the repo FFmpeg is too old to have the more recent presets, but FFmpeg from Ubuntu Maverick is probably new enough though).

The example may not be suitable for the original poster because I don't know much about the video to be converted, and I'm not really sure what the encoded video is targeted for (watching on computer, portable device, playing with a Flash player on a web site, etc).

---

### Post by menachem on 2010-08-09
> **FakeOutdoorsman said:**
> Here's a more recent example:
```
ffmpeg -i input.foo -acodec copy -vcodec libx264 -vpre fast -crf 24 -threads 0 output.mkv
```

The important options to monkey around with are *-vpre* (the preset) and *-crf* (the quality level).  A lower number is a higher quality and a sane range is something like 18-28.  Read more about that at the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

This command will copy the audio from the input video (named *input.foo* in my example) and re-encode to H.264 video using the *fast* preset and then will dump everything into a MKV container file which just happens to be my personal favorite.  This example is suitable for FFmpeg that you compiled yourself.  If you use FFmpeg from the repository instead then change *-vpre fast* to *-vpre hq* (the repo FFmpeg is too old to have the more recent presets, but FFmpeg from Ubuntu Maverick is probably new enough though).

The example may not be suitable for the original poster because I don't know much about the video to be converted, and I'm not really sure what the encoded video is targeted for (watching on computer, portable device, playing with a Flash player on a web site, etc).

I will be watching it on a computer. However, I have to convert it on one computer and then rsync it to another computer which has a small amount of storage available. Because of the file has to be synced over the internet, as well as the fact that I have limited storage on the destination computer, my goal is to have a smaller file that still has decent quality.

---

