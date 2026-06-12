---
title: "Audacity, project sample rate and output device settings"
date: 2007-09-11
forum: Multimedia Production
---

### Post by Tyke91 on 2007-09-11
Whenever i try to edit mp3s with audacity or play them, or do anything... i always get this error

[[IMG]http://images7.pictiger.com/thumbs/fa/4e2161913dd93ea525757a175c160cfa.th.jpg[/IMG]](http://server7.pictiger.com/img/628220/picture-hosting/-home-mykola-desktop-thrill-.php)

what am i doing wrong and how can i fix it?

(it's michael jackson's "Thriller" in mp3 format)

---

### Post by rsambuca on 2007-09-11
Did you show audacity the path to the lame libraries?

Instructions can be found [here, on the Audacity wiki]("http://audacityteam.org/wiki/index.php?title=Lame_Installation#Linux.2FUnix_instructions"), if you care to look for yourself.

---

### Post by stmiller on 2007-09-12
That error means audacity cannot find/use your soundcard. I'm not sure if that has anything to do with that mp3 file.

Some onboard soundcards are fixed at 48000kHz. Looks like your project is at 44100. Try changing the sample rate in audacity to see if it works.

---

### Post by Tyke91 on 2007-09-15
hmm... something seems to have worked, because it registers that i have a sound card now...


but now it wont recognize any music format (ogg, mp3, wav, etc...)

it says that it cannot recognize the compression format, and asks me to try to import raw data... i tried that... it still wont work

---

