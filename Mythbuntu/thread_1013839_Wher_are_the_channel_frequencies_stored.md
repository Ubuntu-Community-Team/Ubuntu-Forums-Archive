---
title: "Wher are the channel frequencies stored?"
date: 2008-12-17
forum: Mythbuntu
---

### Post by My Name on 2008-12-17
I have done the initial scan and myth has found all the available channels.
The problem is that the frontend won't tune in to any channels it has listed.
Looking at the channel list in mythweb, there is nothing in the freqid column. Any idea where I can find these frequencies and add them in?

---

### Post by uncle hammy on 2008-12-17
If you go into the backend setup, go to the channel editor, select a channel in the list, you can edit it's details there.

---

### Post by ian dobson on 2008-12-17
Hi,

The channel frequency is stored in the channels table in the mythtv database under freqid.

Regards
Ian Dobson

---

### Post by uMuppet on 2008-12-17
> **ian dobson said:**
> Hi,

The channel frequency is stored in the channels table in the mythtv database under freqid.

Regards
Ian Dobson

Unless you mean digital channels, they dont store the frequencies in the channel table, they tune in each time you change to them using some other data stored in other tables.

---

### Post by My Name on 2008-12-18
I do mean digital freeview stations.
I think my problem is something else though which i'm dealing with in another thread.
Thanks for the replies

---

