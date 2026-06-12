---
title: "Command Line to bulk convert WMV to MP4"
date: 2016-06-24
forum: Multimedia Software
---

### Post by peridian on 2016-06-24
In a Ubuntu command line setup, what's the best way to batch convert a bunch of WMV files (I believe they are all WMV3) into MP4 files without changing their size/aspect ratio/bitrate (i.e. just re-encode, do not lose any quality)?

Regards,
Rob.

---

### Post by FakeOutdoorsman on 2016-06-24
You can't re-encode to a lossy format without losing any quality. However, you can give it enough bits that you probably can't tell the difference.

Install ffmpeg, navigate to the directory containing the WMV files, then run:
```

mkdir output
for f in *.wmv; do ffmpeg -i "$f" -c:v libx264 -crf 18 -c:a aac "output/${f%.wmv}.mp4"; done
```

[list]
[*]If you really want to not lose quality you can enable lossless mode in libx264 by using "-crf 0", but the output file will be huge and probably not widely playable by devices, etc.
[*]If your ffmpeg is old and outdated add "-strict experimental" to enable the AAC encoder, but I recommend updating instead by either [downloading a binary](http://johnvansickle.com/ffmpeg/) or [compiling](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).
[*]Also see [FFmpeg Wiki: H.264](https://trac.ffmpeg.org/wiki/Encode/H.264).
[/list]

---

### Post by TheFu on 2016-06-24
FakeOutdoors... nailed it with that little script.  18 is an extreme quality - I thought 19 was extreme.  Lots of people use 21, but I see added artifacts at that level. Try a few different levels, see what looks "the same" to you.  Different types of videos need lower (better) settings due to high-action. Low action videos can have higher "quality" numbers.

May be able to change containers without re-encoding. That's the only loss-less way.  **mkvmerge -o output.mkv input.wmv** that's the base command. I've never used it with WMV files, but it works with pretty much all the other popular video formats, so it should work.

BTW, mp4 is just a container. It isn't a video or audio encoding standard.  For the most commercially accepted encodings, the video needs to be h.264 and the audio needs to be aac.

Plus, you might want to use mkv containers rather than mp4.  mkv allows almost any sort of attachment in the container to go with the a/v streams. That can be handy for multiple audio streams or for captions in 10 different languages. It just depends on what you need.  mp4 isn't bad, just folks have been moving to mkv the last 6-8 yrs.

---

### Post by Rob Sayer on 2016-06-25
Actually I'd only consider 18 a high quality CRF factor if the source is high quality Blu Ray or similar.  For DVD quality I'd go 16 or lower.

As mentioned, you can't convert without losing quality unless it's to a lossless codec and no one wants that.  But quality is a bit subjective and you'll have to decide for yourself if it's good enough.

The problem with batch encoding is that there are no magic encoder settings that work for all videos, even if all the source files are the same resolution etc, which they probably aren't.  You need to evaluate each video on a case by case basis.  You can get quality or speed but I don't know how to do b both.

You may not want to resize but I find that downsampling the resolution is the best way to get good quality at a reasonable bit rate.  And one of the best tips I've heard is to resample to a size whose dimensions are mod 16, ie. evenly divisible by 16.  Eg. for 16:9 sources at a width of 720 the height would be 720/(16/9) ~= 404 but I'd use 720 x 400 instead because 400 is mod 16.  Since video encoding and decoding is basically matrix processing this makes the video much easier to encode and decode.

---

### Post by TheFu on 2016-06-25
Another option from ffmpeg is to use HandbrakeCLI.  Setup a few "presets" for the different types of files to be encoded, then using the --preset option, call **HandbrakeCLI --preset WheverYouCallIt -i input.wmv -o output.mkv** Output can be mp4 if you like too.  This is handy when all the source files have subtitles, captions and multiple audio tracks that you just want to copy into the resulting output file.

+1 on the mod16 stuff.  The presets in handbrake make that easy.

---

### Post by FakeOutdoorsman on 2016-06-25
I ignore attempting to adhere to mod16. Hardly makes any difference.

---

### Post by peridian on 2016-06-27
Thanks guys for the input, I almost forgot I posted this question :)

Thanks for the script FakeOutdoorsman, that worked well on a small sample.  I'll play around with quality settings if I feel I need to.

Regards,
Rob.

---

