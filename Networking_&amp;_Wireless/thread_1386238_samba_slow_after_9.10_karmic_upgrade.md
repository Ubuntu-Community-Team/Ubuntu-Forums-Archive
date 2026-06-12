---
title: "samba slow after 9.10 karmic upgrade"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by acy76 on 2010-01-20
I'm running a samba server on an installation of Ubuntu Server x64, recently upgraded to 9.10.

Read/write speeds have been acceptable over gigabit LAN for the past year, about 33mb/sec writes and 55mb/sec reads. The share is stored on 4x1TB SATA disks, configured as a software RAID 5. All of this is running on an AMD Phenom 9600 quad-core at 2.3 GHz.

After a recent upgrade to 9.10, I was experiencing read/write speeds at 1/10th or less their prior speeds, on the order of 3-4 mb/sec (as measured by the Win 7 file xfer dialog box).

I was able to recover most of the performance by altering the buffer sizes in the smb.conf file (from 8192 to 262140, as discussed [[COLOR="DarkOrange"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1112320&highlight=samba+slow&page=2")).

The question is, why did it slow down after the upgrade? And why did modifying a config file that's been fine for 2+ years on two different machines change the situation?

Any ideas appreciated.

**Update:** I've found that removing all socket options from the smb.conf file has given me the best performance yet - speeds are the best I've measured on this machine. Still wondering why the upgrade necessitated this change, and whether there is more performance to be found.

---

