---
title: "Two Harddrive Partitioning"
date: 2009-12-09
forum: Mythbuntu
---

### Post by WVUSax on 2009-12-09
I am building a new Myth system and migrating from a Gentoo base to a Mythbuntu base.  I have two harddrive, HD1 is 500gb which is where I'd like to store OS, swap, and general storage for my music, pictures, and files. The second HD is 1000gb and is where I would like only myth recordings to go to.

Reading on the forums the suggestion seems to be for HD1 having a /, a swap, and a /home partition. Could I not just have a swap and a combining /home into / so I don't have to worry about either / or /home being filled up?

---

### Post by ubnewbie2 on 2009-12-11
> **WVUSax said:**
> I am building a new Myth system and migrating from a Gentoo base to a Mythbuntu base.  I have two harddrive, HD1 is 500gb which is where I'd like to store OS, swap, and general storage for my music, pictures, and files. The second HD is 1000gb and is where I would like only myth recordings to go to.

Reading on the forums the suggestion seems to be for HD1 having a /, a swap, and a /home partition. Could I not just have a swap and a combining /home into / so I don't have to worry about either / or /home being filled up?


Actually putting the /home onto the / partition increases your chances of user files filling up / and creaming your machine.  The idea is to isolate the root partition from places that commmonly hold lots of changing files, and users' files all go in /home.  That said, it's not as important on a server machine like a mythbackend.

---

### Post by SiHa on 2009-12-11
> **ubnewbie2 said:**
>  That said, it's not as important on a server machine like a mythbackend.

Agreed, It's probably more important to ensure that /var is on a different partition/drive, or at least /var/lib/mythtv

I installed Mythbuntu 9.10 using the new default of a single partition (plus swap, I suppose, but that's not mentioned at install). Then I added my main storage drive on a mount point of /var/lib/mythtv.

---

