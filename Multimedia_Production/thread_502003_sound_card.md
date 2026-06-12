---
title: "sound card"
date: 2007-07-16
forum: Multimedia Production
---

### Post by cino on 2007-07-16
It is not ideal, to say the least, but at the moment, all I can afford is my onboard ASUS soundcard.
1) Can I get Ardour working with such primitive hardware or not bother?
2) Does any one have a spare sound card they can send me, *laugh* or rather, could you suggest one or some info...

The aim is recording live instruments + sampling if that helps.
I have some experience in pro tools so, m-audio is to pro tools and "....." is to Ardour?

*help. meep...

---

### Post by paulg on 2007-07-16
M-Audio works well with Ardour too! The Delta series cards are among the best supported in Linux audio. Many USB cards are supported and FireWire audio support is improving under the FFADO project.

However, basically anything that will run with Alsa drivers will work so I suspect your on-board (AC97?) card will run fine. You may not get the low latency you may desire but it should do the job.

---

### Post by dabl on 2007-07-16
I use Audacity for capturing audio from analog recordings.  I assume it would work the same if I plugged in a mic instead of the "line in" from the pre-amp.  I use the onboard "Intel HDA" audio chip, a STAC-92xx chip.

There's a low-latency Ubuntu kernel available in the repos -- works fine here.

:)

---

### Post by cino on 2007-07-17
Grazie!
And thanks for the reply!

---

### Post by skipkent on 2007-07-17
I'm getting amazing latency and quality with the built-in nvidia soundcard on my motherboard.  Low latency kernel is all you need.

By all means - WORK WITH WHAT YOU HAVE NOW - don't wait until you get a card or interface that someone else says is 'good enough'.  Work with what you have until you run into limitations that are unacceptable to YOU.  Until then, there's lot's to do, lot's to learn and fun to be had.

I can play soft-synths in real time, monitor input with fx in real time, no problem.  I have a nice alesis mixer going into the line in of the soundcard giving me 2 channels for recording.  It's actually easier than working under windows with my old (burnt out, sadly) Delta 1010lt.

When you NEED more inputs, the 1010lt is a great choice and well supported in Linux.  Right now, for song-writing and recording my own ideas, the built-in sound card is all I need.  Spend your money on a mic or mixer instead.

---

