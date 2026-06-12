---
title: "Convert .avi + .srt to .mpg using FFMPEG"
date: 2009-04-13
forum: Multimedia Software
---

### Post by kpkeerthi on 2009-04-13
Is there a command line to convert an .avi file to .mpg (DVD), hardcoding subtitle from .srt file in the process using FFMPEG?

---

### Post by lovinglinux on 2009-04-13
It should be something like this:

```
ffmpeg -i original.avi -newsubtitle subtitle.srt -target ntsc-dvd -r 29.97 -s 720x480 -aspect 16:9 -b 8000k -g 12 -mbd rd -flags +trell -mv0 -cmp -subcmp 2 output.mpg
```

But when using the *-newsubtitle* option, it gives me an error. Maybe it will work if you try with a different subtitle format.

---

### Post by kpkeerthi on 2009-04-14
Did not work for me either.

Referring to the man page, it reads
> -newsubtitle
    Add a new subtitle stream to the current output stream. 
it looks like the -newsubtitle option is not for embedding/hardcoding the .srt file to the output file.

Any other pointers, perhaps with some other command line tools other than ffmpeg, is much appreciated.

---

### Post by kpkeerthi on 2009-04-14
Found [spumux]("http://linux.die.net/man/1/spumux") that does [the job]("http://www.linux.com/feature/139221").

Its a two step process. But I can live with it. 
1. Convert .avi to .mpg
2. mux .srt file to .mpg

---

