---
title: "Possible to Extract Audio From Video With FFmpeg?"
date: 2011-08-29
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-08-29
Is it possible to convert an video file (will be .flv) to an audio-only file (.ogg or whatever) with FFmpeg? If so, do I have to add anything to the code or just specify the output as an audio file?

---

### Post by ron999 on 2011-08-29
> **dniMretsaM said:**
> Is it possible to convert an video file (will be .flv) to an audio-only file (.ogg or whatever) with FFmpeg? 
Hi
Yes, you would use a command like this:-
```
ffmpeg -i filename.flv -vn -acodec libvorbis -aq 6 filename.ogg
```

---

### Post by dniMretsaM on 2011-08-29
> **ron999 said:**
> Hi
Yes, you would use a command like this:-
```
ffmpeg -i filename.flv -vn -acodec libvorbis -aq 6 filename.ogg
```

I had read something about the [FONT=Courier New]-vn[/FONT] argument and wondered if that was what I was looking for. I guess it was. Thanks a bunch!

---

### Post by andrew.46 on 2011-08-30
> **dniMretsaM said:**
> Is it possible to convert an video file (will be .flv) to an audio-only file (.ogg or whatever) with FFmpeg?

Mind you many reasonable quality flv files contain aac audio these days and a simple *-acodec copy *would suffice in this case with either an mp4 or m4a container.

---

