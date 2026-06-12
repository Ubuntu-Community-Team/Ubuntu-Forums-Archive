---
title: "720p conversion"
date: 2010-08-22
forum: Multimedia Software
---

### Post by sandyd on 2010-08-22
I did some screen recordings for some games (using frapps) and I wanted to convert it to 720p and upload it onto youtube. my screen resolution is 1440x900, while the 720p resolution is 1280x720. the anoying thing is, even after installing... like 4 video editing programs, it still has to add black borders to both the width and the height even though the resolution of the source is larger than what im converting to. help???

---

### Post by Bachstelze on 2010-08-22
You can use the -s flag to ffmpeg: 

```
ffmpeg -i source.mp4 -acodec copy -s hd720 output.mp4
```

And see if the video quality is good enough for you.  Otherwise you will need higher video quality settings, but I'm not very familiart with ffmpeg (shouldn't be too hard to find, though).

---

### Post by cariboo on 2010-08-22
Moved to the proper place for a support question.

---

