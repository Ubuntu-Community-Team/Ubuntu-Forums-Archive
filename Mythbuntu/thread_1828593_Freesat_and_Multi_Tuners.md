---
title: "Freesat and Multi Tuners"
date: 2011-08-19
forum: Mythbuntu
---

### Post by Billsputters on 2011-08-19
I now have a nice TBS dual card which works great and am able to tune to two Freesat multiplexes, which should stop most conflicts.

Where I am having trouble is in the tuning and channel allocation.

I do a channel scan, and it finds all that is available for one input, for which I get loads of available channels, most not wanted at all. But I also get for instance Channel 4 appearing from 9211 to 9216. Which one do I choose? What do the allocated channums mean if anything? Are they on different multiplexes, or just regional variations? Similar story with BBC 1, but these are more the regional variations. If I label all of them BBC 1, which one takes precedence? Would be nice to be able to get the local variatio, if only for South Today?

And I guess that I then have to go through and do exactly the same for the second tuner? Can I export and say to MythTV, 'Here's my channel lineup, numbers etc, just get on with it' rather than having to scan and manually edit all the unwanted ones out, grouping all the BBC's together etc.

Or has someone already done this, and can save me reinventing the wheel.

---

### Post by bance on 2011-08-19
Hi Billsputters,

I use this script, from the mythtv wiki, you can save it as a txt doc and use a text editor to alter it to suit your needs.

HTH Steve.

---

### Post by Billsputters on 2011-08-19
OK, had a hunt, don't know how I missed it. Do you mean [this one]("http://www.mythtv.org/wiki/UK_Channel_Assignments")?

From what I gather, I just let scan do their thing on both tuners, and the script then reassigns channums as required fo bot of them.

---

### Post by Neon Dusk on 2011-08-20
You should only need to scan once. You'll have one video source (e.g. Freesat) and both the input connectors assigned to that video source

---

### Post by bance on 2011-08-20
Sorry, 

Meant to link to the script, yes , if you only use freesat, then you only need the freesat section (obviously).

I don't run it as a script, (copy and paste directly into the database), I'm still finding my way in Linux  .

But I suppose I should (work smarter not harder). 

Check through the list  carefully to make sure you have all the channels you want.

I assume you know how to formulate what's given into an executable bash script, if not maybe we could work through it together.... It can't be that hard!

And as Neon Dusk says you only need to scan once for one source (freesat).

HTH Steve.

---

