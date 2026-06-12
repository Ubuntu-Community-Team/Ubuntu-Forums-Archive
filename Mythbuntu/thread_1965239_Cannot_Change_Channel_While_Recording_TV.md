---
title: "Cannot Change Channel While Recording TV"
date: 2012-04-25
forum: Mythbuntu
---

### Post by johnvic on 2012-04-25
I have Mythbuntu 11.10. I have an HD Homerun Dual, so I have two tuners. If I am recording a show I cannot watch a different channel. If I look at Backend Status I see that my first Encoder is doing the recording. My guess is that when I go to the Guide to change channels it is trying to change the first encoder.

I guess what I need is to have recordings happen on the second encoder. Does that make sense? If so, how do I do that?

Also, I noticed that each encoder is listed twice in my Backend Status. Is that a problems?

Thanks.

---

### Post by RideMan on 2012-04-25
In Watch Live TV, try hitting "y" to switch tuners. It really doesn't matter which tuner you record on; MythTV will manage that albeit at the expense of your live TV watching.

As for why each tuner shows up twice...that is probably because your tuner allows for multiple streams per channel. That is particularly useful if you have unencrypted SD digital cable and your CATV company has multiplexed channels.  On my system, for instance, I have 10 channels on Channel 10, representing SD center cut versions of all my basic cable (local) channels so I can record multiple programs at once using a single tuner. I think the default max streams for digital tuners is 2, in which case each of your HDHR tuners would show up twice.

--Dave Althoff, Jr.

---

### Post by johnvic on 2012-04-25
Cool, thanks.

---

