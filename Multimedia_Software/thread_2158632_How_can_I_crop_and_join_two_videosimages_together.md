---
title: "How can I crop and join two videos/images together?"
date: 2013-06-29
forum: Multimedia Software
---

### Post by TooFreppaT on 2013-06-29
I want to make a video by combining the top part of one video and the bottom part of another video. One half is a static image but I can just record it and turn it into a video.

---

### Post by vanadium on 2013-06-30
You will probably need video editing software for that.

---

### Post by evilsoup on 2013-06-30
```

ffmpeg -i topinput.mp4 -loop 1 -i bottominput.png \
-filter_complex '[1:v]crop=iw:ih/2:0:ih/2[btm];[0:v][btm]overlay=shortest=1:y=H/2[outv]' \
-map '[outv]' -map 0:a -c:v libx264 -preset veryfast -crf 20 -c:a copy output.mp4

```

The above will require a recent version of ffmpeg -- the version in the Ubuntu repositories probably won't work (and isn't ffmpeg anyway, but actually the avconv fork) because the *shortest* option to the *overlay* filter is fairly new. You can get a static build from the [ffmpeg website]("http://ffmpeg.org/download.html#LinuxBuilds"), or [follow this guide to compile your own](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

*-i topinput.mp4 -loop 1 -i bottominput.png* means that you want to use topinput.mp4 as the first input, and bottominput.png as the second input (ffmpeg starts ounting from 0, so that's inputs 0 and 1); the *-loop 1* tells ffmpeg to use the input image on an unending loop.

The first filter [crops]("http://ffmpeg.org/ffmpeg-all.html#crop") the video stream of input 1 (that is, bottominput.png), so that only the bottom half of it remains. The [overlay filter]("http://ffmpeg.org/ffmpeg-all.html#overlay") then puts what is left over the video from input 0 -- *y=H/2* means that the top of the overlay will be halfway down the video. *shortest=1* means that it will stop when the shortest of the inputs comes to an end (which is good, because the image input is set to loop forever).

*-map '[outv]' -map 0:a* tells ffmpeg to use the output of the filter (which I explicitly labelled as [outv]) and the audio from input 0 in the output file. *-c:a copy* tells ffmpeg to copy the audio exactly, without any re-encoding. You can read about the video encoding settings I've put [on the x264 encoding guide]("http://trac.ffmpeg.org/wiki/x264EncodingGuide") on the [FFmpeg wiki]("http://trac.ffmpeg.org/wiki").

---

### Post by TooFreppaT on 2013-06-30
> **evilsoup said:**
> ```

ffmpeg -i topinput.mp4 -loop 1 -i bottominput.png \
-filter_complex '[1:v]crop=iw:ih/2:0:ih/2[btm];[0:v][btm]overlay=shortest=1:y=H/2[outv]' \
-map '[outv]' -map 0:a -c:v libx264 -preset veryfast -crf 20 -c:a copy output.mp4

```

The above will require a recent version of ffmpeg -- the version in the Ubuntu repositories probably won't work (and isn't ffmpeg anyway, but actually the avconv fork) because the *shortest* option to the *overlay* filter is fairly new. You can get a static build from the [ffmpeg website]("http://ffmpeg.org/download.html#LinuxBuilds"), or [url=http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide]follow this guide to compile your own[url].

*-i topinput.mp4 -loop 1 -i bottominput.png* means that you want to use topinput.mp4 as the first input, and bottominput.png as the second input (ffmpeg starts ounting from 0, so that's inputs 0 and 1); the *-loop 1* tells ffmpeg to use the input image on an unending loop.

The first filter [crops]("http://ffmpeg.org/ffmpeg-all.html#crop") the video stream of input 1 (that is, bottominput.png), so that only the bottom half of it remains. The [overlay filter]("http://ffmpeg.org/ffmpeg-all.html#overlay") then puts what is left over the video from input 0 -- *y=H/2* means that the top of the overlay will be halfway down the video. *shortest=1* means that it will stop when the shortest of the inputs comes to an end (which is good, because the image input is set to loop forever).

*-map '[outv]' -map 0:a* tells ffmpeg to use the output of the filter (which I explicitly labelled as [outv]) and the audio from input 0 in the output file. *-c:a copy* tells ffmpeg to copy the audio exactly, without any re-encoding. You can read about the video encoding settings I've put [on the x264 encoding guide]("http://trac.ffmpeg.org/wiki/x264EncodingGuide") on the [FFmpeg wiki]("http://trac.ffmpeg.org/wiki").

Thanks! :D Not everybody takes the time to explain what all of that overcomplicated stuff means or even where to go to learn more about it. :D
...............I guess I could of googled about ffmpeg but google likes to throw a megagram of sites at us and I think that's why many people just give up on learning about computer stuff because of they just don't know where to start in the very messy pile of random links. I found out about WinFF.

---

### Post by evilsoup on 2013-07-01
WinFF is good for simple tasks, but I don't think it's suitable for this kind of thing (because it's not designed to do these sort of editing tasks, being focused on the encoding side). 

The best ffmpeg reference online is the ffmpeg wiki I linked in my first post. Other than that, this forum is actually pretty good (we've got a handful of people who really know what they're doing with ffmpeg), and superuser.com has a strong group of ffmpeg experts.

There's also an ffmpeg-users mailing-list, but I wouldn't recommend that unless you already know what you're doing a little bit (i.e. it's for intermediate and up users rather than complete newbies). I would put the official ffmpeg documentation in the same category -- worth reading once you've got the basics down, but a bit overwhelming for a new user.

But yeah, most of the information on ffmpeg out on the internet, outside of those sites, is a mixture of wrong and outdated.

---

