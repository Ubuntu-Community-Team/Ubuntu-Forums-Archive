---
title: "Audacious song delay(not a sound problem)"
date: 2009-02-14
forum: Multimedia Software
---

### Post by theLured on 2009-02-14
Hello. I would like to know if there is a feature to pause a song for a few seconds directly after pressing the play button.

Something like this would allow me to press play, and have time to grab my guitar to play along.

---

### Post by Stochastic on 2009-02-14
The pause button works pretty good for this functionality.

If you struggle with the couple milliseconds that it takes to move your hand from the spacebar to the strings on your guitar, then you could easily setup jack to have a frames/period setting of like 4096 frames.  That would produce a long enough lag for your needs.

---

### Post by theLured on 2009-02-14
Thank you for your reply. I did try using jack, but realised that I could just use a terminal. I forgot that Audacious can be controlled from the command line.

I just run the command
audacious --stop; sleep 3s; audacious --play
or I can play an mp3 with 4 metronome ticks so I know when to get ready.
audacious --stop; mplayer metronome.mp3; audacious --play

I have set the commands as a Fluxbox key binding. Very handy.
I have been wanting to do this for a week and the solution was stupidly simple.

---

