---
title: "m4a files and mp3"
date: 2020-07-19
forum: Multimedia Software
---

### Post by devdlp on 2020-07-19
so some of my music is m4a files when i want all of them to be mp3 format becuase i use mixxx to dj how do i MASS get rid of the m4a format songs please and thank you

---

### Post by Yellow Pasque on 2020-07-19
If they're all in one directory, this should do it:
```
for i in *.m4a; do ffmpeg -i "$i" -c:a libmp3lame "${i%.*}.mp3"; done
```

See: [https://trac.ffmpeg.org/wiki/Encode/MP3](https://trac.ffmpeg.org/wiki/Encode/MP3) for more options to control bitrate. Be aware that converting m4a (AAC) to mp3 is a lossy to lossy conversion and will result in audio quality loss.

---

