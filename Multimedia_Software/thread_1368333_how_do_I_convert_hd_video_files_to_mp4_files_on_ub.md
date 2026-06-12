---
title: "how do I convert hd video files to mp4 files on ubuntu?"
date: 2009-12-30
forum: Multimedia Software
---

### Post by snsdfan on 2009-12-30
Hi, I can't seem to find a software that can convert .ts and .tp files to mp4 files in ubuntu. And also, multimedia programs such as the mplayer doesn't creat thumbnail images for .tp and .ts files, I would appreciate it so much if anyone inform me of a program that does create thumbnail images for .tp and .ts files?

---

### Post by LuisGMarine on 2009-12-30
I've used handbrake to convert my hd video files to mp4.

However my hd files were .mts files, but I'm sure yours are supported also.  Let me know how it goes, here is the website:

[http://handbrake.fr/]("http://handbrake.fr/")

---

### Post by snsdfan on 2009-12-30
i went to the website, clicked on the **Ubuntu 9.10 deb - GUI** 32bit download and the system gave me a error saying it's the wrong architecture "i386". this also happened to **Ubuntu 9.10 deb - CLI** 32bit. I'm new to ubuntu, what should i do?

---

### Post by LuisGMarine on 2009-12-30
What is the output of:

```
uname -m
```

---

### Post by snsdfan on 2009-12-30
i have no idea

---

### Post by LuisGMarine on 2009-12-30
Ok.  Go to Applications > Accessories > Terminal, and type in that command I gave you above.  Then post the output of that.

:lolflag:

---

### Post by howefield on 2009-12-30
> **snsdfan said:**
> i have no idea

Brilliant :)

He means for you to open a terminal from Applications > Accessories > Terminal and type 

```
uname -m
```

---

### Post by snsdfan on 2009-12-30
x86_64

---

### Post by HappyFeet on 2009-12-30
Go [here]("http://handbrake.fr/downloads.php") and download the 64bit version of handbrake for ubuntu. You didn't know you were using 64bit ubuntu?

To save you the trouble, [here]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.4-Ubuntu_GUI_x86_64.deb") is a direct link to the file you want.

---

### Post by snsdfan on 2009-12-30
to be frank with u, i thought i downloaded the 32-bit version, so, yeah lol im a noob 
thanks tho i really appreciate it.

---

### Post by LuisGMarine on 2009-12-30
lol that was one of the funniest responses in the ubuntu forums.  So tell us did it work or what?

---

### Post by snsdfan on 2009-12-30
yes it worked but the converting speed is much slower than the one i use in windows :(

---

### Post by LuisGMarine on 2009-12-30
That area I'm not 100% sure.  Thats something you might have to research.  I've read many forums and articles on 32-bit vs. 64-bit and one thing where significant improvements are recorded are in the video conversion.  But you already have Ubuntu 64-bit so ... I'm not sure.

Best of luck to you!

---

### Post by snsdfan on 2009-12-30
do you know a good hd video player in ubuntu? that creates thumbnail images for the video? i think that was a part of the question but no one took notice of it. i dont want to post another thread, just to save some time. ur help is deeply appreciated. if no one answers i'll post a new thread.

---

