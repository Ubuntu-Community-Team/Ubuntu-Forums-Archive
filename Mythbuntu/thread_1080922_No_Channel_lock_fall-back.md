---
title: "No Channel lock fall-back"
date: 2009-02-25
forum: Mythbuntu
---

### Post by splezunk on 2009-02-25
Hi All,

I have done some searching around the net, and am wondering if anybody here might have an answer for me.

I have 3 DVB tuners (in Australia) in my Mythbuntu box (8.10).  Unfortunately there is an issue sometimes where I cannot get a lock on a channel with certain cards.  SBS seems to be the main culprit of this.

Now, is there a way for if a recording is unable to get a lock of a channel on a card that it falls over to the next card in the chain?  At the moment I just end up with a 0 byte recording.

Yes, I know that fixing the antenna on the roof and boosters etc. will help get that lock, but unfortunately I am in a Town House complex and there is a shared antenna.  I think one of the problems is that the splitter is going sending it to 3 cards in a chain.  

Would a booster before the splitter help with digital tv or just cause more noise?  

Any help or suggestions would be appreciated.

Thanks

---

### Post by pjbgravely on 2009-02-25
A small booster might help, but might overdrive if it is too high a gain.

I believe you can set stations on tuners to a higher priority so Mythtv will go to those tuners first. This may only work while recording.

Paul

---

### Post by splezunk on 2009-02-26
> **pjbgravely said:**
> I believe you can set stations on tuners to a higher priority so Mythtv will go to those tuners first. This may only work while recording.

Thank Paul, unfortunately the problem is that a lot of the signal depends on the weather or time of day etc.  So until the actual recording time I have no idea what the card priority is.

Using the SBS as an example.  If no other cards are recording it records fine on all three cards.  However if one of the others are recording it will only use 1 particular card.  I have it set to only use that card at the moment.

This is starting to happen with one other channel now on the odd occasion. 99% of the time it records fine.  

This is why I am looking for a check at recording time with a fallback if no channel lock received.

---

### Post by lofgren on 2009-02-26
Hi,
you've probably tried, (this kinda suggests it)
"I have it set to only use that card at the moment."

But with my old cards (only 2!) that didn't like certain channels, I set the "preferred input" to the good card on my favourite shows.

Have you tried testing which card/channel combos cause issues?
Use tzap on each card at the same time?

The figures it provides aren't great, but may give you an indication of what your problem is.

Any BER (I believe this is Bit error rate) and an amplifier will probably nuke the signal, if the signal is just low, an amplifier might help.

Lofgren

---

### Post by pjbgravely on 2009-02-27
I actually need a fall back to a different channel on the same tuner, but I have not found such a thing yet. 

Can you record multiple channels at the same time? If not maybe you are loading your signal too much. If so a distribution amp should help you then, one that you can adjust would be best. If you try it put it as soon as the cable enters your place. There are ones that have a amp remote from the power so you can put the amp before it gets to you, either by sneaking or asking. Splitting 3 ways will reduce the signal to each tuner less than 1/3 of the original signal.

Paul

---

