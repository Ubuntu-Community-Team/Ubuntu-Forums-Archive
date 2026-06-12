---
title: "cracky sound with jack"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by FunkyMunky on 2007-08-03
i'm using an integrated sound card on asus m2n-e, the system is xubuntu 7.04 feisty fawn.

i've installed a bunch of audio programs such as ardour, hydrogen, audacity, creox, xmms etc.
so since i don't have any input device to test creox (a sound processor, i'm planning to connect it to my bass guitar when i buy it), i started up jack, set xmms to use jackasyn output plugin and set creox to use xmms as input. everything worked as expected, except one thing: the sound was full of popping  and cracking.  it happens with any app using the jack output.

i've been toying around with jack options, still no success. could it be that my sound card is just too bad to handle jack? will buying a new sound card help (SB audigy SE maybe)? 

please help..:popcorn:

---

### Post by nlz on 2007-12-03
same problem here: crack-i-jack :)

---

### Post by christhemonkey on 2007-12-03
Does Jack report xruns?
This is very likely what your problem is.

---

### Post by nlz on 2007-12-04
no x-runs with me anymore since i'm working in realtime, the only cracks I still get are from XMMS, and i think these originate in the jackasyn 0.1 driver..

thanks

---

