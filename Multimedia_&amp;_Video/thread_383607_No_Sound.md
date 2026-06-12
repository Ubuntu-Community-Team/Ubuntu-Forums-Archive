---
title: "No Sound"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by manicman on 2007-03-13
Hi there im trying to get my server to play audio CD's but I'm not doing to well. at the moment cdtool (cdplay) and dcd seem to be playing and the cd spins up but there is no sound. mplayer and mpd work fine so my onboard sound card is working. my server runs an alternate install of edgy 6.10 and has very little installed so im pretty sure its due to the lack of applications but im struggling to work out what to install, does anyone have any ideas ?

Many Thanks Chris

---

### Post by zvacet on 2007-03-13
Do that players support formats you want to play?

---

### Post by manicman on 2007-03-13
yes its directly from an audio cd and thats what the programs are designed for

---

### Post by panch0 on 2007-03-14
So if MPlayer works, why not use it to play the audio CD:

mplayer cdda://

Even better get KPlayer, it detects audio CDs and plays them nicely with MPlayer.

---

