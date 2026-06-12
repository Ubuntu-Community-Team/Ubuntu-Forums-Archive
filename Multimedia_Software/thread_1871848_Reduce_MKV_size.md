---
title: "Reduce MKV size"
date: 2011-10-29
forum: Multimedia Software
---

### Post by Dumbestcrayon on 2011-10-29
I figured it out. See post #2

---

### Post by Dumbestcrayon on 2011-10-29
Here is what I have come up with...

```
ffmpeg -i /media/Stuff/Movie.mkv -vcodec copy -vb 4741120 -sameq -acodec copy -ab 655360 -f vob -copyts -y /media/Stuff/Movies/Movie.mkv
```

Adjust the bitrates (vb = Video Bitrate and ab = audio bitrate) as needed.

---

### Post by FakeOutdoorsman on 2011-10-30
It's somewhat hard to know what your command is supposed to do without the context of the first post.

As for the command itself, *-vcodec copy*, *-vb*, and *-sameq* are all mutually exclusive. You should choose one of those options, otherwise FFmpeg will ignore the other two and it isn't always obvious which option FFmpeg is actually using. Same for *-acodec copy* and *-ab*. *-vcodec copy* will "copy and paste" the input video to the output. There is no re-encoding. *-vb* will re-encode your video and will attempt to do so at the specified bitrate. *-sameq* is a [complicated beast](http://ubuntuforums.org/showpost.php?p=11319760&postcount=6). It is generally not recommended and does not mean "use the same quality for the output as the input" as the previous, misleading documentation used to suggest (the documentation has since been updated upstream).

---

