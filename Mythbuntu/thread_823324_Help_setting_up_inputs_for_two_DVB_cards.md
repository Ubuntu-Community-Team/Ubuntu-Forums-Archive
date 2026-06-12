---
title: "Help setting up inputs for two DVB cards"
date: 2008-06-09
forum: Mythbuntu
---

### Post by ebike on 2008-06-09
Hi All,

I have been running one Skystar 2 DVB card to watch Freeview digital TV in New Zealand for some time, but now want to add a second Skystar 2 card so I can watch and record of different multiplexers at the same time.

I will connect the two cards via a splitter (one port DC blocked) to my dish.

I have some questions on how to set up cards and input associations:

1. On my one-card setup, I tuned in channels on both Freeview multiplexes, do I on the two-card setup separate the channels for each multiplex to each card?

2. What do I do for the inputs and groups, and how do I associate them correctly. Do I attach both cards to a single "Freeview" input?

Any help appreciated. Thanks.

---

### Post by ebike on 2008-06-09
Bump!

---

### Post by ian dobson on 2008-06-10
Hi,

If both cards can "see" the same set of channels then just add you second card to the same input group as the first. MythTV will then automatically use the correct card.

I'm not sure if you can use a splitter for a Sat signal, I always thought that you needed to have one wire per receiver as the communication is actually 2 way. The reciever sends a signal back to the LNB to say wether it wants horizontal or vertical polarization.

Regards
Ian Dobson

---

### Post by ebike on 2008-06-10
Thanks for that, I will try the same input group.

In my case I can use a splitter, as all the transponders I am using are on horizontal only so the LNB is not changed during use and can stay at the same voltage.

---

### Post by ebike on 2008-06-10
Well I tried as you suggested, I made both cards see channels on both multiplexers and tied them to the same input source, however I still have the same problem.

If I am watching multiplex_A on frontend_A then I can't watch multiplex_B on frontend_B. It is like there is only one tuner. ( ... this is with multirecord=2 for each card).

However, if I set multirecord=1 for both cards, then I can watch different multiplexes on each frontened, but that is not ideal, since I can only have two frontends going at once, no more. I would really like to have multiple streams viewed and/or recorded off each multiplex as intended by Mythtv.

Can anyone help out?

---

### Post by ebike on 2008-06-12
This is such a fundamental problem with how Mythtv us "supposed" to work ..... you would think someone would have an answer ](*,) Guess I will have to join the Mythtv forum .... again.:)

---

### Post by ebike on 2008-06-14
Seems it is a problem with Mythtv ... see this thread.

--> [http://www.gossamer-threads.com/lists/mythtv/users/337494?page=unread#unread](http://www.gossamer-threads.com/lists/mythtv/users/337494?page=unread#unread)

Seems the developers see that multiple LiveTV's are not "normal" use :confused:

---

