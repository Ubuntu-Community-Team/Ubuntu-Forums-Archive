---
title: "MythTV, ZFS, FreeNAS and NFS anyone?"
date: 2014-10-26
forum: Mythbuntu
---

### Post by mattlach on 2014-10-26
Hey all,

Has anyone had success with this?

I know the MythTV guide says there is no need for any fancy RAID setups, and just to use individual disks, but I already have a 32TB FreeNAS box, and would rather leverage the free space I have on that box, than buy a bunch of individual disks just for MythTV.

My problem is, no matter what I do, LiveTV freezes randomly when the LiveTV storage group is on my NFS share.

I have read the [MythTV NFS Server Guide](https://www.mythtv.org/wiki/Optimizing_Performance#NFS_servers), but its suggestions haven't helped much.  I've tried pretty much every combination of mount options, wsize, rsize, tcp, udp, nfsvers=3, etc. etc. with no success.   I have also tried both a dual Intel Gigabit adapter in LACP mode, as well as a 10gig ethernet adapter.  Both result in the same LiveTV freezes.

I don't think my storage pool in and of itself is the issue.  It is very fast with 12 drives configured in two 6 drive RAIDz2  (ZFS RAID6 equivalent) arrays striped together to one large pool (much like RAID60).  The storage box has 72GB of RAM for plenty of caching, and has two striped 128GB SSD's for read cache (L2ARC).   When MythTV is recording to the storage box, disk activity is very very light, so it can't be that the drives can't keep up.

When I have benchmarked it (making sure to first disable lz4 compression) I achieved 975MB/s reads and 675MB/s writes, with large enough 500GB tests, to make sure I wasn't just measuring cache speed.

Everything else connected to the FreeNAS box performs very well, which leads me to believe there is something specific about MythTV and how it interacts with NFS.

Has anyone else tried using your storage groups on NFS mounted remote storage (in general), ZFS storage (more specifically) or FreeNAS (very specific)?  What were your results?  Did you have the same problems?  How did you solve them?

I have temporarily installed an old 1.5TB WD Green drive I had kicking around, dedicated for LiveTV and everything works well.   Recordings are still going directly over NFS, and they seem to be working, but they appear to be a bit skippy when watching in-process recordings.

In the past, when I had a slower storage solution, I figured the fact that it was slower was the problem, and temporarily until I upgraded my storage I set it up so that all my liveTV and recordings went to a small local 60GB SSD, and I had a cron job set up, to periodically monitor free space on the SSD and move all the content that hadnt been written to in over 2 hours to the NFS storage.

This worked, but over time my database degraded.   I know the server searches for missing recordings in other identified storage groups, and this did work on th emoved files, but I think the fact that I was moving SO MANY files, just resulted in a seriously degraded database.

I just did a fresh re-install, starting afresh with a clean database, and utilizing my new faster storage, and I really want to get this working right, not with cronjob file moving hacks.

Does anyone have any suggestions?  Does MythTV just not play nice with NFS?   Would going with SMB be a better choice?

I'd appreciate any thoughts or recommendations!

Thanks,
Matt

---

### Post by khPWXxF on 2014-10-28
SD recording are in the 4 to 10 Mbit/sec range so your kit sounds like overkill for them.  
Operating system and database rates will be very much higher.  Are they on local storage?

Phil

---

### Post by jensk on 2014-10-29
I have a setup where my Mythtv backend are using storage on my Openmediavault NAS. It has been working for several years without a glitch.

My backend is accessing the nas via NFS shares mounted in the backend servers /etc/fstab like this:> xxx.xxx.xxx.xxx:/mythtv /var/lib/external/mythtv nfs4 hard,noatime,auto,_netdev,bg,timeo=60,retrans=6,retry=6,intr,tcp


My OMV nas is exporting the shares with these parameters > async,no_subtree_check,insecure,all_squash,anonuid=1006,anongid=100
Where uid 1006 is the "mythtv" user on the nas and the 100 gid is the group "users"

In the backend the uid of the mythtv users is also set to have uid 1006

---

### Post by jeff-openenergy on 2014-11-09
My frontend runs 14.04 on a cheap ZBOX-BI320-U with the recordings on a ZFS server via NFS.  The key to not having problems is to turn off the sync option for the filesystem on your filer.  Alternatively, make sure you have a really fast ZIL device.  In nappit, this is an option on both the pool and per ZFS file system/share.  It generally isn't good practice to turn sync off, but since my TV recordings aren't mission critical I did just for that share.  I've been doing it for over a year now with no problems.  Like you, before I realized that turning "sync" off was the key, I tried a million other options all to no avail.  I'm sure your ZFS server has a similar option.

---

### Post by dannyboy79 on 2014-11-09
doesn't the async basically mean that sync is off?

---

### Post by mattlach on 2014-11-10
> **jeff-openenergy said:**
> My frontend runs 14.04 on a cheap ZBOX-BI320-U with the recordings on a ZFS server via NFS.  The key to not having problems is to turn off the sync option for the filesystem on your filer.  Alternatively, make sure you have a really fast ZIL device.  In nappit, this is an option on both the pool and per ZFS file system/share.  It generally isn't good practice to turn sync off, but since my TV recordings aren't mission critical I did just for that share.  I've been doing it for over a year now with no problems.  Like you, before I realized that turning "sync" off was the key, I tried a million other options all to no avail.  I'm sure your ZFS server has a similar option.

Thank you.   I already have two mirrored Intel s3700's as SLOG/ZIL and even so, I have created a separate dataset for MythTV recordings with sync=disabled, so I don't think the sync issue is what's killing it for me.

> **dannyboy79 said:**
> doesn't the async basically mean that sync is off?

The NFS mount option async DOES mean this, but this is what NFS requests, not necessarily what it gets.

ZFS has three different settings for sync, which you can set either globally for the entire pool, or on a per dataset basis.

sync=default:     Tries to obey application/protocol preferences to be asyncronous or syncronous.
sync=always:     Disregards application/protocol preference, and runs synchronous no matter what
sync=disabled:     Disregards application/protocol preference and runs async no matter what.

This way you can tune your ZFS based storage server to use syncronous writes in areas you know are sensitive to loss, and asyncronous writes in ones where you know it doesn't matter.


My problem seems to occurr only when writing to and reading from the SAME file at the SAME time, like when watching live TV.  Scheduled recordings appear to function perfectly.

Based on this, as a workaround, I threw in an old WD green drive, and set up a dedicated livetv recording folder on it, and send scheduled recordings to my ZFS Pool on my FreeNAS box.

I'd rather fix this all together though.

A user by the handle ljw1 on the FreeNAS forums suggested the following may be the cause:

[quote=ljw1]
Everything you have discussed could be attributed to the copy on write file nature of zfs. Every time the file is written to a new copy is made which will not allow access until it is completed. NFS has an annoying behaviour of locking the file system while it is being used which could easily timeout the playback machine.[/quote]

Considering I see my problems only when reading from and writing to the same file at the same time, it sounds plausible to me that this is what is going on with my setup.


In order to fix it, I intend to try to mount the folders using SAMBA instead of NFS and see if it goes away.   If that doesn't work, I might try iSCSI, but I'd hate preallocating images on my NAS, and then only ahve them able to be accessed by one system at a time, rather than be shared.

I never unsderstood why iSCSI is so popular in Enterprise IT circles, the fact that it is preallocated, (even if you thin provision it by using a sparse file) limits its usefullness, by creating a fixed max size, rather than it being dynamic, and the fact that the image is locked to just one OS at a time, rather than having shared access, is just a huge pain in the ass.

Hoping Samba will work and fix my issues :p

---

### Post by jeff-openenergy on 2014-11-10
Sorry to hear that didn't fix it.  SMB is worth a shot.  You might also look at what is happening to the ZIL when sync is disabled or try nappit on OmniOS instead if you can stomach Solaris.  If you can isolate activity to where only the recording is trying to write over the network, you should see no ZIL activity with sync disabled (it just keeps the changes to RAM directly before flushing them to disc every 5 seconds or so).  

You've got a pretty sweet setup for home - I'm jealous!  I manage several systems at work similar to what you have with 10g networking and mirrored ZIL but haven't convinced my boss I need the same setup at home for "testing purposes".  :-)

---

### Post by mattlach on 2014-11-10
> **jeff-openenergy said:**
> Sorry to hear that didn't fix it.  SMB is worth a shot.  You might also look at what is happening to the ZIL when sync is disabled or try nappit on OmniOS instead if you can stomach Solaris.  If you can isolate activity to where only the recording is trying to write over the network, you should see no ZIL activity with sync disabled (it just keeps the changes to RAM directly before flushing them to disc every 5 seconds or so).

I appreciate the suggestions!   I've had some philosophical differences with the FreeNAS forum moderators (or one specifically) and have actually considered switching to Napp-IT, but haven't yet as it was suggested to me that Napp-IT might not be compatible with my GPT based pool, and I REALLY don't want to break it down and recreate it.   That and NappIT doesn't seem to ahve much of a user forum at all, which could stink if I ever get stuck.

Except for this one little issue of dealing with Live streams from MythBuntu, FreeNAS has  been working very well for me.  We'll see what happens over time.

> **jeff-openenergy said:**
> 
You've got a pretty sweet setup for home - I'm jealous!  I manage several systems at work similar to what you have with 10g networking and mirrored ZIL but haven't convinced my boss I need the same setup at home for "testing purposes".  :-)

Thank you.   It's actually a little more ghetto than it sounds on the forum.  We are talking old dual socket LGA1366 Supermicro board I found on ebay without an I/O shield (got a shield later) for $150, a set of paired 6 core Xeons for $120 used on eBay, 12 used DDR3 RDIMMS for $40 a piece, and a bunch of old Intel NIC's and other hardware I had kicking around from previous builds.

It's amazing to me how quickly older enterprise hardware drops in value and can be found cheaply on eBay.

If it weren't for all the money I have into drives, SSDs and that Norco case, it would have been an absolute steal.

I can't remember how I put it above, but I don't actually have any real 10gig ethernet hardware.  it is all internal to ESXi using virtual VMXNET3 drivers.   Only the 1gig interfaces are external to the box (but the box has 9 1gig ports)

If you are more interested in my build, I did a pretty extensive post [over here](http://hardforum.com/showpost.php?p=1041106037&postcount=1396).   (I have since added two APC SmartUPS units, one SUA750 and one SUA1500) to deal with power outages.

It's fun to do a lot on a budget on eBay and snap pieces up when you see them at the right price, as long as you aren't afraid of doing some stability testing.  (I have spent WAY too much time with Memtest86+ ...)

---

### Post by dannyboy79 on 2014-11-10
not sure if this is any help but i found it within the mythtv archive forums
> 
If you're RAID card contains a battery it is likely it cheats by 
reporting to the O/S that it's committed the data to disk when in fact 
it's only committed it to battery-backed RAM. This is fine so long as 
the O/S doesn't schedule too many commits per second, because in that 
instance, the RAID card is constrained by the speed at which the HDDs 
can commit. RAID cards with a GB or so of RAM will ride out almost all 
the bursts you are likely to experience. 

In general, a database insert will consist of a tail append of a MYISAM 
data file and index file, corresponding updates to the filesystem inode 
table, block bitmaps or free extent maps and a journal write. Although 
it is true that the filesystem structures are only updated at 
journal commit intervals, they will all hit you eventually. On a 
streaming system like MythTV, it could easily cause a stutter if there 
are lots of filesystem structure updates to perform at each commit 
interval. As the saying goes, you don't get owt for nowt. For this 
reason, I advise Monkey Pet to use a shorter commit interval. The 
default of 5 seconds seems reasonable. 

A further consideration for RAID 5/6 systems is the nature of each disk 
write. Remember, I'm talking about database writes which will be mostly 
single filesystem block writes. In a RAID 5/6 array, the disks are 
presented to the O/S as stripes. Each stripe, consists of one or more 
sectors from disk 1, the same from disk 2, ... and the same from a 
parity disk (or two for RAID 6). To keep the parity correct, a write of 
a single filesystem block (say 1kB), the RAID system must do this: 

- Read those sectors from disk 1's share of the appropriate stripe. 
- Read those sectors from disk 2's share of the appropriate stripe. 
- Read those sectors from disk 3's share of the appropriate stripe. 
... 
- Overwrite the memory buffer with the changed data 
- Re-compute the parity 
- Write out the changed sectors to the disk containing the data. 
- Write out the changed sectors to the disk containing the parity. 

This is a slow process because it consists of four sequential stages. 
Although a RAID controller will launch the reads in parallel, it will 
be forced to wait for much longer than you might think because the 
spindles of the drives are not synchronized. You should expect an 
average of three disk rotations per read-modify-write sequence. At 
5400rpm, this sure eats into your performance budget. 

For sure it's not all that bad. With a large-enough cache many of these 
writes can be coalesced into full-stripe writes, and it's also likely 
that regular tail appends will still be in the RAID cache, but even so 
it's very easy to hit pathological cases. Don't forget that RAID5/6's 
read-modify-write process requires N times the cache memory of RAID 0 
or 1. If your video is being written through the same controller (even 
if it's on separate disks) this will turn over the cache rapidly. 

If you've spent any time working with databases you'll know just how 
much everyone relies on data being in cache, nicely indexed, subject to 
only the shortest of locks and above all, with uniform data 
distribution. A battery-backed RAID system is a nice adjunct to a 
database, but only if it offers low-latency and sustained throughput. 
RAID 5/6 will come and bite you in the **** at a critical time. 

For a more complete review of the impact of RAID 5, I suggest reading 
chapters 29-31 of Recovery Mechanisms in Database Systems by Kumar and 
Hsu. The performance figures they quote bear out my experience. 

I haven't been following this thread closely so forgive me if it's 
already been asked, but what kind of disk systems do those people who 
are experiencing problems have? I'll start the ball rolling by 
describing mine: 

- One cheap-jack old motherboard with some SATA ports and a 2.5GHz 
Dual-core Celeron. 
- A couple of 1.5TB 7200rpm HDDs, both with video data on them and one 
with the database as well. 
- LVM and dmcrypt. 
- ext4 noatime,nosuid,barrier=1 for the database 
- xfs nodev,noexec,nosuid,barrier for the video 
- MySQL binlogging on 
- MythTV 0.27 + my posted patch for bulk inserts to recordedseek 
- Ring buffer set to 14000KB I think 
- No kernel tweaks 
- Not using NFS 

I haven't had a chance to examine any later versions of MythTV. 

I'm not saying it has anything to do with disks but I'd like to know if 
problems are more likely when people move away from what might be 
considered a bog-standard config. 

Yours, 

Mike.
here: [http://www.gossamer-threads.com/lists/mythtv/users/563179?page=last](http://www.gossamer-threads.com/lists/mythtv/users/563179?page=last)

---

### Post by mattlach on 2014-11-10
> **dannyboy79 said:**
> not sure if this is any help but i found it within the mythtv archive forums

here: [http://www.gossamer-threads.com/lists/mythtv/users/563179?page=last](http://www.gossamer-threads.com/lists/mythtv/users/563179?page=last)

Thank you.   interesting reading for sure, but not sure how it relates to ZFS.  Hardware RAID and ZFS operate very differently.

My two SAS RAID cards are actually flashed to IT mode, so they just present a bunch of drives to the OS, and let ZFS do the work instead.   There is no RAM on them, but the system RAM on the ZFS box does something similar to the RAM on the RAID card in your quote (when sync is disabled).  If sync is enabled, it uses either a fast dedicated SSD for this purpose, or if no dedicated SLOG/ZIL is present, it writes it to the pool, which can be slow.

That is why we were discussing sync vs. async above.

The rest of the stuff, I am not sure to what extent it applies to ZFS, as it operates rather differently than traditional hardware RAID.

---

### Post by lukeiamyourfather on 2014-11-10
What version of ZFS on Linux are you running? There were some changes made to the write throttling in 0.6.3 that make writes "smoother" and less "bursty" compared to 0.6.2 and older. It might be that the delay caused by the bursty writes is long enough to exhaust the video buffer on the client.

[http://open-zfs.org/wiki/Features#Smoother_Write_Throttle](http://open-zfs.org/wiki/Features#Smoother_Write_Throttle)

Then again it could be something else but if you haven't yet definitely upgrade ZFS on Linux to the latest version.

---

### Post by mattlach on 2014-11-13
> **lukeiamyourfather said:**
> What version of ZFS on Linux are you running? There were some changes made to the write throttling in 0.6.3 that make writes "smoother" and less "bursty" compared to 0.6.2 and older. It might be that the delay caused by the bursty writes is long enough to exhaust the video buffer on the client.

[http://open-zfs.org/wiki/Features#Smoother_Write_Throttle](http://open-zfs.org/wiki/Features#Smoother_Write_Throttle)

Then again it could be something else but if you haven't yet definitely upgrade ZFS on Linux to the latest version.

Sorry,  I should have been clearer.

The box all this is running on is a VMWare ESXi host.   ZFS is on a FreeNAS guest (thus BSD version).  MythBuntu is another guest on this host. (There are 7 in total right now)

I have no idea how the BSD and Linux ports of ZFS compare.

---

### Post by epkphoto on 2014-12-08
mattlach, have you had any luck fixing the playback freezing? I just switched from a dedicated server/drive for my mythtv backend to a VM with a NFS-mounted FreeNAS ZFS dataset and am seeing the exact symptoms you describe when playing livetv or a recording-in-progress. Very frustrating for what I thought would be a superior setup.

---

### Post by mattlach on 2014-12-08
> **epkphoto said:**
> mattlach, have you had any luck fixing the playback freezing? I just switched from a dedicated server/drive for my mythtv backend to a VM with a NFS-mounted FreeNAS ZFS dataset and am seeing the exact symptoms you describe when playing livetv or a recording-in-progress. Very frustrating for what I thought would be a superior setup.

I haven't had time to mess with it yet, but I have found some good information.

The user ljw1 over on the FreeNAS forums replied with this:

[QUOTE="ljw1, post: 150733, member: 23195"]Everything you have discussed could be attributed to the copy on write file nature of zfs. Every time the file is written to a new copy is made which will not allow access until it is completed. NFS has an annoying behaviour of locking the file system while it is being used which could easily timeout the playback machine. You could try is mounting the share using a different protocol eg cifs or sshfs and see if the behaviour persists.[/QUOTE]

My plan is to try SAMBA and see if that helps, when I get around to it.

---

### Post by epkphoto on 2014-12-13
> **mattlach said:**
> My plan is to try SAMBA and see if that helps, when I get around to it.

I switched my mythtv storage dataset mount from NFS to SMB/CIFS and noticed a considerable improvement. I can now watch live TV as well as recordings-in-progress without freezing or buffering issues. I haven't tested extensively to gather any metrics or test with multiple clients streaming at once, but initial indications are good. The combo of ZFS+NFS+MythTV seems to be a bad one.

---

### Post by mattlach on 2014-12-15
> **epkphoto said:**
> I switched my mythtv storage dataset mount from NFS to SMB/CIFS and noticed a considerable improvement. I can now watch live TV as well as recordings-in-progress without freezing or buffering issues. I haven't tested extensively to gather any metrics or test with multiple clients streaming at once, but initial indications are good. The combo of ZFS+NFS+MythTV seems to be a bad one.

Great!   Thank you for reporting back.  Been way to busy to test myself yet, but I am excited that this seems like a solution.   It isn't all that difficult to create a SMB share and mount.

(It is a little bit more tricky if you want it password protected, but want linux to mount it automatically)

---

