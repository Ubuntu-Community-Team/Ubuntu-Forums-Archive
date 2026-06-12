---
title: "[SOLVED] Creating Powerpoint 2010 compatible videos with FFmpeg..."
date: 2013-03-22
forum: Multimedia Software
---

### Post by andrew.46 on 2013-03-22
I have to use MS PowerPoint 2010 at work for presentations and I am keen to embed some video clips. Using FFmpeg I seem to have found a *base level *encode that works well enough:

```

ffmpeg -i input.flv \
          -c:v wmv2 -q:v 4  \
         -c:a wmav2 -b:a 128k \
          output.wmv

```

Does anybody have experience with FFmpeg conversions for this purpose, and could suggest a better set of codecs?

---

### Post by FakeOutdoorsman on 2013-03-22
> **andrew.46 said:**
> Does anybody have experience with FFmpeg conversions for this purpose, and could suggest a better set of codecs?

I had to do this once. I think I may have ended up using either MPEG-1 video (mpeg1video) in either .mpg or .avi, or WMV2 like your command. I can't remember...so I guess this isn't very helpful. Too bad [Compatible audio and video file formats in PowerPoint 2010](http://office.microsoft.com/en-us/powerpoint-help/compatible-audio-and-video-file-formats-in-powerpoint-2010-HA010336709.aspx#_Toc261351670) isn't more specific.

Sounds like a good time to experiment. Maybe one will play back more consistently than the other.

---

### Post by andrew.46 on 2013-03-22
Thanks FakeOutdoorsman. I have found out that there is a bug with Powerpoint 2010 and wmv container with a not particularly helpful 'Playback error' message and frozen video. Solutions are either revert to an older Powerpoint format or use avi or mpg container. Sigh.....

---

### Post by andrew.46 on 2013-04-12
So the powerpoint is almost ready and I will be presenting this Friday: '*Artificial Airways in the Intensive Care Unit*' believe it or not. The following works well with Microsoft Powerpoint 2010 with embedded videos in non-compatibility mode:

```

ffmpeg -i Melker_Emergency_Crico_Set.flv \
       -q:v 4 -c:v wmv2 -c:a wmav2 -b:a 128k \
       melker.avi

```

Not exactly elegant but it works well for the presentation. Next to setup Zeranoe's FFmpeg, get a decent console application for Windows XP and do all of this at work next time :).

---

