---
title: "Reading an OpenDisc-crippled CD?"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by ljp37 on 2007-08-28
I've bought a CD which appears to have "OpenDisc" marketing software on it. 

OpenDisc's [FAQ]("http://support.opendisc.net/customer_support/faq/us/index.asp") claims that it is not a DRM system, and asserts that the CD is Blue Book-compliant.  Indeed, it plays on a normal CD player without issue.  I want to at least rip it to an ISO so I can use it with my VMWare Windows installation, but even that doesn't work...

When I insert the disc, not only will it not play, but the ATAPI CD-ROM driver has a seizure.  Commands like "fdisk" or "dd" on /dev/cdrom will hang for a few minutes, and then die mysteriously.  

dmesg shows this:

[ 2890.112000] ata1.00: qc timeout (cmd 0xa0)
[ 2890.112000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2890.112000] ata1.00: (BMDMA stat 0x25)
[ 2890.112000] ata1.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x28 data 16384 in
[ 2890.112000]          res 51/51:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2890.112000] ata1: soft resetting port
[ 2890.596000] ata1.00: configured for UDMA/25
[ 2890.596000] ata1: EH complete


Does anyone have any leads for this problem, or know of a more appropriate forum to ask this question?

I can't find any other info on OpenDisc+Linux, at least not in English.  OpenDisc seems to be more popular in France, and French forums hint at OpenDisc not working on Linux but do not have any technical details or solutions.

I'm using Feisty on a Toshiba Portege M400 laptop, have also tried and experienced the same problem on an ancient Dell laptop running the latest Xubuntu.

---

### Post by fdimmling on 2007-09-18
Same problem here. 

Friedrich

---

