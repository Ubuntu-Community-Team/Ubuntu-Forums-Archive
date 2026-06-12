---
title: "soundjuicer can't rip cds after gutsy upgrade; cdd2wav errors"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by hugo1967 on 2008-01-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/134640](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/134640) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				sound juicer gives awful screeching noises when playing or ripping cd's.  Grip, xmms and others can *play* cds but the files *ripped* with Grip and others give ***exactly*** the same gawdawful screeching that soundjuicer does.  The above-mentioned workaround indicates that the problem isn't a bad CD/DVD drive.

This has been reported on launchpad but has a screwy workaround (insert DVD into drive.  remove DVD, replace with desired CD.  CD now plays and rips).  I'd like a more elegant solution, please . . .

cdd2wav debugging gives both "0x4 Hardware Error" and " 0x03 (logical unit communication crc error (ultra-dma/32)) ".  I'm hoping that maybe there's some hdparm tweak or other simple fix for this? 

 Here's the cdd2wav output:

******:~$ sudo cdda2wav -D 1001,0,0 -N
Type: ROM, Vendor 'LITE-ON ' Model 'DVDRW SHM-165H6S' Revision 'HS06' MMC+CDDA
569344 bytes buffer memory requested, transfer size 131072 bytes, 4 buffers, 55 sectors
#Cdda2wav version 2.01.01a33_linux_2.6.15.7_x86_64_x86_64, real time sched., soundcard, libparanoia support
AUDIOtrack pre-emphasis  copy-permitted tracktype channels
      1- 7           no              no     audio    2
***snip****
recording 845.0266 seconds stereo with 16 bits @ 44100.0 Hz
percent_done:
  0%cdda2wav: Success. ReadCD MMC 12: scsi sendcmd: no error
CDB:  BE 04 00 00 00 37 00 00 37 10 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 129360
cmd finished after 0.047s timeout 60s
cdda2wav: Success. ReadCD MMC 12: scsi sendcmd: no error
***this pattern repeats starting with the CDB: line.

---

