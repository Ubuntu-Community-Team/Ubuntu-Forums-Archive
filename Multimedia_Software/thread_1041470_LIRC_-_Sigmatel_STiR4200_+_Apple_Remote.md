---
title: "LIRC - Sigmatel STiR4200 + Apple Remote"
date: 2009-01-16
forum: Multimedia Software
---

### Post by SnakeArtworX on 2009-01-16
Hi!

I have a SigmaTel stir4200 usb dongle which works great with my Siemens M65 (with Obex and SiMoCo under Wine). I've ordered an Apple Remote and I'm wondering is it possible to use this remote with mentioned IrDA dongle and LiRC? If not, what is the best and easy way to get an IR control in Totem, Rhythmbox, F-Spot and OpenOffice Impress?

---

### Post by DREMA on 2009-08-11
Any solution on this?

---

### Post by tuxonapogostick on 2012-04-06
any solution? I am trying to figure this out for a universal remote, and have had no luck so far.

---

### Post by Shplad on 2012-05-19
Tuxonapogostick:

I don't know exactly what OP SnakeArtworX was using on his Siemens M65,
but If you Google STiR4200, you get this:
[http://scratchpad.wikia.com/wiki/Uwatec_Smart_Protocol](http://scratchpad.wikia.com/wiki/Uwatec_Smart_Protocol)
which suggests to me that the STiR4200 is an IRDA device.

The LIRC FAQ page states that LIRC doesn't support IRDA USB dongles (receivers).
Then again, that FAQ was written in 2009, and it's...well...not 2009 any more.
AFAICT, this is still true. If this is true, it  might be time to buy another receiver.
I chose a Manta TR1 and I'm very happy with it and the support I got.

IrDA devices are really more designed for transferring somewhat larger amounts
of data (e.g. syncing with your phone), whereas LIRC is more for remote control.

Shplad

---

