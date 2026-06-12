---
title: "Which ffmpeg profiles for ogg/theora/vorbis ?"
date: 2012-03-18
forum: Multimedia Software
---

### Post by Lucas Malor on 2012-03-18
What profiles ffmpeg has by default for ogg/theora/vorbis encoding?

---

### Post by andrew.46 on 2012-03-18
I am not sure I fully understand your question but perhaps this post might help out:

[http://ubuntuforums.org/showpost.php?p=11530735&postcount=2](http://ubuntuforums.org/showpost.php?p=11530735&postcount=2)

---

### Post by Lucas Malor on 2012-03-18
Thank you for the link, it's very useful. Anyway it's not exactly what I'm looking for. I'm searching ogg presets (not profile, excuse me). An example of h264 presets: [http://juliensimon.blogspot.it/2009/01/howto-ffmpeg-x264-presets.html](http://juliensimon.blogspot.it/2009/01/howto-ffmpeg-x264-presets.html)

---

### Post by andrew.46 on 2012-03-18
OIC :). Unfortunately the only presets available to FFmpeg in the official source code are those for FFmpeg and libvpx. It is possible that somebody has written presets for theora + vorbis but I have not seen these.

---

### Post by Lucas Malor on 2012-03-19
Thank you anyway :) I think I'll retry to use ffmpeg2theora. At least it's more user-friendly :P

---

### Post by andrew.46 on 2012-03-19
Fair enough, it is purpose built to produce ogc files after all. The command line I used to use with FFmpeg2theora was something like this:

```

ffmpeg2theora -v 8 -a 6 <input> --no-skeleton --optimize -o <output>.ogv

```

but it has been a while since I have used it.....

---

