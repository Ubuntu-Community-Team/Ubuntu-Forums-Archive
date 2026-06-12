---
title: "File System for Storage"
date: 2015-06-19
forum: Mythbuntu
---

### Post by elliott6 on 2015-06-19
Hi all!

Been out of the "game" for awhile, but looking to get back in. Working on my mythbuntu server, and replacing/fixing/consolidating my storage. Moving from a perc 5i to H700, and from raid5 to raid 10 (decision is based on that I have the hardware).

Question is, what should I format the new storage space with? Previously I was using XFS, and probably will keep it. But before I do, and then move all my media, just checking if it is still best. And while I have searched, a lot of the information is from 2013 or older. Wanted to see if the default EXT4 would be a better solution. Started many moons ago (it was 8.04 or earlier) and used XFS based on better deletes of larger files, and EXT4 was not around or in its infancy.

My usage is to store and record all of my media to this one server. It serves a windows/mythbuntu frontend HTPC in the main living space, as well as another mythbuntu frontend in the bedroom. I also rip my DVDs and BluRays to it, as well as music. The storage portion serves a few Windows laptops (wife and mine), two Android tablets, and two Blackberry phones with all media, as well as my main (Windows) desktop.

The server is a mythbuntu desktop - boots to SSD with the RAID array as storage (current will be RAID10 4x3TB=6TB space; will probably keep and do 3x1.5TB RAID5 as secondary). Recording is a HDHomeRun Prime through FiOS.

Is XFS still my best choice for the storage portion? Thanks!

elliott6

---

### Post by TheFu on 2015-06-19
a) RAID doesn't replace backups. RAID is *ONLY* for HA needs, not redundancy and cannot replace backups. Writing corrupted data to multiple locations concurrently is what RAID is normally used for in home installations, based on all the cries for help with RAID in these forums. Please, please, please have good backups to go along with the RAID stuff. Please.

b) XFS is a fine file system.  I'd use it over ext4 since you are already comfortable with it, but it really doesn't matter in your situation.

c) The only "better" for certain values of "better" file system might be ZFS, but it is a whole new ballgame and changing to it is NOT a light decision and you wouldn't want to use any HW-RAID with it.

The short answer is to stay with xfs.

---

### Post by elliott6 on 2015-06-19
Thanks TheFu for replying!

Noted about RAID not being for backups. Finally in a position to be able to (and working to do it efficiently) to properly back up the necessities. 

Wasn't looking for opinions (not saying that you were offering) on my choice of HW Raid. It's what I have, comfort, and using. I appreciate you replying. I was about to change the topic to File System for Storage - What is everyone using?!

I'll probably stick with XFS (unless someone compels me otherwise) as you indicate. Like I said, as I "refresh," I was just checking in, as most of my search came up with replies from 2013 and older. Haven't been active, so I was just making sure that with this refresh, I wouldn't be regretting not doing something with it.

Again, I thank you for taking the time to read and reply!!!

elliott6

---

### Post by aelfric55 on 2015-06-20
For years, from about 2009 until 2013, I used xfs exclusively for video storage on my various myth machines, while using ext4 for system or other non-videostorage drives. Since about kernel 3.2.x, I started having consistent niggling issues with xfs drives and xfs file utilities. Superblock issues, can't mount, xfs repair couldn't access the drives, etc. etc. But before giving up completely on salvaging the data in these drives, I booted the machines from bootdisks with older kernels on them --3.0.1 and 2.6.39. Older kernels simply mounted the xfs drives without incident. In a couple of cases older xfs repair tools were able to correct the issues with drives that the later versions couldn't even access. This type of behavior has repeated several times over quite a few kernel upgrades.

So I have a nagging suspicion that something is a bit amiss with xfs support in the later 3.x.x kernels and beyond. It bothers me enough that whenever I replace or upgrade a storage drive now, I make the new one ext4. 

[LIST]
[*]
[/LIST]

---

### Post by TheFu on 2015-06-20
Thanks for sharing aelfric55.

The friends running xfs all run RHEL/CentOS.  CentOS v7 has 3.10.x as the kernel and I wouldn't worry about XFS support on that version. If you only do **apt-get upgrade** (not dist-upgrade), the kernel will remain stable.

Still, I'd have to wonder what is happening with the Ubuntu XFS interaction. First-hand experience matters.

---

### Post by aelfric55 on 2015-06-20
3.10.x was a pretty good vintage, as far as I recall. All my machines nowadays are on 3.18.1, but with similarly upgraded libraries and such, this renders kernels earlier than about 3.4 unbootable for rescue discs and such.  Sync failure with a "kernel too old" error message. This means even more that good backups have to be relied on.

---

