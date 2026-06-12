---
title: "A little tuning for occasional skip playing back recordings 0.24"
date: 2011-10-27
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2011-10-27
I recently have been occasionally getting little skips/pauses when playing back recordings.

I fixed this (apparently) by setting the PCI latency for SATA and IDE to 176 from the default 32 (set by the motherboards BIOS).  Supposedly this allows fewer I/O disruptions to the large blocksize xfs filesystem.   

This link describes the what and how·to better than I can…

[http://www.mythtv.org/wiki/PCI_Latency]("http://www.mythtv.org/wiki/PCI_Latency")

Earlier I had introduced "de·fragmentation/reorganization" for my xfs disks by running a script using xfs_fsr at 2 a.m. everyday with cron.  This helped a prior similar skipping.  Here's what it does from it's little log file:```
&#8943;@&#8943;:/var/log# cat xfs_fsr.log
&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;xfs report
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda3      xfs    144G  135G  9.2G  94% /iso
/dev/sdb1      xfs    1.9T  1.5T  414G  78% /pvr
/dev/sdc1      xfs    1.9T  1.4T  512G  73% /pvs
total            -    3.8T  2.9T  935G  76%
&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;frag_report
&#8943;&#8943;xfs frag report for /iso (/dev/sda3) &#8943; Wed Oct 26 02:00:02 PDT 2011
actual 6324, ideal 6262, fragmentation factor 0.98%
&#8943;&#8943;xfs frag report for /pvr (/dev/sdb1) &#8943; Wed Oct 26 02:00:03 PDT 2011
actual 1147, ideal 1097, fragmentation factor 4.36%
&#8943;&#8943;xfs frag report for /pvs (/dev/sdc1) &#8943; Wed Oct 26 02:00:03 PDT 2011
actual 1360, ideal 1087, fragmentation factor 20.07%
&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;reorganization
&#8943;&#8943;Wed Oct 26 02:00:04 PDT 2011&#8943;&#8943;start&#8943;&#8943;xfs_fsr
&#8943;&#8943;Exit status for xfs_fsr= 0
&#8943;&#8943;Wed Oct 26 04:19:21 PDT 2011&#8943;&#8943;-end-&#8943;-xfs_fsr
&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;frag_report
&#8943;&#8943;xfs frag report for /iso (/dev/sda3) &#8943; Wed Oct 26 04:19:21 PDT 2011
actual 6324, ideal 6262, fragmentation factor 0.98%
&#8943;&#8943;xfs frag report for /pvr (/dev/sdb1) &#8943; Wed Oct 26 04:19:22 PDT 2011
actual 1147, ideal 1097, fragmentation factor 4.36%
&#8943;&#8943;xfs frag report for /pvs (/dev/sdc1) &#8943; Wed Oct 26 04:19:22 PDT 2011
actual 1119, ideal 1090, fragmentation factor 2.59%
&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;&#8943;end
```Before I started doing this, defragmentation was >80%.  Since I have added a second 2TB drive.  In this busy new season with MLB playoffs, *&c*, it been running about two hours a night.  

This summer it was running about 20 minutes a night.  The increase also my be due to the disk getting fuller, up to 76% from about 50%.  I should look into the autoexpire/delete/limit, now maxed out at 200GB.

My system combo client/server, AMD 3 CPU 3.1MHz, 2250 Hauppage 2xtuner card, 240 nvidia, 4GB memory, 2x2TB satas and a 320GB sata for system and a little extra recording storage.  I comm-flag immediately after starting a recording.

---

