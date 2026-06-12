---
title: "ati fglrx made for FireGL?"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by WalmartSniperLX on 2007-03-19
I was looking at my fglrx control panel and it says "firegl" repetitavely in the background and I also read up rumors that fgl in 'fglrx' stands for firegl. Is this true? Were the ati proprietary drivers aimed towared the FireGL cards but had to revert to radeon support to compete with Nvidia's Unified Driver Architecture? (if fgl stands for firegl, what does rx stand for?)

---

### Post by AirRaven on 2007-03-19
> **WalmartSniperLX said:**
> I was looking at my fglrx control panel and it says "firegl" repetitavely in the background and I also read up rumors that fgl in 'fglrx' stands for firegl. Is this true? Were the ati proprietary drivers aimed towared the FireGL cards but had to revert to radeon support to compete with Nvidia's Unified Driver Architecture? (if fgl stands for firegl, what does rx stand for?)

The FireGL range are, for all intents ad purposes, Radeon cards. There's very little difference between them.

I'd assume that you're right- the FireGL cards are mainly aimed at non-game rendering- which means OpenGL support. Radeon Drivers' GL support is notoriously bad- it'd make sense for them to use modified FGL drivers on Linux.

---

### Post by mcduck on 2007-03-19
Ati's linux drivers are based on FireGL drivers, as they are made to use OpenGL in the first place, while normal windows drivers are more optimized for Direct3D. (you can actually run FireGL drivers in windows with many Radeon cards to get better OpenGL performance)

---

### Post by WalmartSniperLX on 2007-03-19
> **mcduck said:**
> Ati's linux drivers are based on FireGL drivers, as they are made to use OpenGL in the first place, while normal windows drivers are more optimized for Direct3D. (you can actually run FireGL drivers in windows with many Radeon cards to get better OpenGL performance)

> The FireGL range are, for all intents ad purposes, Radeon cards. There's very little difference between them.

I'd assume that you're right- the FireGL cards are mainly aimed at non-game rendering- which means OpenGL support. Radeon Drivers' GL support is notoriously bad- it'd make sense for them to use modified FGL drivers on Linux. 

Thanks. Well that just gave me an idea for windows ;)

---

### Post by mcduck on 2007-03-19
> **WalmartSniperLX said:**
> Thanks. Well that just gave me an idea for windows ;)

No problem. :) (By the way, using FireGL drivers in Windows means that your Direct3D support will be very poor, and most Windows games use that.. I believe the unofficial Omega drivers have copied some parts of FireGL drivers to get best of both worlds..)

---

