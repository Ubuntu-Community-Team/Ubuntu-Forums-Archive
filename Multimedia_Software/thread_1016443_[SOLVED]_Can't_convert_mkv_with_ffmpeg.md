---
title: "[SOLVED] Can't convert mkv with ffmpeg"
date: 2008-12-19
forum: Multimedia Software
---

### Post by Nazty_Nayt on 2008-12-19
Ok, I originally tried winFF to convert my mkv files, but just didn't seem to work.  So I decided to just use the command line to do it, but that's not working either.  So, this let's say have video1.mkv that I want to convert, and this is the line I run.

```
ffmpeg -i video1.mkv -acodec mp3 -vcodec mpeg4 -sameq video1.avi
```

It returns with this error.

```
video1.mkv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```

I've tried this line as well...

```
ffmpeg -i video1.mkv -vcodec copy -acodec copy video1.avi
```

And I get the same error.  Do I need to list the whole directory that the file is in when converting, or what.  I just can't seem to figure it out.  I even though, ok, maybe there's something wrong with the file, but no it plays just fine.

---

### Post by eye208 on 2008-12-20
If you can play the file with MPlayer, you can convert it with MEncoder. Both programs support the same file types for input.

---

### Post by Nazty_Nayt on 2008-12-20
Thanks I found a program called Avidemux and that's working how I want it too, and quick at that.

---

