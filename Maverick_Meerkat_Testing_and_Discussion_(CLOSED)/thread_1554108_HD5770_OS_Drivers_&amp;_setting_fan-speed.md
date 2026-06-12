---
title: "HD5770 OS Drivers &amp; setting fan-speed"
date: 2010-08-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2010-08-16
With the ATI catalyst drivers it is possible to set the fan speed and read the chip temperature of the gpu.

Is it possible to do this for the hd5770 using the current open source (non proprietary) drivers in maverick?

Since I'm looking to get one of these cards soon, what is the support like for the 5770 with open source drivers like in maverick?

TIA

---

### Post by Devport on 2010-08-16
Temperature sensors reading will be included in linux-2.6.36 - maverick comes with 2.6.35.

[http://www.phoronix.com/forums/showthread.php?t=23801](http://www.phoronix.com/forums/showthread.php?t=23801)

I guess we'll have to wait for the next release.

Performace of the open source drivers is not good yet - if you want fps you will want to use the binary blob drivers for now ( e.g. my old fps games et, warsow run at < 30 fps while the binary blob drivers give me > 90 fps @ radeon HD 4550, low profile - almost unplayable ).

However - personally I am very glad that open source drivers have come so far already so that games already run fine at all.

---

### Post by Col-1023 on 2010-08-17
Thanks very much Devport for your reply.

I was worried the binary blop drivers might cause problems with maverick (plymouth, etc).

I've been reading that plymouth causes problems for closed source graphics drivers, so do the ati closed source drivers work well with maverick?

---

### Post by Col-1023 on 2010-08-19
Does the ati binary blob for the hd5770 work fine (even if just in 2d) for maverick, and how about with lucid?

TIA

---

### Post by Devport on 2010-08-20
I cant comment on the binary driver on maverick since I decided to stick with open source drivers from now on.

---

### Post by rajeev1204 on 2010-08-21
> **Col-1023 said:**
> With the ATI catalyst drivers it is possible to set the fan speed and read the chip temperature of the gpu.

Is it possible to do this for the hd5770 using the current open source (non proprietary) drivers in maverick?

Since I'm looking to get one of these cards soon, what is the support like for the 5770 with open source drivers like in maverick?

TIA

m

---

### Post by Col-1023 on 2010-08-22
Rajeev, If you found my OP confusing, the machine I'm talking about currently has a hd4870, but the card is flakey, so I'm looking to swap in a hd5770.

Using karmic, the catalyst drivers that were in the karmic repos and the 4870, I can read the gpu temp and set the card fanspeed.

So I was asking whether the same applies to the hd5770 cards?

---

### Post by 0004tom on 2010-08-22
> **Col-1023 said:**
> Does the ati binary blob for the hd5770 work fine (even if just in 2d) for maverick, and how about with lucid?

I don't have the 5770 altho i have the 5450 which are the same drivers. I'm on lucid and they work well 10.7 CCC that is, 3D/2D etc etc

---

