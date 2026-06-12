---
title: "VLC media player"
date: 2009-08-31
forum: Multimedia Software
---

### Post by norm.h on 2009-08-31
I have VLC media player 0.9.9a Grishenko set up as my default player in Ubuntu 9.04.
Whenever I play any audio CD, VLC always starts at Track 10, progressing numerically upwards and after the last track, continues with Track 1.
Is it possible to set VLC to start at Track1?
There doesn't seem to be any relevant setting choices in Preferences.
norm

---

### Post by mc4man on 2009-08-31
The issue from autoplay is it's probably using the wrong launch command for audio cd's. (I'm using hardy where it does use the wrong command

First confirm the tracks will load in proper order by opening vlc -> media -> disk -> audio cd.

If you get the proper order there then post what release of ubuntu your using.

If you have more than 1 cd/dvd drive mention also, would need to ck. my desktop to see if it works right with 2 drives. (desktop is setup to autoplay amarok from either drive, but would be easy to ck.

Are you seeing or do you want to see the track names.

Edit:
tested on desktop with 2 drives, works fine as autoplay with proper ordering though the method for 2 drives is slightly more invoved

---

### Post by Zimmer on 2009-08-31
sort order could be alpha...
might explain the behaviour.

10 11 12 13 then 1 (1<space>)  <space> coming after the numerals in the sort order.

or it could be <space> 1 <space> 2 etc.  The effect would be the same if the program treats the track number as text... so could be a bug/feature in VLC, maybe. Perhaps there is an option to adjust the sort order....

---

