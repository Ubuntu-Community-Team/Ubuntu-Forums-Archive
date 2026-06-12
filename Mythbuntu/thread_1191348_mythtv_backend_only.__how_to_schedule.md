---
title: "mythtv backend only.  how to schedule?"
date: 2009-06-18
forum: Mythbuntu
---

### Post by Big_Z on 2009-06-18
I've struggle to get smooth, crash free playback on Mythbuntu for serveral months now and have been foiled.  The backend has proven to be rock solid and all the recording and comskip and other features have worked flawlessly.  My problems are with playback and frontend crashing.  

So i'm thinking about moving the PC out of my home theater and using only the backend for recording adn processing.    I'm thinking of using a network media tank (NMT) for playback of files.  Popcorn Hour is a popular NMT but there are many varietes out there.  They are specialized boxes that can play most any media file across your network and support up to 1080p without breaking a sweat.

before I go down this road my question is how would I set up scheduling on the backend?  does mythtV have any sort of remote scheduling interface?  I'm thinking something like a webpage I could go to to set recordings?  Any advice?  what other issues am I overlooking?


Thanks,
Z

---

### Post by AboveTheLogic on 2009-06-18
mythweb plugin:

[http://www.mythtv.org/wiki/Mythweb](http://www.mythtv.org/wiki/Mythweb)

I have 3 frontends, but I only really schedule recordings with mythweb

---

### Post by Big_Z on 2009-06-18
awesome!   i knew there was something out there but i looked right past that.   Thanks.

---

### Post by Big_Z on 2009-06-18
next question.  

can a AMD x2 5000+ system w/ 4gb RAM record 4 HD shows at once?  will the harddrive be the bottleneck?  SATA drive?   I have had no problems with 2 at a time.  thinking of adding a 2nd HDHomerun for extra coverage.

Z

---

### Post by buntunub on 2009-06-18
Mythweb comes standard with every Mythbuntu install. Just point your browser at it (localhost/mythweb) or (IP/mythweb). 

As far as how many jobs a backend can simultaneously handle, the Mythbuntu docs say that 2 is the recommended. For more powerful machines, 3 or more may work, but the strain on your machine will be rough with multiple instances running, transcoding, etc.

---

### Post by ian dobson on 2009-06-18
Hi,

My 3 x WD 2Tb disks in a RAID5 array can handle recording recording 4 HD streams and commflagging 3 at the same time but the I/O system starts lagging badly. Copying files, opening programs at the same time takes forever.

I don't think a single disk could handle 4 HD streams. The problem is not the bandwidth it's more the seeking all the time.

Regards
Ian Dobson

---

### Post by Big_Z on 2009-06-20
I agree.  I may switch to a raid.  Can you give me your hardware specs?  My motherboard (Asus M3N78-EM) has "onboard sata RAID through nvidia chipset.  will that work in linux?  I've done some googling but can't find a definite answer?  I found some references to "fakeraid" or software raid.   I know RAID would give me a speed increase and also a bit of redundancy in case of drive failure.





> **ian dobson said:**
> Hi,

My 3 x WD 2Tb disks in a RAID5 array can handle recording recording 4 HD streams and commflagging 3 at the same time but the I/O system starts lagging badly. Copying files, opening programs at the same time takes forever.

I don't think a single disk could handle 4 HD streams. The problem is not the bandwidth it's more the seeking all the time.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-06-21
> **Big_Z said:**
> I agree.  I may switch to a raid.  Can you give me your hardware specs? 

Asus P45 chipset motherboard (6 SATA ports)
Q9550 Quad Core CPU (I use the box mainly for heavy duty processing work)
8Gb DDR2 PC800 ram
4 WD 2Tb Drives (3 in a RAID5 Array using mdadm, 1 as a Backup)
1 WD 1Tb drive as transfer/hot swap.
2 DVB-c tuner cards
1 PVR-500 dual analog tuner

The 3 RAID drives are partitioned into 2 partitions, 1 small (20Gb) boot partition and the rest for data. The Boot partition is setup a a RAID1 (mirror) and the data partition is setup as a RAID5. Both partions are formated ext3. 

Note the ext3 data partition is setup with full journal mode, it's abit slower than ordered or writeback but it's the safest and my data is very valuable to me.

Regards
Ian Dobson

---

