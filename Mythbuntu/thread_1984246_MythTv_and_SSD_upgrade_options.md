---
title: "MythTv and SSD upgrade options"
date: 2012-05-21
forum: Mythbuntu
---

### Post by Ubu_Fester on 2012-05-21
I'm just starting investigating solid state drives.  It's probably a no-brainer for an HTPC box, no?  

What are the pros/cons for this this drive for an HTPC application?

I currently have two hard drives taking up my two HD bays.  Can the SSD be installed in my second CD drive bay? 

What size would I need?  I'm presume I just need to cover my OS (mythbuntu), and partition my usr home to an internal HD.  Budget is tight at the moment.

Thanks in advance!

---

### Post by nickrout on 2012-05-21
40G is sufficient for /

mount the other drives under /mnt and point mythtv to put the recordings and videos on those drives via storage groups setup.

---

### Post by Ubu_Fester on 2012-05-21
cool.  Thanks!

---

### Post by ian dobson on 2012-05-22
Hi,

I'm using a 40Gb (34Gb usable) on my frontend. Mythbuntu doesn't actually need much space.

As I had a working system, I just dd'd the origional harddisk onto the ssd, booted from the ssd and did a manual trim, and it's been running since then.

Regards
Ian Dobson

---

### Post by matt06 on 2012-05-23
I'm using a 40GB OCZ Vertex 2 for the OS on my backend (10.04 and 0.23-fixes).  Previously I had a 80GB IDE drive and all aspects vastly improved after moving to the SSD.  Scheduling, remote frontends, MythWeb are all very quick in responding now.

---

### Post by crbnrod on 2012-05-27
After trying an SSD on a new FE a few mos ago, I don't think I'll ever build a new computer again w/out putting the OS on an SSD (well, until that tech is also outdated, heh). Pretty fantastic, although since you asked I guess the cons would be you don't get much space for your dollar compared to a slow, noisy, hot regular HD.

---

