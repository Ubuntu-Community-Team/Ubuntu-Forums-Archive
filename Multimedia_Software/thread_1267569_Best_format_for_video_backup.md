---
title: "Best format for video backup"
date: 2009-09-15
forum: Multimedia Software
---

### Post by woedend on 2009-09-15
Hey guys,

I'm going to be backing up much of my movie collection(well, more specifically, TV Seasons on DVD).  I plan to buy a couple 1 TB external drives to do this with.  I have everything built and lined out now for this media server of sorts, I just need to pick a format to rip to.  I want something that will be the smallest possible size without sacrificing noticeable a/v quality.  It doesn't need to be uncompressed/lossless format obviously, but I want it to be watchable on the big screen.  I've read a bit on google but everyone seems to either a)have no idea what they are talking about(think Yahoo answers) or b) disagree horrendously in answers.  Figured i'd try here.  Any suggestions and/or testimonials?

Thanks

---

### Post by andrew.46 on 2009-09-15
Hi woedend,

I have a deep suspicion that you will find just as much disagreement here as you have encountered elsewhere :). My own thoughts would be that if you are saving a single video stream + a single audio stream you would be best to transcode to h264 for the video and aac for the sound in an mp4 container. There is plenty of room to move with h264 encoding using x264 in terms of quality/size adjustments and I have always been happy with aac for sound... Interesting to see what others think :).

Andrew

---

### Post by lovinglinux on 2009-09-15
> **andrew.46 said:**
> Hi woedend,

I have a deep suspicion that you will find just as much disagreement here as you have encountered elsewhere :). My own thoughts would be that if you are saving a single video stream + a single audio stream you would be best to transcode to h264 for the video and aac for the sound in an mp4 container. There is plenty of room to move with h264 encoding using x264 in terms of quality/size adjustments and I have always been happy with aac for sound... Interesting to see what others think :).

Andrew

I agree, except for the container. I would suggest h.264 and aac on a mkv container, since it allows more flexibility, like storing multiple streams, subtitles or even chapters.

---

### Post by FakeOutdoorsman on 2009-09-15
You'll get excellent quality for file size with H.264 video using FFmpeg and x264.  Development of both FFmpeg and libx264 is active and new features are often being introduced.

Older machines may struggle to play "HD" H.264 video, but standard definition video such as DVD should be no problem.  Encoding times are good with newer machines and aren't bad on older hardware if you use a proper command.

I recommend compiling FFmpeg and x264 yourself to take advantage of recent developments that are missing from the Ubuntu repository FFmpeg.  It's fairly simple to compile if you follow this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by vinutux on 2009-09-16
+1 for H.264 ....best result for me using x264 codec with MP4 container.

Handbrake is finest tool to dealing with x264.........

---

### Post by andrew.46 on 2009-09-16
Hi vintux,

> **vinutux said:**
> Handbrake is finest tool to dealing with x264.........

We will have to agree to disagree with at least part of that :). For me the discovery of the FFmpeg presets, courtesy of FakeOudoorsman's guides, was revelation that even a total video encoding n00b like myself could achieve great results.

Andrew

---

### Post by vinutux on 2009-09-16
> **andrew.46 said:**
> Hi vintux,



We will have to agree to disagree with at least part of that :). For me the discovery of the FFmpeg presets, courtesy of FakeOudoorsman's guides, was revelation that even a total video encoding n00b like myself could achieve great results.

Andrew

I agreed that ffmpeg is far better tool to deals videos.....but i think for a newbie itz better to recomended easiest GUI apps like handbrake........:)

---

