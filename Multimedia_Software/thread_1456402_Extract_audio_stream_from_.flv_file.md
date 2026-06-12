---
title: "Extract audio stream from .flv file"
date: 2010-04-17
forum: Multimedia Software
---

### Post by rookworm on 2010-04-17
Hello, I would like to know how to demux the audio from a flash video file (copied from /tmp while browsing a video site). I would prefer to avoid re encoding if possible. Thanks!

---

### Post by ron999 on 2010-04-17
Hi
What format is the audio track (soundtrack) in now, is it mp3 or aac or what?
If you're not sure use **mediainfo** to find out.
Or use this command:-
```
ffmpeg -i filename.flv
```

---

### Post by rookworm on 2010-04-17
I actually have several, some are mp3, some are aac (I got most of them from youtube

Edit: the one of most interest to me is aac

---

### Post by ron999 on 2010-04-17
Ok
For the mp3 tracks use this command:-
```
ffmpeg -i filename.flv -vn -acodec copy whatever.mp3
```

For the aac tracks use this command instead:-
```
ffmpeg -i filename.flv -vn -acodec copy whatever.m4a
```

It's quite easy to use Winff to do the job if you have several.
I'll explain the settings if you're interested.

---

### Post by rookworm on 2010-04-17
Sweet! Thanks, it worked. I'll try to figure out how later :) Presumably, something similar can be used to make an .mp4 video that can be played on a portable device, no?

---

### Post by ron999 on 2010-04-17
Yes, _but only if they use permitted codecs_ such as aac audio and avc video you can use command:-
```
ffmpeg -i filename.flv -acodec copy -vcodec copy whatever.mp4
```

To see which are the permitted codecs for mp4 look at this table here:-[http://en.wikipedia.org/wiki/Comparison_of_container_formats]("http://en.wikipedia.org/wiki/Comparison_of_container_formats")

---

