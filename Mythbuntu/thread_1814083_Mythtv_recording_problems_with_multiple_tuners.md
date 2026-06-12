---
title: "Mythtv recording problems with multiple tuners"
date: 2011-07-28
forum: Mythbuntu
---

### Post by mikeyandmary on 2011-07-28
Hi all,

I have a mythtv system with 5 tuners (3 single tuners and 1 dual tuner - all USB). When one tuner (any tuner) is recording it records perfectly. If I record with more than one tuner at once, the recordings become broken up and pixelated. The more tuners that are operating at one time, the greater the chance / severity of poor recording quality.

I have no signal problems with any of the individual tuners and the playback problems are the same on the frontend and when I connect a monitor to the backend. I think it might be either related to too many USB devices operating at once or too much data going to the drives at once. Any ideas on how to find and solve the problem would be greatly appreciated...

Thanks...
Michael

My mythtv setup is as follows...
Backend - Core2Quad Q6600 2.6GHz 4gig RAM 320TB HDD (boot and file storage), 2x1.5TB HDD (1 recordings, 1 videos and other media), 2x2TB HDD (2 recordings drives) - ALL SATA II Drives. Storage Groups is set to share files between the recording groups according to "Balanced Disk I/O".

Frontend - Intel Atom D525 NVIDIA ION GT218 2gig RAM. The frontend has performed perfectly.

---

### Post by ian dobson on 2011-07-29
Hi,

Sounds like you exceeding the bandwidth of your USB. Although you have multiple external USB ports on the motherboard internally they are attached to multiple USB hubs that share a single USB port on the chipset.

Here's a lspci from my system (Asus p8p67) it has 8? usb ports but 4 internal hubs (bus)
```

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0b05:179c ASUSTek Computer, Inc.
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The only thing you can try is to attach your tuners so that each one is on their own hub (not sharing bandwidth).

Attach the output from lsusb und lspci from you box.

Regards
Ian Dobson

---

### Post by mikeyandmary on 2011-07-29
Thanks heaps for the help Ian. I looked at lsusb and 4 of the tuners were connected to the same bus. There seems to be 2 USB2 buses on my computer so I now have 2 tuners on one and 3 (a single and the dual) on the other. So far, no poor recordings. 

Hope it's all good now...
Michael

---

### Post by ian dobson on 2011-07-29
Hi,

Are you sure you have only 2 usb hubs. What does lspci show?

But if the poblem is solved, then maybe leave it solved :)

Regards
Ian Dobson

---

