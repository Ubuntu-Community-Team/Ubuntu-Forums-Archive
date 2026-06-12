---
title: "TvTime/PCTV, no sound"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by ddaavviidd on 2007-04-11
Hi everybody!

I'm a happy new user of Ubuntu 6.10, there's just (so far) one thing that gets me a bit frustrated:

I can't seem to get any sound out of TvTime. I run it in Ubuntu (gnome), on a HP Pavilion AMD 64 computer. The TV card is a Pinnacle PCTV (PCI).

I've done a fair share of googling on the subject, without much luck.

I'm thinking the problem might be related to the fact that my sound card is integrated on the mother board, and there's nowhere to connect the sound cable from the tv card to the sound card. Now, on WinXP and with Pinnacles own software this isn't a problem, I can get the sound through PCI instead. But how do I do this on Ubuntu/TvTime?

I hope I'm making at least some sense.. :)

---

### Post by reclusivemonkey on 2007-04-12
> **ddaavviidd said:**
> 
I'm thinking the problem might be related to the fact that my sound card is integrated on the mother board, and there's nowhere to connect the sound cable from the tv card to the sound card.

How do you connect your sound card to your speakers?

---

### Post by ddaavviidd on 2007-04-21
nevermind, i found the solution here:

[http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa]("http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa")

all i had to do, yes ALL, was to type this line into the terminal:

> arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0

beautiful.

seems now though that tvtime isn't the best application if you want to get the sound through pci.

---

