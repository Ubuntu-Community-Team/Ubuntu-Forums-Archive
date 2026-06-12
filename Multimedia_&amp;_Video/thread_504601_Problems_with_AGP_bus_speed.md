---
title: "Problems with AGP bus speed"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by Canesfan2020 on 2007-07-19
ever since about 2 releases ago my X700 pro has been locked into 0x AGP vs It use to be 8x agp..i have searched everywhere and cant find any clues to the issue.. is this a driver problem or is something suddenly not loading in linux? im using fglrx

---

### Post by wolfen69 on 2007-07-19
is everything working correctly? if so, i wouldnt worry too much about how it's being reported.

---

### Post by jrusso2 on 2007-07-19
Check the bios setting for the AGP

---

### Post by Canesfan2020 on 2007-07-19
> **wolfen69 said:**
> is everything working correctly? if so, i wouldnt worry too much about how it's being reported.

I dont know if its a side effect of it or not bug moving windows around the desktop and stuff gets a little laggy sometimes and trying to use XGL is a joke...super lag.

surely my pc isnt that crappy.. Athlon64 3200 1gb ddr2

---

### Post by phreadom on 2007-09-03
I'm having this same problem. The BIOS is set correctly etc.

DRI is enabled... everything is working correctly except for the AGP bus speed being set to 0x... and as Canesfan2020 said, the speed is horrible... probably less than 10% of what it should be.

I've seen a number of people post with this same problem, it was known even before the release of Feisty Fawn, but for some reason they didn't consider it a show stopper and went ahead with the release. The latest several kernel revisions/xorg releases all seem to suffer from this, but I haven't seen any more definite details.

---

