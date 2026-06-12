---
title: "opinions on filesystems for myth [ZFS RAID-Z 1/2 or individual disks or combo]?"
date: 2014-10-30
forum: Mythbuntu
---

### Post by david169 on 2014-10-30
Hi all,

don't often post here, but I've been tinkering with my myth setup again having moved house and been looking into making better use of my setup.

I like the idea of a storage pool for multiple HDDs as it should make the best use of the space. I want to avoid the scenario whereby I've allocated a load of space for Myth recordings and I end up not needing but then don't have enough space for normal storage and then have to manually mix and match folder locations to fill up the drives.

A storage pool seems ideal and in my recent refresh of my myth network I created a ZFS RAIDZ-1 with 6x 2TB drives and created a load of myth partitions in that for my backend with quad tuner to use.

So, first question, when multiple streams are being written to multiple ZFS partitions of one pool, is it (ZFS) smart enough to make use of the fact it has 6x drives attached and can write the 4x streams to 4x physical disks or will it potentially interlace the data on the drives and cause horrendous performance issues further down the line?

I guess ideally I want to cap each myth drive and pre-allocate the space if possible and that might do it but I'm not that familiar with ZFS yet to know if or how to do this.

I screwed up my initial ZFS setup (I've done it as 4x2 drives instead of 2x (2+1)) so as I need to remake the pool anyway I'm trying to work out the best solution having got a little bit of experience with ZFS.

Or I just make one or two drives exclusive use for Myth and put the rest into a storage pool.

What are people's experiences with large storage sets? I guess a better way might be to transcode the files and write them out to a central storage for better use of the space and should avoid the simultaneous write issues.

Thoughts?

Thanks,
Dave

---

### Post by AlecJ on 2014-10-31
Hi

I use individual drives, 2 x 1TB, 1x 3TB, 1x 1TB USB and 1x 32GB solid state for the system.

the 2x 1TB each have a Recordings folder and myth fills them with live TV from the 6 tuner cards each giving 2 feeds.

the 3 TB only has a 2 TB partition only that holds the Movies and Music, this was a 2TB drive that failed, the only way to recover a large partition was to image the damaged drive onto a large empty drive. Hence 3TB , I'm at a loss as what to do about this right now?

the usb drive holds all the backups and copies of the photos and music folder's.

I've had many drive failures over the years and every time it's been touch and go how much of the data I can save, thats the trouble with ripping all our DVD's then donating the DVD away, just to have a less cluttered lounge?

The main problem is heat, I have silent fans on all the drives and have moved the whole setup to a rack server type box full of fans. I noticed that the drives in the caddies last longer than mounted next to a power supply and CPU heat sinks etc, having said that the last drive had bearing failure.. no grease nipples what can you do? 

So if your raid can survive a drive fault, won't over heat and won't be too noisy. Then maybe thats the way to go?

Alec

---

### Post by dannyboy79 on 2014-10-31
the most important aspect is how fast can you write to the data pools? i recall when i was asking on the unraid forums whether using unraid with mythtv would be ok and they said the particular setup i was talking about doing that i may have performance issues. currently i just have 1 2TB drive formatted as XFS and another 1TB formatted as EXT4 and then in mythtv i have 2 storage groups. the main os is on a 250GB HDD

---

### Post by jensk on 2014-10-31
I have no experience with ZFS but I have for years been using my NAS - presently OpenMediaVault - as the sole storagepool for my mythserver.
The server accesses the NAS storage via NFS and event though my NAS is based on a meagre AMD E350 processor I have no problem doing 2 HD recordings while doing 2 other HD playbacks to different frontends simultaniosly. My backend server has no frontend.

The only time I had performance problems was when i did not have the solves the UID and GID properly between Mythserver and NAS.

On my OMV NAS i have storage consisting of one big pool made up of 6 x 3T WD reds in raid6 configuration. All shared as one big storage poll with different shares and services to myth, to home pc's, to PXE boot and devices/services like Sonos, Subsonic  etc.

---

### Post by david169 on 2014-10-31
> **AlecJ said:**
> Hi

I'm at a loss as what to do about this right now?



whats the filesystem (XFS, JFS, EXT3/4 etc)? Can Gparted not grow it to fill the extra space?

I haven't fully tested the I/O performance of my ZFS storage pool, that would probably be a good start but equally the performance today might not be the same as a year from now depending on how optimally the data is written to the drives and by then it will be a pig to get the data off it! I suppose another option would be to run a defrag every week/month or something similar to sort that problem out.

When DVB streams are multiplexed with others, does myth just write out the one stream or does it split it up first? As I have a quad tuner I'm wondering if I should ideally have 4x separate partitions (one per tuner) or n*4 where n is the number of simultaneous multiplexed channels I tell Myth it's allowed to record.

Another advantage of the storage pool / ZFS option is I can limit the space myth uses quite easily with quotas. With liveTV I highly doubt that I'll want to keep more than 1TB or so of recorded content so I don't really want to dedicate 8TB to it (4x2TB drives) and currently physical space is the limiting factor in my case... I can maybe squeeze 2-3 more HDDs in there before I have to start getting creative... I've already lost 2x bays due to vibration isolation measures for the 6x spinning drives - system drive is a SSD so that can easily be moved.

I have been thinking of getting a 8-12U 19" rack and filling it with drives so this wouldn't be an issue but my cupboard under the stairs where this lives has an old 4" waste pipe right where it would go so can't go down that route until it's removed!

---

### Post by AlecJ on 2014-11-01
Not sure, I often have 6 recordings at the same time, the recording go into one of the folders on the 2 different drives I don't have a choice which go where, (if their was I didn't mess with it) , only have 2 because 1 TB of recording's was not enough?? and if you run out of space it all stops, no TV!
The drives are all SATA and plugged into ports on the motherboard.
We do have a clear out every so often, there is only so much Downton abbey she can save..

normally have 55% free space on the drives but I've seen it at 5% free space on both drives.
I archive most the films off into the movies folder after the ads have been removed.

---

