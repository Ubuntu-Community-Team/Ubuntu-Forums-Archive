---
title: "conflicting recordings"
date: 2010-01-30
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-30
I would like to record 2 programs on the same day that overlap.  My recording schedule indicates that 1 of the programs is in conflict now and it won't be recorded.  In the backend I specified that it should record up to 2 shows simultaneously.  I only have 1 TV card...do I need 2 TV cards to do this?

---

### Post by ian dobson on 2010-01-31
Hi,

The multirec option (record more than 1 program at the same time) can only record multiple programs at the same time if both channels you want to record are in the same multiplex.

In the good old days of analog TV you only had one sender per channel (842MHz for example). With digital TV and data compression it's possible to squeeze several TV senders into one channel (842MHz).

So what multirec does is tune the tuner to the required channel for example 842MHz then split off the data for channel ABC and XYZ (which are both on the same channel) before writing to the harddisk. 

So to answer your question if you want to record 2 programs at the same time tha are on different multiplexes then you'll need 2 tuner cards.

Regards
Ian Dobson

---

### Post by linuxhippy on 2010-01-31
multiplex...that's new to me.  I'm not sure how many of those I have.  My cable signal is using analog, though.  Does that mean that ABC (5) and FOX (13) are on different multiplexes or the same?

---

### Post by ian dobson on 2010-01-31
Hi,

If you only have analog then you don't have any multiplexes, their only for digital channels where you can have several programs packed into the "space" used by one analog channel.

Regards
Ian Dobson

---

