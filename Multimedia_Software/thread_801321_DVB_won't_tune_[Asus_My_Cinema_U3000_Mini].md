---
title: "DVB won't tune [Asus My Cinema U3000 Mini]"
date: 2008-05-20
forum: Multimedia Software
---

### Post by neocookie on 2008-05-20
I've installed my Asus U3000 mini as per the linuxtv.org site, and it seems to register properly. Doing a scan for my local transmitter (Leeds, UK - uk-EmilyMoor) finds nothing. If I scan all frequencies (in Kaffeine) I occasionally get a channel or two, but they're choppy at best.

I've tried with an Hauppauge Nova-T USB2 Stick with the same results over the past year or so, in which time I've moved twice and I'm now on the top floor on a ruddy-big hill. I've also tried different antennas. No luck with anything.

Whats annoying me is that the guys on the floor below have flawless reception with their set-top box and set-top antenna (which isn't even powered)!

Is there anything I can do to increase the power/sensitivity of the device?

---

### Post by pokab on 2008-06-21
I've bought the same device, and it works _almost_ perfectly using no special software, just the 8.04 ubuntu generic kernel with the latest update (that is necessary).

While mine is working perfectly with a small antenna, when I plug it into my big antenna on the roof, neither 'kaffeine', nor 'scan' gets any signal. The latter can't even find the stations anymore. As soon as the signal strength is not maximum anymore (signal<0xffff), everything works normally. I made the signal weaker by creating a bad contact between two cables. :)

I suppose there is some interesting bug in the kernel driver or some common library, since the two programs can't both go crazy.

Any ideas, anyone? :)

---

### Post by xc3RnbFO8P on 2008-06-21
You need a amplifier (hope that is the right word over it)

---

