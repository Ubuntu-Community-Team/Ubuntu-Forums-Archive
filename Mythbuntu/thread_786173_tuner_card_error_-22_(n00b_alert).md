---
title: "tuner card error -22 (n00b alert)"
date: 2008-05-07
forum: Mythbuntu
---

### Post by punter on 2008-05-07
hi,

firstly, if I'm posting in the wrong forum, sorry and please direct me somewhere better!

I'm running 7.10 and installed mythtv on top.

Then I bought a tuner card and installed it, the box says the card is a 
DViCO TV Tuner - FusionHDTV Home DVB-T
but when I opened the box it seemed I'd been "upgraded" to a Fusion Plus. At least, that's what the sticker says on the card's chip.

So I installed it, but when i run MythTv back end configuration. I try to ad a new card, but under the **card type: DVB**, it's not recognised. Under another card type, like MPEG4 etc, it is recognised. But that's not right? My card is a digital tuner, not a mpeg stream? right? If I try using this card type I can't scan for channels.

Anyway I've done a 
[B]$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ make[/B]
and
[B]$ make install
[/B]
That runs smoothly, but doesn't fix anything.
If I run this command:
[B]$sudo dmesg | grep dvb
[41.497001] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[41.497005] cx88/2: registering cx8802 driver, type: dvb access: shared
[41.649760] cx88/2: dvb_register failed (err = -22)[/B]

and I don't have a /dev/dvb directory :(

I've exhausted my knowledge and googling abilities. Any help will be greatly appreciated.

---

