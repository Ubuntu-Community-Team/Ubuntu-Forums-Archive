---
title: "Vive help!!"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by kerme8503 on 2006-10-17
Hello, I have installed vive on my ubuntu compy, and it opens up fine, it just doosent encode when i push the encode button.  I set everything up, hit the button, and nothing happens...not even any recognition of my button pushing...it just sits there... help!!

---

### Post by kerme8503 on 2006-10-17
BUMP!!  need help!!

---

### Post by kerme8503 on 2006-10-18
BUMP BUMP BUMP!!!  Comon, someone needs to know something about this...

---

### Post by kerme8503 on 2006-10-18
BUMP!!! ahh!  i need help here ppl.

---

### Post by skymt on 2006-10-18
Two questions:

* If you run it from a terminal, does it output anything interesting?

* How long have you "let it sit"?

---

### Post by kerme8503 on 2006-10-18
I dont know the command to run from terminal, i tried ```
 vive 
```  but all i get is this long thing like "blah blah in line 368" something, but if i need to run more in terminal, let me know.  i know im a noob sry lol.

EDIT  I forgot about the 2nd part.  not long but it didnt show any signs of working so i just quite after 1 or 2 min.  next, i just tried ```
 vive ./"The Office"/theoffice1.01.avi theoffice1.01.mp4
```  but it opened up vive gui and sat there.  :\

---

### Post by skymt on 2006-10-18
> **kerme8503 said:**
> I dont know the command to run from terminal, i tried ```
 vive 
```  but all i get is this long thing like "blah blah in line 368" something, but if i need to run more in terminal, let me know.  i know im a noob sry lol.

The blah blah is exactly what I want to know. Copy and paste all the output you get, and I'll see if I can help.

---

### Post by kerme8503 on 2006-10-18
ok wait now it just opens up vive gui...it reinstalled it but didnt test the command again.  sorry.

---

### Post by kerme8503 on 2006-10-18
bump

---

### Post by skymt on 2006-10-19
> **kerme8503 said:**
> bump

So can you tell me what it outputs? I can't help you without knowing what's wrong. Just run "vive" in a terminal, and copy and paste what you get.

---

### Post by unique on 2006-11-20
I have the same problem. Running vive from terminal open the gui when i hit encode i get this in the terminal

```
Use of uninitialized value in concatenation (.) or string at /usr/local/bin/vive line 70.

```

---

### Post by kaffekopp on 2006-12-12
Same problem here. When I hit encode, the line:
```
Use of uninitialized value in concatenation (.) or string at /usr/local/bin/vive line 70.

```
keeps popping up endlessly...

Would really appreciate help with this or info on alternative ways of encoding video for the 5g ipod

---

### Post by Scotty562 on 2007-05-15
Same thing is happening to me.

Here is a small sample:

```
readline() on closed filehandle DEFAULTS at /usr/bin/vive line 1013.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 1017.
Use of uninitialized value in split at /usr/bin/vive line 1018.
Use of uninitialized value in substitution (s///) at /usr/bin/vive line 1019.
Use of uninitialized value in substitution (s///) at /usr/bin/vive line 1020.
Use of uninitialized value in regexp compilation at /usr/bin/vive line 1031.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 1031.
Use of uninitialized value in split at /usr/bin/vive line 1058.
Use of uninitialized value in substitution (s///) at /usr/bin/vive line 1059.
Use of uninitialized value in substitution (s///) at /usr/bin/vive line 1060.
Use of uninitialized value in split at /usr/bin/vive line 1064.

```

Having this tool working would be amazing :). One less reason I'd need to boot into windows.

---

