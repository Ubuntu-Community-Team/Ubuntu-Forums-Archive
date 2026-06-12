---
title: "Lenovo E530 with Intel Centrino or Broadcom?"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by Dr. McKay on 2013-03-02
I will be ordering a Lenovo E530 in the next coming days but I have a question about Broadcom wifi chips.
Some batches of the E530 come with Intel Centrino chips, others with Broadcom wifi. I know Intel Centrino poses no problems with Linux, but Broadcom can be hit and miss. As there is no way that the shop I'm buying from can guarantee that my E530 will come with Intel Centrino technology (since that's the manufacturers prerogative), I'm afraid I might get a model with Broadcom chips.
So, in the case that should happen, can I expect lots of problems in linux or maybe even forget Linux altogether ?

---

### Post by EnesTesla on 2013-03-02
Broadcom, Intel sucks in everything except Processors :)

---

### Post by chili555 on 2013-03-02
> **EnesTesla said:**
> Broadcom, Intel sucks in everything except Processors :)Absolutely not.

---

### Post by Dr. McKay on 2013-03-04
As far as I understand, Centrino works out of the box with Linux but you have to install drivers for Broadcom (which means no wifi when using Live CD or USB on broadcom...).

---

### Post by drchrist68 on 2013-03-04
Oddly enough, my Broadcom BCM4312 LP-PHY was detected during install with 12.04.2 (but not 12.10, which is another story...). It worked, but not great, and after much research discovered the latest b43 (lpphy) which so far is the least of several evils. All of the drivers, proprietary or OSS, seem to give issues, but at least the wireless stays connected... At any rate, I've never had an Intel chip let me down. Full support out of the box, no dickering around with modules, they just work. Atheros has been OK too, but maybe I've been lucky.

I've had bigger issues than the Broadcom though, most notably the stupid dnsmasq and avahi implementations that break DNS, but that's fodder for another thread...

---

