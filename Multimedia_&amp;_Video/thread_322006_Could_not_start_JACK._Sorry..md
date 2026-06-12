---
title: "Could not start JACK. Sorry."
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by EMoShunz on 2006-12-19
[FONT="Palatino Linotype"]I can not start JACK.  I have AMD64 3000+ DFI NForce 4 with on board audio.  I want to start playing with Hydrogen and jokosher etc for fun, but I can't even get Jack to work.  I read a bunch of threads, all of them jack at least starts.  Here is my error:
20:03:02.699 Patchbay deactivated.
20:03:02.708 Statistics reset.
20:03:02.879 MIDI connection graph change.
20:03:02.939 MIDI connection change.
20:03:06.593 Startup script...
20:03:06.593 artsshell -q terminate
sound server terminated
20:03:06.996 Startup script terminated successfully.
20:03:06.996 JACK is starting...
20:03:06.996 jackd -dalsa -dhw:0 -r44100 -p1024 -n2
20:03:06.999 Could not start JACK. Sorry.
20:03:12.332 JACK was stopped successfully.

As a side, my audio works.[/FONT]

---

### Post by EMoShunz on 2006-12-20
Can anybody help?

---

### Post by EMoShunz on 2006-12-20
[FONT="Palatino Linotype"]I'm not too proud to beg. PLEASE HELP.[/FONT]

---

### Post by EMoShunz on 2006-12-20
[FONT=Palatino Linotype]If no one can help, could someone plesae direct me to some place that can?[/FONT]

---

### Post by deadgobby on 2006-12-21
If you install Jack. Before you start your program. Open up the Terminal and type in jack.  That should start jack and DO NOT CLOSE THE TERMINAL. Do so will end Jack.
See Ubuntu Studio.
[http://www.ubuntustudio.com/](http://www.ubuntustudio.com/)

Gobby

---

### Post by EMoShunz on 2006-12-21
[FONT="Palatino Linotype"]Thank You!  I will try that and post the results!  I almost gave up.  I appreciate the link as well.[/FONT]

---

### Post by deadgobby on 2006-12-22
No problem. I use Jack myself. I install Ubie studio and pretty slick o roo.
Gobby

---

### Post by EMoShunz on 2006-12-22
OK, Please don't laugh, I'm green.  I didn't have 'jackd' installed in the respratories.  So I added that.  FYI to anyone reading this, the volume control that loads automatically will keep you from starting JACK.
I have this issue now, no sound out of my audio programs (Hydrogen and Ardour).  Any thoughts?

---

