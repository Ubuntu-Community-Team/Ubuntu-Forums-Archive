---
title: "transposing problems in KMid"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by jennhi on 2006-08-09
Hi! I got UbuntuStudio set up according to the wiki and am marvelling at the possibilities in the future. For now, I'm a french horn player looking to play midi files of the accompaniment for the pieces I'll be playing at a recital. So far I've been using timidity, which is irritating in that I don't have the option of pausing, adding a click track, slowing down, or speeding up.

So I installed the studio, ran JackControl and qsynth, and played the files in KMid. I've tried seq24 and rosegarden, and neither gave me any sound at all, but KMid did a good job, with one exception: all of the files seem transposed up a third, making them useless as accompaniment. I tried several different sound fonts and discovered they're all playing the same pitches, so I'm at a loss to figure out how to correct this or add transposition. In timidity, the pitches are fine. Can anyone clue me in to what I'm doing wrong?

Thanks!
Jennifer

---

### Post by dolson on 2006-08-10
My guess would be that you have JACK configured at 48kHz, but your samples are meant to be played at 44kHz... Try changing that in JACK.

---

### Post by jennhi on 2006-08-11
Thanks, Dolson! Where can I change it? Under "setup", maybe? what field? My sample rate says 44100 -- is that what you were referring to?

Thanks!
Jennifer

---

### Post by dolson on 2006-08-11
[http://ubuntustudio.com/wiki/index.php/Dapper:JACK_Configuration](http://ubuntustudio.com/wiki/index.php/Dapper:JACK_Configuration)

If you look in that image on that page, you can see the option for Sample Rate. Try changing that some, and see if it helps.. If not, I am stumped, but there are more knowledgeable people than I. :)

---

### Post by christhemonkey on 2006-08-11
Another French Horn player?! :o!

:D

---

### Post by jennhi on 2006-08-11
> **christhemonkey said:**
> Another French Horn player?! :o!

:D

Yup! In fact, if you go to [The Obedient Accomapnist]("http://www.hornmidi.com/") you'll get midi accompaniment files of tons of horn pieces.

Anyway, I went into the Jack setup and it indeed says 44100 as the sample rate, but the status is frozen at 48000 no matter what I select. How can I really effect a change?

Thanks!
Jennifer

---

### Post by christhemonkey on 2006-08-12
<offtopic> On the Obedient accompnist, it says that it is the old site?
Where would the new one be? </offtopic!>

Anywho, ill stop distracting your thread...
Seeming as im unable to help:(

---

### Post by dolson on 2006-08-12
You have to stop Jack and then start it again. There are buttons on the main QjackCtl window I think labeled as such.

---

### Post by jennhi on 2006-08-13
> **dolson said:**
> You have to stop Jack and then start it again. There are buttons on the main QjackCtl window I think labeled as such.

Unforunately, I've stopped and started it many times and it's still stuck in 48K. I've seen someone else on the Net has had the same problem but the solutions looked extremely complicated. Someone lent me a Studio Canvas indefinitely, however, so I won't be needing to fix this up anymore.

Thanks!
Jennifer

PS - christhemonkey, they've been saying they're the old site for quite some time (years, I think). The new one never went up, apparently. You'd probably want to save all their files soon as you can.

---

