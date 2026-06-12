---
title: "Hard Subs for .mp4"
date: 2014-03-02
forum: Multimedia Software
---

### Post by Lango on 2014-03-02
I've read several threads on here but can't quite seem to get the settings or right answer.

I have a .mp4 H.264 video with an accompanying  subtitle .srt file for the non-English parts.  I'm trying to get it to play on my Xbox 360 which cannot read subtitles from a separate file.

I've managed to do something similar with a .avi file using Avidemux (good quality and quick).  However I've tried a number of suggestions from this forum trying to use; ffmpeg, FFmpeg, mencoder, Handbrake, MP4Box, all have either not worked or took hours and ended up with a much bigger file or a much worse quality video, (oh and Handbrake doesn't seem to be able to burn in the subtitles, is that right??).
 
Can anyone recommend any ideas/settings/config/application/guide/tips for this task?  The original video is perfect on my Xbox (except for the lack of subtitles), so ideally I'd like to keep everything the same but hard burn in the subs... and of course do it as quick as possible.
 
Thanks.

---

### Post by FakeOutdoorsman on 2014-03-02
You can do this with ffmpeg.

[size=6]1. Get ffmpeg[/size]
The version in the repo is an old, buggy, fake version from a fork that also lacks the [subtitles video filter](http://ffmpeg.org/ffmpeg.html#subtitles). You can simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

[size=5]1a. Laziness[/size]
If you want to download and extract the static build but are too lazy to use the link above just do this:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
tar xzvf ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz

```

[size=6]2. Encode[/size]
Notice the **./** before **ffmpeg**:
```
./ffmpeg -i video.mp4 -vf subtitles=subtitles.srt -codec:v libx264 -crf 23 -preset medium -codec:a copy output.mp4
```
[list]
[*]This will [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) the audio.
[*]I'm not sure what H.264 profile and level limitations the Xbox 360 has, so you may have to add the "-profile:v" option, such as "-profile:v baseline".
[*]You can add "-ss 300" (as an input option) and "-t 60" (as an output option) if you want to skip the first 300 seconds and make a 60 second test output so you don't have to encode the whole thing.
[*]crf will control your quality. A lower value is a higher quality. 18 is roughly "visually lossless" and 23 is default. preset will control your encoding speed vs compression efficiency ratio. Generally you use the slowest preset you have patience for, but medium (the default) is good if you are unsure or don't care. See the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide) for more info.
[*]Also see [How to burn subtitles into the video](https://trac.ffmpeg.org/wiki/How%20to%20burn%20subtitles%20into%20the%20video).
[/list]

---

### Post by Lango on 2014-03-03
@FakeOutdoorsman - Thanks for the advice used the ffmpeg code above and  it works on Xbox just fine, file size only increased only by ~7.5%, and I  couldn't notice any quality degradation, so thanks for the easy to  understand explanation of the options.

I do have a pretty old pc  and just left the conversion running overnight, it seemed to take around  6 hours for a 1.8GB video, does that sound about right, is the CPU the  main factor that affects duration (noticed CPU was maxed but not RAM)?

Was hoping that it might be quicker (without sacrificing file size) as a similar sized .avi file using Avidemux only took around 45 mins (I think).

In any case, thanks for your help.

---

### Post by FakeOutdoorsman on 2014-03-03
> **Lango said:**
> I do have a pretty old pc  and just left the conversion running overnight, it seemed to take around  6 hours for a 1.8GB video, does that sound about right,
Try a faster preset like "fast" or "veryfast" as shown in the encoding guide.

> **Lango said:**
> is the CPU the  main factor that affects duration (noticed CPU was maxed but not RAM)?
Yes.

---

