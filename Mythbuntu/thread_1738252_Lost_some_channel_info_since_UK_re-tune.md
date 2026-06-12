---
title: "Lost some channel info since UK re-tune"
date: 2011-04-24
forum: Mythbuntu
---

### Post by BigGeoff on 2011-04-24
Hi all

Has anyone else had guide problems since the UK Freeview re-tune a couple of weeks back? I seem to have lost all guide info on Film4 and Yesterday - the guide just shows it as empty and says 'no information'. I have tried completely deleting all the channels then re-scanning but no change. The TV attached to the same aerial (literally a T off 30cm away) shows a complete guide without errors. 

Anyone have an idea what the problem is?

Geoff

---

### Post by PhilWig on 2011-04-26
Hi BigGeoff,

I've seen two DVB problems/bugs in this area.

1.   Can you 'live view' Film4 and Yesterday with Myth?  If not then you might be hitting a re-tuning bug, the details of which I think are:
If during a transmitter channel re-alignment there is a particular multiplex which has a frequency which matches one already in the database but has parameters such as QAM which change, then a Myth rescan will not write those new parameters to the database.  Result is that it cannot subsequently tune the channels on that multiplex.  Delete all channels, video sources and cards then recreate them to fix this one.  


2. In January EIT re-population took DAYS for some channels after I did a card deletion/recreation.  For those channels, it found 'now and next' and also '3 days ahead' with a big gap in between.  It had to wait for 'now and next' to roll over and fill the gap.
As you have found, my TV found the info immediately.    Others have reported this problem - I wish I knew how to fix it.

Regards
Phil

---

### Post by BigGeoff on 2011-04-26
Lo again Philwig - it's been a while. 

From what you say it looks more like the former as I cannot watch either channel in live TV either. I have tried deleting the channels but not the sources etc. and I was thinking of upgrading to 10.10 so I may just do a clean install and be done with as I have an empty watch list at the moment.

Will let you know.

Geoff

---

### Post by BigGeoff on 2011-04-30
PhilWig

Did an upgrade to 10.10 and deleted all channels, video sources and cards then recreated them as you suggested - Film4 and Yesterday OK but Beeb2 and ITV4 disappeared! I suppose you can't have everything. did a clean install of 10.10, then decided to upgrade to 11.04 (a lot sooner than I usually would) and everything is as it should be except I cannot seem to persuade it to display full size on my TV. Not terminal but irritating.

Geoff

edit 1/5/11 - sorted the screen size problem - now all working ok - thanks

---

