---
title: "Intermitent crash using Huawei E620 USB Modem on Jaunty (NBR) on Eee PC 901"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by regstraton on 2009-12-11
Hi, a question about a suitable diagnostic approach:

I am running Jaunty NBR on a Eee PC 901, which mostly works great. However there is one rather nasty crash I sometimes get which relates to when I am using my Huawei E620 USB (GSM/HSDPA) Modem. The crash is intermittent and I've hardly ever had it whilst sitting in one place. But its frequency is significantly increased when I am travelling on a train and network coverage is changing and coming and going.

The effect is a very sudden and completely grey screen with a few horizontal flickery lines and the speakers spitting at me. The machine becomes unresponsive in any way apart from the POWER-OFF button.

(And publicly embarrassing for Ubuntu - remember I'm mostly on the train when it happens - and this is NOT a good thing coz Ubuntu is mostly totally G.R.eat, and I am an almost evangelical supporter of Ubuntu these days. So thus we need to find this glitch and get it sorted.)

What approach should I use to diagnose the root cause?

---

### Post by regstraton on 2010-02-08
:KS Eurika!! :KS

Finally, I believe I have discovered the cause of the crash, though it wasn't for any of the looking I did.

After a bit of testing I now believe that the crash is as a result of Electro-Magnetic Interference from the USB HSDPA dongle. (Though the trouble with an intermittent bug is you sometimes can't be totally sure.) 

Simply adding a ~70cm USB extender cable to put a little distance between the dongle and my Eee PC 901 does the trick - no more crashes. And it is possibly better for my health too.

:D

---

