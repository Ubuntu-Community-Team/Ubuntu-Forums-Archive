---
title: "Simultaneous HD-PVR"
date: 2010-07-22
forum: Mythbuntu
---

### Post by uopjohnson on 2010-07-22
I have pretty decent backend hardware about 2 years old.  I'm wondering how many simultaneous HD-PVR streams I can record.  Has anyone hooked up a few of these to the same system?

---

### Post by uopjohnson on 2010-09-17
Went ahead and bought two and hooked them up to DirecTV.  Works great with no problems.

---

### Post by ian dobson on 2010-09-17
Hi,

The actual recording doesn't hit the CPU that hard if the tuner supplies a mpeg/h264 stream. Commflagging does cost some CPU, playback needs abit more CPU if you don't have VDPAU and transcoding eats all the CPU it can get.

Recording needs more I/O disk bandwidth than CPU, recording HD needs alot more than SD.

My backend (Quad Core, 8Gb ram,RAID5 array with 4 2Tb drives) can record 6 streams at the same time (3 HD, 1 SD from 2 PCI tuners and 2 SD streams from 2 settop boxes) without getting overloaded.

Regards
Ian Dobson

---

### Post by uopjohnson on 2010-09-17
Thanks, I was more concerned with overloading a USB bus or the I/O on the disks.  I ended up offloading these to a second backend anyway and my primary just manages my two HDHRs.

---

### Post by LowSky on 2010-09-17
Mr. Dobson, that is one crazy setup! I just picked up a 2TB hard drive which will double my current space, thanks for making my computer feel inadequate, LOL.

To stay on subject, and to show off a little less than Ian, I run a quad-core, 4GB of RAM, 1.8TB of HD space, not RAID'ed, with a dual tuner PCI express  tuner(HVR-2250), and a HD-PVR. I can record 3-5  shows simultaneously (multirec) and it doesn't glitch. I can even run a separate X session and watch things on Hulu with no problem too.

---

