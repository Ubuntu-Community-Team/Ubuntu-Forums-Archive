---
title: "What is the ffmpeg command for converting avi to mov?"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by jclmusic on 2007-03-28
couldn't find it on a search. anyone know what the correct command is?

---

### Post by Rui Pais on 2007-03-28
Hi, try 

```
man ffmpeg
```

besides being extremely informative on the thousand of options on each codec/format it gives a lot of examples on how to use it.

hth

---

### Post by fenian on 2007-03-28
For dvd quality conversion try
> 
ffmpeg -i filename.avi -target ntsc-dvd filename.mov

replace filename with appropriate filename.Replace ntsc with pal if you need to.

---

### Post by jclmusic on 2007-03-28
thank u so much!

---

### Post by hihihi on 2008-02-05
-target pal-dvd gives a .mov container with mpeg2
but if you just want to convert dv .avi to .mov than use -target pal-dvvideo
like:
$ ffmpeg -i input.avi -target pal-dvvideo output.mov
cheers

---

### Post by ron999 on 2008-02-05
Yeah, pal-dvd for UK. And ntsc-dvd for USA.

---

