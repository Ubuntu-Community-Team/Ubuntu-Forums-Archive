---
title: "Electronic Program Guide Setup How To"
date: 2008-11-13
forum: Mythbuntu
---

### Post by iitywygms on 2008-11-13
I had a hard time figuring out how to set up my EPG (electronic program guide) and had a hard time finding answers in one spot, so I thought I would share what worked for me.

I have a standard frontend-backend in one box with 1 hdhomerun and 2 pvr150 cards.  Comcast cable.

1.Use mythweb to set things up.  This is a personal preference but I find it much easier to use.
2.Use a separate source for each input if possible.  I tried using one source for everything and I could never get mythtv to switch to the correct tuner if both tuners used the same xmltvid. Having separate sources solved that issue.
3.Name each channel with a different channum and callsign.  I tried using the same callsign for some channels that were the same, but mythtv would not change channels correctly.
4.Use a unique xmltvid for each channel.  I used the same xmltvid for several channels that showed the same shows, but were on different sources, and that made a big mess of things.
5.Guide channel order.  I pulled my hair out trying to get the guide to show the channels numerically, 2, 2.1, 2.1 etc.  Even if I set the front end up to show guide by number, it would still not be in the correct order.  UNTIL, I went into the backend, channel editor, and set it to show channels by number.  After I did that, the guide would work correctly.

Some things may be obvious to some people and I am sure there are other ways to accomplish what I wanted, but this route worked well for me.
If you have anything to add or see something I may have wrong please tell me.

---

