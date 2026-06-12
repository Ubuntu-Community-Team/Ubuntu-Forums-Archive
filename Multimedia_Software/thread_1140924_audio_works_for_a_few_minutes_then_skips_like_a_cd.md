---
title: "audio works for a few minutes then skips like a cd"
date: 2009-04-28
forum: Multimedia Software
---

### Post by bernhardtjeff on 2009-04-28
just updated to 9.04. playing audio (mp3 so far, maybe others) in ANY audio player causes this problem... after a couple minutes, the audio starts glitching like a cd sound when it skips and won't work like normal again without a reboot. anyone else with this problem? would love to get a solution to it.

edit: here's some more info.

my soundcard is reported as "ati ixp ac '97." i've tried using alsa, oss and pulseaudio but it seems to happen evertime. playing videos with totem doesn't cause the sound to glitch, and playing flac files doesn't seem to make it glitch either, so maybe it's an mp3-related problem?

---

### Post by Darioff on 2009-04-28
Hi Im a Kubuntu user, i have the same problem and the same audio card. Ive been using ubuntu until now and ive just switched to kubuntu. In the previous relases removing pulseaudio fixed the problem. Now in kubuntu is not possible, there's only libpulse0 installed and removing it removes everything...

---

### Post by bernhardtjeff on 2009-04-28
well, glad to know someone else has the same problem... just wish we could get it fixed. i was able to get rid of pulseaudio completely, so now i'm playing some music and seeing if i can get it to skip again.

---

### Post by bernhardtjeff on 2009-04-28
bump.

really want to get some feedback on this... it's the only thing keeping me from seriously getting into ubuntu.

---

### Post by Darioff on 2009-04-28
Apparantly in Jaunty removing pulseaudio doesnt work, im going to downgrade to intrepid. too bad!

---

### Post by hardyn on 2009-04-28
upgrading to pulse 0.9.15 though a users PPA helped ALOT with my system.

---

