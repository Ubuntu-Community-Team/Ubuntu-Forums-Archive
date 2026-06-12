---
title: "2 PCM loops with alsaloop"
date: 2015-11-21
forum: Multimedia Software
---

### Post by Jonathan_Zaentz on 2015-11-21
I seem to be unable to get two instances of alsaloop running properly.

"alsaloop -C hw:1,0 -P hw:0,0 -c 1 -t 50000 -d" works fine

as does "alsaloop -C hw:0,0 -P hw:1,0 -c 1 -t 50000 -d" 

when each is used alone but when I use both lines I get a metalic buzzing through the output devices.

Basically I'm linking 2 USB headsets so they function as intercoms with an additional feed for a video game - every thing seems to work as expected until I run the 2 instances of alsaloop together.  I have a feeling that I need to indicate that I should be using separate "mixer" hardware but I'm unable to decipher the syntax.  I have spent more than a few days searching for answers but I have only found the same question asked a couple of times a few years ago.

Thank you in advance for any help.

---

