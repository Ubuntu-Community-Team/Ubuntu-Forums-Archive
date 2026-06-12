---
title: "Help with a partitioning scheme."
date: 2009-02-17
forum: Mythbuntu
---

### Post by jmail524 on 2009-02-17
Hi everyone,

I am running Mythbuntu 8.10 on a RAID5 system. My current setup is as follows:
Partition 1: 15GB - System
Partition 2: 350GB - TV Recordings
Partition 3: 1.2TB - Video, Music and Photos
Partition 4: 500GB - Network shared drive for RAID storage of important files from my desktop and laptop.

This setup works fairly well, but the partition sizes are permanently set and I cannot change them as my needs change.  For instance, I have found that 350GB for TV recordings is a little low for all of the HD content I'm recording.  I would like to be able to alter the sizes as needed.

I don't have a problem running 1 huge partition.  The Videos, Music, Pictures and network share sizes don't really concern me, I arbitrarily picked 500GB for network share and left the rest for Videos, etc...  However, I wish to limit the amount of TV recordings to "x" number of hours.  The only way I saw to do this was to create a separate partition with a set capacity.

My "long-winded" question is:  Is it possible to set a recording limit in MythTV or should I use LVM to create a dynamic disk system that I can resize partitions and needed. (or any other way to do this.)

Thanks for your patience in reading my post.
Brian

---

