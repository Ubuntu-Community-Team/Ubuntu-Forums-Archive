---
title: "Is it possible that the Intel 82865G graphics card will ever be fixed?"
date: 2011-11-12
forum: Multimedia Software
---

### Post by Roasted on 2011-11-12
At my last job, we were utilizing old HP P4 systems as thin clients with LTSP. After seeing one or two of them freeze up when trying to wake them up, we realized after some digging that the graphics card they had was problematic with Linux. An LTSP dev told me "considering it's an old card and a fix isn't here already, we might never see one."

Fast forwarding, here I have an old system I'm trying to revive. I noticed it was having issues with the screen waking up after it shut off after a certain amount of time.

So, a quick lspci later, I realized, oh boy! I have an 82865G! Imagine that?

Is there some sort of fix I never heard of? Or is one perhaps... coming? Linux makes these old machines so usable, and it's sad to think they are tarnished by this extremely common (albeit, very old) graphics card. 

:(

---

### Post by MoreOrLess on 2011-11-12
Don't hold your breath..
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

### Post by Rubi1200 on 2011-11-12
Having helped users deal with this card for both 10.04 and 10.10 and not having heard any news recently, I think it is unlikely this will be resolved in the near future.

---

### Post by Roasted on 2011-11-12
What do you guys think about it? Is this one of those super easy problems that could be fixed with the better part of a monday evening or is this something far more involved than I ever thought possible? I hate to just accept it and move on as I find this hardware very usable thanks to Linux, but at the same token I just really have no idea what I could possibly do to help in this arena. If I knew how to program drivers, it'd be a no brainer. :(

---

### Post by MoreOrLess on 2011-11-12
> What do you guys think about it?
I think you're spinning your proverbial wheels. I don't usually like to recommend throwing money/parts at a problem, but in this case, a cheap/used PCI card or even an AGP card if you have a slot for it is the easiest solution. I put a Geforce 5200 in my old i815e system and it breathed new life into it.

---

### Post by kurt18947 on 2011-11-12
> **MoreOrLess said:**
> I think you're spinning your proverbial wheels. I don't usually like to recommend throwing money/parts at a problem, but in this case, a cheap/used PCI card or even an AGP card if you have a slot for it is the easiest solution. I put a Geforce 5200 in my old i815e system and it breathed new life into it.

 That would be my thought too, I think.  Determine which slots/interfaces are available then check Ebay & other pulled/used vendors for a card you know is supported. You might be able to find something for around $20. There are a few new PCI (not PCI-E) cards available on NewEgg and Amazon.

---

### Post by Roasted on 2011-11-12
> **MoreOrLess said:**
> I think you're spinning your proverbial wheels. I don't usually like to recommend throwing money/parts at a problem, but in this case, a cheap/used PCI card or even an AGP card if you have a slot for it is the easiest solution. I put a Geforce 5200 in my old i815e system and it breathed new life into it.

I hear ya there. Good thought, but it's still frustrating. :(

---

