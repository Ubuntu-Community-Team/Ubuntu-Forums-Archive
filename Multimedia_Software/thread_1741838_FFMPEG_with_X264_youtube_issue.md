---
title: "FFMPEG with X264 youtube issue"
date: 2011-04-28
forum: Multimedia Software
---

### Post by MJLaukala on 2011-04-28
So, I finally broke down and learned how to use ffmpeg with x264. It was quite easy. The problem I am having is when I download my videos to youtube, they are pretty much all gray. From my reading and testing, i have determined that it is x264 and furthermore, it has to do with weightp defaulting to 2. I want it to equal 0 but I cannot find any way to do thins through ffmpeg. Is there a way I can set the default to 0? Or does anyone know how to set it to zero from ffmpeg? here is the terminal line I am trying to get to work.

[HTML]ffmpeg -i video.mkv -b 2600 -vcodec libx264 -acodec libmp3lame -preset slow -crf 18 -r 24 -f mp4 videoOUT.mp4[/HTML]

The only thing missing is the property to change weightp and I have no idea what it is and could not find it anywhere. Anyhelp would be appreciated.

---

### Post by FakeOutdoorsman on 2011-04-28
> **MJLaukala said:**
> So, I finally broke down and learned how to use ffmpeg with x264. It was quite easy. The problem I am having is when I download my videos to youtube, they are pretty much all gray.

I can't duplicate your issue using your command. Can you show the complete FFmpeg terminal output from your command? Can you provide a link to one of the gray videos?

> **MJLaukala said:**
> From my reading and testing, i have determined that it is x264 and furthermore, it has to do with weightp defaulting to 2. I want it to equal 0 but I cannot find any way to do thins through ffmpeg. Is there a way I can set the default to 0? Or does anyone know how to set it to zero from ffmpeg?

You currently can't override the options each preset sets, but the developers are working on fixing this. However, the previous preset system allowed this. So your options are:
[list=1]
[*]Wait for FFmpeg to update the libx264 preset system to allow for option overriding
[*]Use an older FFmpeg version
[*]Use x264 directly and re-mux the video and audio
[/list]

Option 1. I'm not sure how long this will take.

Option 2. Explained here: [using an older FFmpeg](http://ubuntuforums.org/showpost.php?p=10699860&postcount=1647). You probably want commit abf8342aa94bdf06bb324f6723a6743dd628d5c6. Then use the old syntax:
```
ffmpeg -i input -vcodec libx264 -vpre slow -crf 18 -wpredp 0 -threads 0 output
```

Option 3. Recompile x264 (no need to uninstall first) to get *lavf* support. This allows x264 to handle any input that FFmpeg can (I should add this to the guide). Then something like:
```
x264 --preset slow --crf 18 --weightp 0 -o x264output.mkv input
ffmpeg -i x264output.mkv -i audioinput -vcodec copy -acodec copy output.mkv
```

> **MJLaukala said:**
> here is the terminal line I am trying to get to work.
```
ffmpeg -i video.mkv -b 2600 -vcodec libx264 -acodec libmp3lame -preset slow -crf 18 -r 24 -f mp4 videoOUT.mp4
```
As for your command (ignoring the current issue of not being able to override options): *-b* and *-crf* are two different methods of rate control and therefore can't be used together. In your case *-b* is probably being ignored. Changing the frame rate isn't usually recommended but there are exceptions of course. *-f mp4* isn't needed since your output ends in .mp4. Adding *-threads 0* will make the video encode faster.

---

### Post by MJLaukala on 2011-04-28
Thanks for the reply. After a few more hours of searching, I figured ffmpeg needed a fix. So i'm waiting for the fix but in the meantime, i'll be using the libxvid codec. It works quit well, as for the rest of the advice, thanks. I will be sure to fix up my terminal cammand. Thanks so much for the reply!

---

### Post by FakeOutdoorsman on 2011-04-29
FFmpeg has been updated to allow **-wpredp** to be used to overwrite the preset value. (This is actually a direct result of your question, so you could visit *#ffmpeg* IRC channel and thank *bcoudurier*). See **Updating FFmpeg and x264** at:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

```
$ git log

commit 97dc86b793efb9c6ac604cdfff4027fe27efa12c
Author: Baptiste Coudurier <baptiste.coudurier@gmail.com>
Date:   Fri Apr 29 14:13:19 2011 -0700

    In libx264 wrapper, change wpredp to a codec specific option.
```

---

