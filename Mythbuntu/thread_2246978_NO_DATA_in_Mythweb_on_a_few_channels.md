---
title: "NO DATA in Mythweb on a few channels"
date: 2014-10-04
forum: Mythbuntu
---

### Post by jim74 on 2014-10-04
Hello, I have been trying to sort out a "NO Data" problem I have. I have channels in Mythweb that show "NO Data" but looking on the FE i see the data is there.

My setup: 
1 DVB-T Card (two tuners)
1 DVB-S Card
1 Mythbackend
2 Frontends

I have the 3 cards setup, with 2 sources Freeview & Freesat, and point them at the correct cards.
I have completed a channel scan on both cards and have all the channels.
I have them ran organised my channels in a similar manner to this - [http://www.mythtv.org/wiki/UK_Channel_Assignments](http://www.mythtv.org/wiki/UK_Channel_Assignments)

I have investigated my problem and found the following.

ITV1 Channel - 

No EIT Data Shown in Mythweb, But full EIT shown in FE schedule

Looking at the mysql - I have two chanids "13110" on source 1, and 2003 on source 2.
Looking at the program data on each channel, 13110 has no EIT data and 2003 has the next 7 days.

It looks like mythweb is finding the program list from the first channelid, but the fe is doing something else.

Any ideas?

---

