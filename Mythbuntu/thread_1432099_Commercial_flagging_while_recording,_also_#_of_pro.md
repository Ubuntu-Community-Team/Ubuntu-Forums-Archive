---
title: "Commercial flagging while recording, also # of programs at one time"
date: 2010-03-17
forum: Mythbuntu
---

### Post by JMcFly on 2010-03-17
Running 9.04, my current backend is a 2.4ghz P4, 2gb RAM, running a Hauppage PVR-1600.  Should I be ok running commercial flagging while recording, or should I leave it to process after the show is complete?  I normally do not transcode my jobs, just leaving them in raw format as I rarely watch on a remote front-end and I'm usually the only person on the network.
 
A spare PC I can make into a new 9.10 backend is a dual-core Celeron 2.5ghz, 2gb ram and a GeForce 8400, if I add a PCIx1 recorder (Haupauge HVR-2250, for example) and the PVR-1600, would the SATA hard drive (would 1 be enough or would I need multiple just for bandwidth?) be able to keep up with 2 HD streams and two MPEG streams?

---

### Post by ian dobson on 2010-03-17
Hi,

My backend (Quad C2D 2.83GHz) can record 4 SD streams at the same time and commflag them at the same time, without putting the CPU under much load. The most important thing is having enough ram/IO bandwidth to handle the disk requests.

My backend has 8Gb ram and the recordings sit on a 4drive RAID5 array.

The only time I see the backend under any real load is when I record/commflag several HD streams at the same time.

Regards
Ian Dobson

---

### Post by matt06 on 2010-03-17
> **JMcFly said:**
> Should I be ok running commercial flagging while recording, or should I leave it to process after the show is complete?
You should be fine flagging in real-time.  I run two HVR-1600 in a 3.0GHz P4(HT) and can easily flag two analog or digital recordings simultaneously.  Flagging digital shows seems to be quite a bit more CPU intensive, especially at the beginning, but I still have no issues doing two on my box.  Just guessing here, but I think 2.4GHz could do one digital + one analog easily and two digital might be possible.

> **JMcFly said:**
> would the SATA hard drive (would 1 be enough or would I need multiple just for bandwidth?) be able to keep up with 2 HD streams and two MPEG streams?
I have a single 1TB SATA recordings drive on my backend and have done two digital (HD) and two analog recordings all simultaneously.  I think I turned off flagging on all but one show in this instance as I didn't want to chance getting a bunch of artifacts from not being able to write fast enough.  It should be noted that my OS and DB are another drive, I'm sure this might make a significant difference in results.

---

