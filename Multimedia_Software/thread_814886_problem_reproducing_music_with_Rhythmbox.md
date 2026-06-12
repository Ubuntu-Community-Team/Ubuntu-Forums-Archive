---
title: "problem reproducing music with Rhythmbox"
date: 2008-06-01
forum: Multimedia Software
---

### Post by El-ahrairah on 2008-06-01
Hi everyone :D

I'm opening this thread 'cause I've got a pretty big problem with Rhythmbox in ubuntu 8.04: I have imported all songs from the windows partition, but sometimes, when I start the program, it can't play them! (obviously, I HAVE mounted the filesystem :D)

that is: I double-click one song, but nothing happens.

the only solution I found up to now is to restart ubuntu, then it works correctly...

can any of you help me solving this problem? thanks!

---

### Post by kostkon on 2008-06-05
Try to run *Rhythmbox* from the terminal, i.e. like this:
```
rhythmbox
```
and check for any error messages to get an idea of what it may cause this problem.

You could also run *Rhythmbox* in debug mode, although a lot of output messages will be generated. You can pipe them to a file in your home folder like this
```
rhythmbox -d > ~/rb_output.txt
```

---

### Post by El-ahrairah on 2008-06-05
ok, thanks for the advice :D the next time the problems shows up, I'll try them, and hopefully see what has caused that problem

---

