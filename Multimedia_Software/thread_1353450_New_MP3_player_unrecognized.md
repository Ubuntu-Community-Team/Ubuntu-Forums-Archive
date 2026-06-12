---
title: "New MP3 player unrecognized"
date: 2009-12-12
forum: Multimedia Software
---

### Post by tv0571 on 2009-12-12
Some Ubuntu music players like Quod Libet rely on a file to identify the fact that your MP3 player is in fact a music player, and not just a thumb drive.

My daughter just got a Disney Mix Stick (Hannah Montana).  Quod Libet wouldn't recognize it as a music player and I couldn't transfer tunes.  This link describes which file needs to be edited & how.
[http://blog.pcode.nl/2006/08/24/introducing-hal-to-your-digital-audio-player/](http://blog.pcode.nl/2006/08/24/introducing-hal-to-your-digital-audio-player/)

QL now recognizes the player and all works well.  

I had to do something similar a few months ago for a Sansa Fuze.  Thought I'd post this as others may be having similar questions.

---

### Post by N00b-un-2 on 2010-01-03
add a file called *.is_audio_player* to the root of your daughters music player.  I don't know if this works for quod libet, but it works just fine on Rhythmbox and Banshee (and it kind of works on Exaile)

---

