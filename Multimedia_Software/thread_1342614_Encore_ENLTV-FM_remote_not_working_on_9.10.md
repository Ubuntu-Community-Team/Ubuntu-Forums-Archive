---
title: "Encore ENLTV-FM remote not working on 9.10"
date: 2009-11-30
forum: Multimedia Software
---

### Post by badkuk on 2009-11-30
hi peeps,

Any ideas on how to make this work? i installed Ubuntu 9.10 from scratch with the ENLTV-FM card installed; it seems to load the proper drivers(detected as card=148) and tuning and audio works fine, but the remote isn't working. Running irw doesn't output any response when pressing the buttons.

/etc/lirc.conf seems to load the correct config(enltv.conf) as well. Any ideas on where to look? How can i increase logging for lircd/irw?

tia

---

### Post by dangerous666 on 2010-01-26
Same here... :(

---

### Post by sports.car.guy on 2010-01-27
I hate to be the bearer of bad news, but, just because the card is loaded and working when it comes to TV cards on Linux, that does not mean the IR receiver and remote will work. That should not be assumed to be the case or that it is a given. A lot of cards are supported, even a few on board IR chipsets on supported cards, just not a lot of them. if you google about it and check out the linuxtv.org wiki page for your card you should know if it is or not and go from there.

Even if the IR is supported, I would honestly suggest spending $15 - $30 on a Windows Media Center / Vista / 7 remote. It is worth the investment. I love having mine and never regretted the purchase.

---

