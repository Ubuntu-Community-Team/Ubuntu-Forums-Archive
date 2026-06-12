---
title: "Mixer Help"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by sbjaved on 2007-07-01
Feisty user with Cirrus Logic CS4281 PCI Sound card.

My problem is that if one application is using sound (e.g. Amarok), the other apps will only give audio output IF THE FIRST APP (e.g. Amarok) STOPS USING SOUND. This is proving a real show stopper for me. 

Workaround?

---

### Post by morgan_greywolf on 2007-07-01
My guess is that either the driver for that chipset doesn't support hardware mixing or the chipset itself doesn't include hardware mixing. Without hardware mixing, on Linux the first application that uses the sound card gets to use it, and other applications will not have access to the driver.  AFAIK, your only recourse is to get a different sound card, or to find a driver that supports hardware mixing if the chipset does in fact support it.

---

### Post by sbjaved on 2007-07-01
> **morgan_greywolf said:**
> My guess is that either the driver for that chipset doesn't support hardware mixing or the chipset itself doesn't include hardware mixing. Without hardware mixing, on Linux the first application that uses the sound card gets to use it, and other applications will not have access to the driver.  AFAIK, your only recourse is to get a different sound card, or to find a driver that supports hardware mixing if the chipset does in fact support it.
A course that I'm not likely to take soon :)

I *did* hear somethimg about "software mixing" but I'm not sure what it is and how to get it running...

---

### Post by sbjaved on 2007-07-02
Okay... I read an ALSA Wiki describing "dmix" plugin and how to enable it. Played with the configuration a bit and now my card works with different apps happily! Posted the detail on [my blog]("http://sbjaved.blogspot.com/") if anyone else has the same problem.

---

