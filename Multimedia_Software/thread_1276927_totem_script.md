---
title: "totem script"
date: 2009-09-27
forum: Multimedia Software
---

### Post by cletus550 on 2009-09-27
Could anyone help with writing shell scripts for totem?

I would like to start the movie, go to full screen, move two minutes in, show two minutes and then quit.

totem --fullscreen vid.mp4

starts the movie and jumps to full screen but 

totem --fullscreen vid.mp4
totem --seek-fwd

doesn't start and then jump forward. Instead it waits for the first command to complete and then runs totem again with no file. 

The man page says 'The following options command an already running instance of **totem** to do something' but I don't understand how to address the already running instance in order to send the commands.

A few examples of scripts that control totem would be very useful.

This is running on ubuntu 8.10 on eee 901.

---

### Post by sisco311 on 2009-09-27
Hi and welcome to the forums!

You have to run totem in the background:
```
totem --fullscreen vid.mp4 **&**
totem --seek-fwd **&**

```

or use mplayer:
```
mplayer -fs -ss 00:02:00 -endpos 00:02:00 path/to/file
```:evil:

---

### Post by cletus550 on 2009-09-28
Thanks for the pointer.

mplayer is much easier to control

---

