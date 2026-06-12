---
title: "Recording what u hear"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by abh83 on 2007-11-24
Is there anything i can use to record what I'm currently listening to off my computer? I remember back in my winblowz days i used the recording option in the creative software (got it along with my creative soundcard).

(and if possible directly into mp3 format)

(maybe even a plugin for audacious?)

cheers

:guitar:

---

### Post by ron999 on 2007-11-24
Hi
You can use **arecord**

There's a tutorial here:-[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")

It works OK for me with Feisty.
I found it tricky to set up alsamixer, but I got it right eventually.
Sometimes I save it as a wav file then convert it all to mp3 afterwards with lame.
Read the responses in the tutorial, there's a typo in the mp3 command he uses.
The command to record as wav is:-
**arecord -f cd out.wav**

8):guitar:8)

---

### Post by abh83 on 2007-11-24
cool thx a lot.. will look into it!

---

### Post by irw on 2007-12-12
I am trying to do this currently.

Unfortunately the file produced by acrecord is very, very quiet.  If the volume is turned up to 100% i hear a hiss plus a very quiet version of what i recorded.

Any ideas what may help this.

Several hours trawling the internet have not helped so far ...

---

