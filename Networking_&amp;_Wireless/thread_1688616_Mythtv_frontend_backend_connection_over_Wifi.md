---
title: "Mythtv frontend backend connection over Wifi???"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by PaulReaver on 2011-02-15
hi,  I hope someone can help with this.....

I'm trying to connect my combined mythtv frontend/backend to the frontend downstairs in the lounge... 

I can't run cat5 cable,  but the backend does have a Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) wifi card

the front end has an atheros ath5k wifi card

I have mythtv working properly on the combined frontend/backend machine, it records and I can watch TV :)
I'm having trouble with the wifi setup and firewall rules to the frontend downstairs

So far I'm not having any luck so any help or advice would be much appreciated.

---

### Post by gordintoronto on 2011-02-15
Each of the PCs normally connects to a router. Almost any 802.11g or n wireless router should work.

It might be possible to make the connection without a router, but most people don't know how to do that.

---

### Post by mr_luksom on 2011-02-16
It shouldn't be that hard to get them talking.

First, check that both machines can ping each other, and then note the backend ip and mythconverg database password. This is found in one of the last pages in Utilities > Setup > General Settings

On the frontend, put the backend ip and database password in the same location you got them from the backend.

The real problem you will have is bandwidth. I tried wireless as I too cannot route cat5/6, however it was only suitable for SD, and the wireless network could not be used for anything else, and that was 802.11n. I ended up getting power over ethernet so that I can stream HE and use the network for other things.

---

### Post by PaulReaver on 2011-02-16
> **gordintoronto said:**
> It might be possible to make the connection without a router, but most people don't know how to do that.

Any suggestions on how I would do it without a router? 

I've previously used hostapd to share my wired connection through wifi so I know my card supports master mode...
and my other card definitily does master mode too.... so I should be good....

> **mr_luksom said:**
> 
The real problem you will have is bandwidth. I tried wireless as I too cannot route cat5/6, however it was only suitable for SD, and the wireless network could not be used for anything else, and that was 802.11n. I ended up getting power over ethernet so that I can stream HE and use the network for other things.

Yeah...its only for standard definition programs...  and I only use wifi for the playstation and wii... so it taking up all the wifi is fine....

now that I'm 90% sure its possible, I'm probably going to spend quite a bit of time figuring this out....its just the actual wifi setup.... I'm quite good with mythtv.

thanks guys... :) I do a tut if I figure this one out.

---

