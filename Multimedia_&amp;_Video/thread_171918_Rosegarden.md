---
title: "Rosegarden"
date: 2006-05-07
forum: Multimedia &amp; Video
---

### Post by the_tiger on 2006-05-07
I am looking for good free notation software. Rosegarden stands out but what do you  think? Also if I am to run a music studio using rosegarden what distribution is currently easiest to use in terms of set up. If a live CD were available that would be particularly useful.

---

### Post by ncappel1 on 2006-05-07
I am a musician myself, and I regret to inform you that there are no music notation programs (at least any i've heard of) that match the level of Sibelius or Finale, for mac and windows respectively.

Lilypond is supposed to work well, but it is really a typesetting program. If you have music written in front of you and you need to make it neat and professional looking, it can do that. I have tried it and personally it is not good for composing on the spot. The problem is that the input it not gui, it is text based. the output is in music notation, however. It is very important to see the music and to be able to visualize it right in front of you. 

Rosegarden will output to standard music notation too, but it is mainly a sequencing program. It hasn't even worked well on my computer, to be honest, something about ALSA and jack servers that I never figured out. 

here is an ubuntu project, the ubuntu studio: http://ubuntustudio.com/wiki/index.php/Welcome,_Musicians!

here's another page with some good info you can explore and try out:
[http://linux-sound.org/notation.html](http://linux-sound.org/notation.html)

from the website: [http://linux-sound.org/](http://linux-sound.org/)

---

### Post by dolson on 2006-05-07
[img]http://denemo.sourceforge.net/0.7.3beta2-4tet.png[/img]
[Denemo](http://denemo.sourceforge.net/)

---

### Post by ncappel1 on 2006-05-08
im starting to rethink my opinions, I should check that out. thanks for the link!

learn something new every day!

---

### Post by the_tiger on 2006-05-08
Has the notation in rosegarden not improved alot since the release in February?

---

### Post by ssavelan on 2007-02-10
I am game to try anything that is compatible with JACK.  Rosegarden seems like it may be worthwhile; although, it is a little bigger and more bloated than I like.  Does anyone know what the following error may mean:

[http://ubuntustudio.com/wiki/index.php/Welcome,_Musicians](http://ubuntustudio.com/wiki/index.php/Welcome,_Musicians)!

........ oh crud, I pasted that link over my error message....... well it says it can't find a time with the resolution needed and that I should try to contact ubuntu to find out how to set my kernel resolution higher or something.....

darn.... will try to get message up soon.

---

### Post by evfan42 on 2008-01-07
so I got two errors when I tried to load rosegarden.. on was failed to connect to JACK audio server.. then, System timer resolution is too low someone help me fix this?

---

### Post by eric71 on 2008-01-09
For the jack error, the easiest solution is to install QJackCtl, a control program for the Jack server.  Doing this will also install jack itself.  You will need to start jack via QJackCtl before starting Rosegarde to use normal audio or DSSI instruments. If you only plan to use MIDI with timidity or qsynth for output, then you don't need to worry about the jack error. 

For the timing error - the default kernel has its timer resolution set too low for professional MIDI use. If you install and use the realtime kernel, this won't be a problem.

---

### Post by marufaberlin on 2008-01-09
Denemo is a good program for typesetting music, but it misses some features. For example dynamics are not fully supported, special guitar bends, pitch bends, and other things are fust missing. If you do not need that, Denemo is the perfect choice. Personally, Denemo does not include enough features for me, such as on-the-fly moving of notes.

The installation of QJackCtl does not solve the problem for me. I always get the error message

*can't find server ` default'*.

The thing is, the day I installed Jack, it worked perfectly, but after a reboot, thigs didn't work out so well. Does anyone know anything to do?

Thx marufaberlin

---

