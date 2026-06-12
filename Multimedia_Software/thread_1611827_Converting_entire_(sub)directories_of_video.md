---
title: "Converting entire (sub)directories of video"
date: 2010-11-02
forum: Multimedia Software
---

### Post by JackandJohn on 2010-11-02
I have a collection of music videos of various ages, and want to consolidate the codecs into mp4 files with the following criteria:

1) Retain the same directory structure and same name, hopefully with something like "/music/Videos (Encoded)/" and "/music/Videos (Failed Encoding)/" (Note: Using UTF-8 filenames)

2) Prefer to do this all in one batch; terminal commands/ bash script = awesome :)

3) Keep the highest quality video without having to encode everything the same (some widescreen, some hd, some with super low resolution)

4) Retain the audio stream untouched (plus, some help on what command to do to convert it to a good format)

and, hopefully, to encode with settings that allow for universal apple playback (Handbrake as a great preset for this)


Thank you in advance for any help: as I learn and do this, I'll definitely be creating a how-to so that future users will benefit :)

---

### Post by JackandJohn on 2010-11-02
I've not gone through these tutorials, just to make sure my encoding powers are up to date:

[http://ubuntuforums.org/showpost.php?p=9114176&postcount=967](http://ubuntuforums.org/showpost.php?p=9114176&postcount=967) (Compile ffmpeg from scratch)
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283) (Install restricted codecs from medibuntu)

I'm currently trying to figure out what I should use for the batch processing and passing parameters to FFMPEG - some have suggested just using the 'find' program for similar tasks, but my knowledge of that command is severely lacking..


Basically, I'm thinking at this point, that it will be something like:


```
find '/Music Videos/' -type f -exec ffmpeg -acodec copy -vcodec libx264 -vpre hq '/Music Videos (Encoded)/$path'
```

But, I know there is a lot missing there, also; if I could use handbrakecli instead, it has a 'universal' preset that is what I'm looking for in the final encode.


Any help is appreciated :)

---

### Post by crazyness003 on 2010-11-07
Hey. Sorry im not of any use, but i too would like to know how something like this would be achieved.

I have little to no knowlege about the ins and outs of video conversion/compression

I went thru the [**Comprehensive Multimedia & Video Howto**]("http://ubuntuforums.org/showthread.php?t=766683&highlight=convert+videos") but all i found was WinFF...and I really dont know how to change the settings to suite my needs.

Anyway, just thought id share what i found.

---

