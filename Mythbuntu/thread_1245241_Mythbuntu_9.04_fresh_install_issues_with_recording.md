---
title: "Mythbuntu 9.04 fresh install: issues with recording playback (only)"
date: 2009-08-20
forum: Mythbuntu
---

### Post by Morgennebel on 2009-08-20
Hi,


last week I updated my MythTV box (combined front- and backend, hardware and 
software to Mythbuntu 9.04 plus all updates).

Hardware:
   - Core 2 Duo 3.00 GHz
   - 2 GB RAM
   - 160 GB SATA Intel SSD Flash disk (operating system)
   - 1.5 TByte SATA WD (recordings)
   - 2 DVB-S Cards
   - NVIDIA 8500 GT + 22" LCD

The system is fast as hell and did run for about 12-18 months errorless with Ubuntu 8.0
+ MythTV packages. 

Now, upgraded to Mythbuntu 9.04. Everything went fine, remote and ACPI wakeup works out of the box (almost).

Current status:
   - Watching LiveTV (even with Picture in Picture) works perfect
   - Watching DVDs/mkv video files from remote network share works perfect
   - System records as expected
   - Watching a sending during recording works perfect

BUT (and I do not have any clue why)
   - Watching a recording after a reboot stutters as hell.

Sympoms of the issue:
   - Harddisk LED is active without flickering for about 3-5 seconds
   - Black screen for about 10 seconds
   - 3 seconds of the recording will be shown
   - Another 5 seconds delay (froozen picture, the 5.1 amplifier looses SPDIF signal)
   - Repeat until forever

   System does not react on remote triggers. 

   When the system has stopped watching of the recording, the same recording can
   be watched smoothly out of the RAM cache without any issues.

My diagnoses:
  - First I thought about a disk performance issue
  - bonnie++ reported 80MByte/s rw performance on the 1.5 TB SATA disk
  - bonnie++ reported more than 150 MByte/s rw performance on OS SATA disk
  - Hmmm....

I tried to reduce the CPU levels in TV, Playback options (CPU- and CPU+). I tried
a different SATA port for the recording disk. I disabled realtime option.

No solution. There are no errors in mythbackend and mythfrontend logfiles.

Any help/hints would be appreciated,

Thanks, -MN

---

