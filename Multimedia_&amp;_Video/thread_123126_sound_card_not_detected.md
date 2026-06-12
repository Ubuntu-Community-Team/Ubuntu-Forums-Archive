---
title: "sound card not detected"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by kephix on 2006-01-29
I've just installed ubuntu, main problem is no sound.

Device manager lists a set of  entries "pnp device (AZT0000)" and AZT0001 0002 etc

But all the properties are "unknown"

The card is an AZTECH sound galaxy 16 (i think)

So I assume this is it, is this compatible with ubuntu, is there a driver? if so where can I get it and how do I install it.
Or can I use a different driver?

I'm completely new to Linux so am a bit lost

Thanks

---

### Post by bernardfrancois on 2006-01-29
There's a [page at the wiki](https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28sound%29) explaining more about how to setup sound cards in ubuntu that weren't automatically detected.

You'll have to find out which kernel module is able to drive your sound card. A link to a site with a list of sound cards and kernel modules is on that wiki page.
I checked it, and I saw that module **snd-azt2320** can be used for **Aztech Systems AZT2320 (and 2316)**.

I don't know if your card has the AZT2320 or AZT2316 chipset, you'll have to find that out on the site of your sound card's manufacturer.

If you have any more questions, just shoot.

---

### Post by kephix on 2006-01-30
Brilliant,
that has worked first time

thanks

:)

---

### Post by bernardfrancois on 2006-01-30
Nice to hear that :-) I didn't always have luck like that when I started using Linux...

Did a **modprobe snd-azt2320** do the trick?

---

