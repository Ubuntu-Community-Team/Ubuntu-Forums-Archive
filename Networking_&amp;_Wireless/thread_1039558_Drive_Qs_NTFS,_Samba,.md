---
title: "Drive Qs: NTFS, Samba,"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by cbonilla on 2009-01-14
OK, so I’ve learned just enough Linux to be dangerous. Now that I’ve had it up and running for a while I have a few questions.

I have set up a gigabit home network, bunch of windows boxes (XP, Vista) and one Linux box (Dell PoweEdge 2650) running Heron server. The PowerEdge is used as the central repository for pictures, music, shared files, etc.

The PowerEdge has two disk systems.  A pair of small SCSI drives where Linux is mounted with RAID1 set up in hardware by the built in Adaptec controller and two 750G Esata drives connected to a Silicon Image controller set up as a RAID1 configuration. Since the SI card is fake raid the RAID was set up using MDADM. Drives are formatted as LINUX drives (I think the file system was ext3). Windows boxes see the Esata drives via Samba. All works fine, all the machines on the network have access to the Esata drives.

And finally my question. Samba seems to impose some performance penalties. It occurs to me that if a performance penalty was to be imposed it should be at the Server end, since it is Windows boxes that actually do any reading or writing to the drives. 

One of my Esata drives has failed and I’m waiting for an in-warranty replacement. This means that I will be playing with the setup. Will I see better performance formatting the drives directly under NTFS so that the windows boxes can write directly to those drives? How would the Linux box see the drives? Is that where ntfs-3g comes in? Would mdadm still be able to configure two ntfs drives as a RAID1? Or would any of this make any difference? Advice and counsel much appreciated.

Thanks, Carlos

---

