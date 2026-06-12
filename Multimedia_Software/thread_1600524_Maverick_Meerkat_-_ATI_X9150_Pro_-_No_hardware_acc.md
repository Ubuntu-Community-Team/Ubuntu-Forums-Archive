---
title: "Maverick Meerkat - ATI X9150 Pro - No hardware acceleration and page tearing"
date: 2010-10-19
forum: Multimedia Software
---

### Post by tedrogers on 2010-10-19
Hi,

Running Meerkat 10.10 with an ATI X1950 PRO, and with no visual enhancements I get page tearing on minimising windows and things like that.

If I turn on even basic visual effects, then Maverick slows down and becomes quite unresponsive. There are noticeably long delays between closing windows or clicking on a menu etc.

Is this because the open source ATI driver does not support hardware acceleration on my X1950 yet?

Is there any hope for me? Recent versions of Ubuntu seems to have taken a step back in that respect. I remember 8.04 worked really well!

Thanks.

---

### Post by beerbelly on 2010-10-19
Quite similar problem over here... running a ATI Mobility Radeon 5000 series and the ATI/AMD proprietary FGLRX graphics driver.

Ran fine, even with all effects on, but after installing Meerkat it seems as if my color depth goes down dramatically all of a sudden. No idea where to check to be sure, but graphics on screen indicate nowhere near the color depth I was used to.

Graphics driver is active and in use and the ATI Catalyst Control Center doesn't warn about anything. Saw something in the [Knows Issues section]("https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Graphics%20and%20Display") for Meerkat, not sure if that applies.

Anyway, as we are dealing with proprietary drivers, there probably isn't much the folks at Ubuntu/Canonical can do. Just sit and wait for some kind person to fix this, I guess...

---

### Post by tedrogers on 2010-10-19
I think you're having problems because the X.org version of Meerkat has incremented to 7.5, and this isn't supported by your ATI drivers and Catalyst Control Centre panel.

You'd have to double check the version, but I'm pretty sure CCC and ATI drivers only support up to 7.4 of X.org.

So, we sit and wait...

---

### Post by Mark Phelps on 2010-10-19
Well ... I'm running an ATI X1650 on one machine, have the default open-source driver installed, have it set to full video effects ... and have no problems at all.

DVDs, Videos, YouTube ... all display fine with no tearing, no lag, no other artifacts.

As to hardware acceleration, the open-source drivers are known not to have much, at least, as the proprietary drivers did, but they haven't been supported for our cards since Ubuntu 8.10.

---

### Post by tedrogers on 2010-10-20
> **Mark Phelps said:**
> Well ... I'm running an ATI X1650 on one machine, have the default open-source driver installed, have it set to full video effects ... and have no problems at all.

DVDs, Videos, YouTube ... all display fine with no tearing, no lag, no other artifacts.

As to hardware acceleration, the open-source drivers are known not to have much, at least, as the proprietary drivers did, but they haven't been supported for our cards since Ubuntu 8.10.

Yours would be an RV530/RV560 based card, whereas the X1950 is is an RV570/R580 based card...this may be the reason why you have no problems with the default open-source drivers and full visual enhancements. Perhaps the RV530/RV560 cards are better supported at present than the RV570/R580 cards?

---

### Post by Mark Phelps on 2010-10-20
> **tedrogers said:**
> Perhaps the RV530/RV560 cards are better supported at present than the RV570/R580 cards?
I though all the R5xx cards had the same support under the old legacy drivers; guess I was wrong if my card works and your doesn't.

You can check over at the Phoronix forums.  They do a lot of detailed testing with the legacy drivers.

---

### Post by tedrogers on 2010-10-20
Any ideas what I should be looking for at that website you suggsted?

I'm reaching the limit of my understanding as regards some of this.

---

