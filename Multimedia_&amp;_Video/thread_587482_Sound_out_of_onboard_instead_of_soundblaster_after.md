---
title: "Sound out of onboard instead of soundblaster after Feisty install"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by Rawrhunter on 2007-10-22
I just installed Feisty and everything seems to be working except my sound. Ive got an Soundblaster Audigy card, and apparently this is pretty common.

In the sound preferences menu I can select my Soundblaster card, but I still get no sound.
Running

cat /proc/asound/cards

outputs

0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0x92200000 irq 21
1 [Audigy2 ]: Audigy2 - Audigy 4 [SB0610]
Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0x1000, irq 21

So my card IS installed and working properly, so I run

alsamixer -c 1

and make sure everything is turned up.

From looking at a few other forum posts, turning on or off the Audigy Analog/Digital Output Jack can sometimes work, however, mine still doesnt.

I also tried plugging my speakers into my onboard audio and everything worked fine, but I would like to use my sound card if possible.

How can I set my soundblaster to be the default output device?

Any help would be appreciated :)

---

### Post by Rawrhunter on 2007-10-22
I managed to get my Audigy set as my default by running some command I found in another post, so my 'cat /proc/asound/cards' now outputs:

 0 [Audigy2        ]: Audigy2 - Audigy 4 [SB0610]
                      Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0x1000, irq 21
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x92200000 irq 21

However, now I have no output from my onboard AND my soundblaster. Ive tried messing around with alsamixer a bit more but so far have had no luck.

---

