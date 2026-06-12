---
title: "NFS slooooww over Gigabit Ethernet"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by sgtrock on 2009-05-18
Two 8.10 boxes, both less than 3 months old.  I'm attempting a copy of a large file (~7.5 GB) from an nfs client to a server yields very inconsistent, but very low, rates.  Typical numbers are anything from 750 KB/s to 3 MB/s.  I will occasionally see very short bursts up to 40 MB/s, but they rarely last for more than a few seconds.

scp copy between the same two servers with the same file and destination subdirectory yields sustained rates between 40 and 50 MB/s.  While not great, at least it's about half the theoretical maximum instead of an order of magnitude lower.

Within fstab, I've tried both hostname and IP address of the server, rsize and wsize from 1024-65536 in multiples of 2noatime, intr, timeo=14, with no change.  On the server side, I've tried sync, async, increasing the number of threads to 8 and to 16.  Nothing that I've tried has made a significant difference.

I've dug through posts here as well as Google.  I have found several entries that indicate that NFS should be much faster than scp or Samba.  I've also found several people complaining about similar symptoms to mine.  None of the proposed solutions have helped.

Does anyone have any thoughts on what I can try next?

TIA

---

### Post by sgtrock on 2009-05-20
bump

---

