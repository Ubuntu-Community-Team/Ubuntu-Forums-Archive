---
title: "Embed subtitles in video file?"
date: 2010-04-30
forum: Multimedia Software
---

### Post by aquascrotum on 2010-04-30
I have a film that has been split into 2 files, both of which has an associated srt subtitle file.

I want to embed the subtitle file permanently in the films, so I can subsequently combine the 2 video files (and so have continous playback).

I've tried playing about with Avidemux but no joy so far.  Can anyone point me in the right direction?

---

### Post by ron999 on 2010-04-30
........

---

### Post by beliyyal on 2010-08-05
> **ron999 said:**
> ........
Wow, that was really helpful....


I am trying to create a dvd in DeVeDe that has subtitles. It is, like you said, split into two separate video files, cd1 and cd2. DeVeDe cannot use .idx and .sub subtitle formats, so I got the proper .srt subtitles. I put both video files on there under one title, add the subtitle files and all. I go to preview cd1, it works great, text shows up and everything, spot on. But when I preview cd2, I get an error "conversion failed. could be a bug of SPUMUX". I have no clue what the problem is, I am at a loss. If anyone could give some information on this, or just embedding subtitles into the video .AVI file, this would be very helpful. 

[img]http://a.imageshack.us/img835/18/screenshoterror.png[/img]

---

### Post by beliyyal on 2010-08-06
This worked for me dude.

> **aala said:**
> For embedding subs into .avi video...

```
transcode -i videofile.avi -x mplayer="-sub subfile.xxx" -o outputfile.avi -y xvid
```

for more explicit help!...
```
transcode -h |more
```

From [this thread](http://ubuntuforums.org/showthread.php?t=1188954).

---

