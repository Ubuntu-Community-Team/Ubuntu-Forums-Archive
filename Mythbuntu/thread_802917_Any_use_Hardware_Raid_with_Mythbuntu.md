---
title: "Any use Hardware Raid with Mythbuntu?"
date: 2008-05-21
forum: Mythbuntu
---

### Post by jaakan on 2008-05-21
I'm planning a Multi-HD/QAM tuner based HTPC: Q6600 Quad core, 2Gb of ram, NV GF7 or GF8, Firewire, Digital audio out. By the time this is built I might have Comcast Digital Cable or Verizon FIOS TV.

I'm debating on to get 2x 500GB SATA drives for RAID 1 or 4 x 200GB RAID 5 or 4 x 250GB RAID 10.

What are the performance hits like on each, say with recording 2 shows and  playing a recording?

---

### Post by mrand on 2008-05-21
> **jaakan said:**
> I'm planning a Multi-HD/QAM tuner based HTPC: Q6600 Quad core, 2Gb of ram, NV GF7 or GF8, Firewire, Digital audio out. By the time this is built I might have Comcast Digital Cable or Verizon FIOS TV.

I'm debating on to get 2x 500GB SATA drives for RAID 1 or 4 x 200GB RAID 5 or 4 x 250GB RAID 10.

What are the performance hits like on each, say with recording 2 shows and  playing a recording?Howdy jaakan,
I can't completely answer your question based upon personal experience (I currently have a RAID 1 setup with 2x750 GB SATA, but only one analog tuner), but I have done a fair amount of reading on the topic.  You didn't mention if you were planning on using Linux-based RAID, motherboard chipset-based RAID, or a dedicated RAID controller.  There is no questioning performance of a dedicated RAID controller - it should be able to handle anything you can imagine.  My reading about motherboard (chipset-based) RAID is that it doesn't gain you measurable performance (and sometimes even hurts performance) over Linux-level RAID, and has a downside: it ties you to that brand of chipset until you're ready to reformat.  But back to your direct question.  The short answer is that with SATA drives, you are going to have a very hard time coming up with enough data to cause them any trouble, even if they are in a RAID.  Take ATSC at ~20 Mbit/s and double it for a safety factor (or for a Blu-ray level bitrate).  Now double it again for two tuners.  You're at 80 Mbit/s, or 8 MBytes/s.  This is well less than 1/5 the capability of a SATA drive.

Now, for some stuff you didn't ask for: The pricing sweet spot on drives is currently migrating from 500 GB to 640 and/or 750 GB ($100 to $120).  I personally wouldn't buy anything smaller than 500 GB for power, space, and cost reasons.  If you buy a 250 GB now and then in a year buy a 500 GB to replace it, you'll probably spend as much on those two drives combined as you would if you just bought the 500 GB right now.  I'd rather go with the larger drive and not have to deal with migrating in the future.

Sorry for the rambling!

[INDENT]Marc[/INDENT]

---

### Post by ian dobson on 2008-05-22
Hi,

I have Q6600,3Gb ram, 4x500Gb WD SATA drives in a RAID5 array using mdadm (SW Raid). From my tests I can record 2 channels from my DVB-C card (Both SD), 1 channel from my PVR-150 and watch a different program all at the same time and don't see any I/O problems.

Note my Frontend is running on a different box, connected the backend over a 1Gb lan.

I had a look at using a hardware raid controller but the price/performance ratio just didn't add up. It was cheaper to buy a quicker CPU/more ram than a HW raid controller for almost the same performance.

Regards
Ian Dobson

---

