---
title: "Weird film format"
date: 2008-05-23
forum: Multimedia Software
---

### Post by GabrielWolff on 2008-05-23
I got a film cut in 10 parts, looking this way:
```
When.Harry.Met.Sally..001  When.Harry.Met.Sally..005  When.Harry.Met.Sally..009
When.Harry.Met.Sally..002  When.Harry.Met.Sally..006  When.Harry.Met.Sally..010
When.Harry.Met.Sally..003  When.Harry.Met.Sally..007
When.Harry.Met.Sally..004  When.Harry.Met.Sally..008

```
Nautilus refers to file no.1 as* .avi* and to all the others as to *program*.

How do I paste these files together?

---

### Post by zatoichi0 on 2008-05-23
This should work:

open up a terminal in the folder with the parts and run:

```
cat * > When.Harry.Met.Sally.avi
```

---

### Post by GabrielWolff on 2008-05-23
> **zatoichi0 said:**
> This should work:

open up a terminal in the folder with the parts and run:

```
cat * > When.Harry.Met.Sally.avi
```

Thank you a a lot :)
I tried this and it seemed to work in the beginning, but when opening the film file, VCL states the file is broken.
After fixing it, the film doesn't really reach the end...

Any clue about this?

---

### Post by aeiah on 2008-05-23
it looks like a usenet thing. nzb and par type stuff. i usually go for .rar scene releases

---

### Post by solitaire on 2008-05-23
It's not a format, it's the file has just been split into parts.

---

### Post by GabrielWolff on 2008-05-23
OK, thanks a lot for the replies.
Any clue how to work on the broken file issue?

---

### Post by solitaire on 2008-05-23
sounds like you are missing a bit.

---

### Post by GabrielWolff on 2008-05-23
> **solitaire said:**
> sounds like you are missing a bit.

Any chance I can find out in which part of the split file the bit is missing?

---

### Post by solitaire on 2008-05-23
Think the best way is when you use the "cat" and specify each file in turn
```
 1@a:~$cat file.001 file.002 file.003 > movie.avi
```
One might be inserted out of order..

---

### Post by cor2y on 2008-05-23
You could try using a joining app like lxsplit or the frontend gtksplit or via wine both hjsplit or glue.
They should tell you if you are missing parts before joining the file.

---

### Post by GabrielWolff on 2008-05-24
> **cor2y said:**
> You could try using a joining app like lxsplit or the frontend gtksplit or via wine both hjsplit or glue.
They should tell you if you are missing parts before joining the file.

Can't find those packages.
Which repositories do I have to enable?

---

### Post by xc3RnbFO8P on 2008-05-24
Maybe this:
[http://linux.softpedia.com/get/System/Hardware/gtk-splitter-014.shtml]("http://linux.softpedia.com/get/System/Hardware/gtk-splitter-014.shtml")
or this:
[http://linux.softpedia.com/get/Utilities/LX-Split-11067.shtml]("http://linux.softpedia.com/get/Utilities/LX-Split-11067.shtml")

---

