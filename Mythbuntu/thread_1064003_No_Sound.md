---
title: "No Sound"
date: 2009-02-08
forum: Mythbuntu
---

### Post by ocken on 2009-02-08
Hi all,

I just got a de-branded HP media center PC for the purpose of making a Myth box.  I am currently running the 64bit version.  I have installed an Nvidia 5500 card with an Svideo out and can get no sound out of the card, in mplayer it gives me an error that pulse cannot connect to server.  Also odd is aplay -l only seems to read an nvidia analog and a nvidia digital device and not the onboard audio, which I would prefer the sound to go through to be able to hook it up to my surround.  Any help would be great

---

### Post by ocken on 2009-02-08
check that I now have audio in VLC not in Mplayer

---

### Post by slick666 on 2009-02-08
I assume your audio out analog and not digital (spdif) but if not please say so.

Check under the setup->setup->general then the third screen. Make sure that you do not have either pass through options enabled, and all your sources are set to default. Also turn off internal volume controls as well just to be sure.

I hope that gets you somewhere.

---

### Post by ocken on 2009-02-08
no love, I have tried just about every setting in the mythbuntu frontend between alsa-digital and alsa analog, outside of the front end I was able to get both mplayer and vlc working using alsa

---

