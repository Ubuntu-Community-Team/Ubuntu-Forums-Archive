---
title: "Disk free space problems"
date: 2008-07-05
forum: Mythbuntu
---

### Post by menny on 2008-07-05
Hi,
It seems that mythtv does not behave nicely when the disk is small.
I have a 80gb disk, and about once a month I get free space related problems.
The backend does not starts-up and the frontend deletes all my preferences (like Playback and OSD configuration).

The problems are caused due to either a huge log file (I had some weird repeating log line "skipping frame" or something) or due to large recording files.

So:
1) How can I limit the size of the log files?
2) How can I configure mythtv to automatically delete old clips when space is needed?

Thanks,
Menny

---

### Post by tgm4883 on 2008-07-05
Sounds like the recording directory is on the same partition as the as root, which isn't ideal.

You can either fix that, or in either the frontend setup or mythtv-setup there is a setting for amount of free disk space to keep.

---

### Post by menny on 2008-07-06
So, it will automatically delete old recording?
What about the log file? Is there a way to limit it size?

---

### Post by menny on 2008-07-25
Hi,
MY free space problem is getting annoying. I have three partitions:
1) Linux and MythTV installation - 80gb
2) Recording (livetv and default) - 250gb
3) Media files (movies and music) - 250gb

I suspect that mythtv does not delete old files, since I get ZERO free space on the recording partition.

Can someone explain to me how to configure mythtv to delete clips when space is needed, and how to configure it to delete LiveTV clips after two days automatically.

Thanks.

---

### Post by mrand on 2008-07-25
> **menny said:**
> Hi,
MY free space problem is getting annoying. I have three partitions:
1) Linux and MythTV installation - 80gb
2) Recording (livetv and default) - 250gb
3) Media files (movies and music) - 250gb

I suspect that mythtv does not delete old files, since I get ZERO free space on the recording partition.

Can someone explain to me how to configure mythtv to delete clips when space is needed, and how to configure it to delete LiveTV clips after two days automatically.

Thanks.Howdy Menny,
Are you sure it isn't deleting LiveTV clips automatically?  I believe the default behavior is 1 day.  If it is going beyond that, you should verify the setting.

For the rest... as tgm4883 said, in frontend setup, under general settings, there is setting with wording something like "Free Disk Space Threshold."  I believe that Myth doesn't delete anything until it falls below that threshold, and then it only deletes the oldest items until it rises above that threshold again.  In other words, Myth tries to keep shows on your hard drive for as long as possible. 

The last setting of interest is for when you actually delete a recording. Check Setup->TV Settings->General->2nd Page, where you should find the "Autoexpire instead of Delete" checkbox.  If checked, it keeps deleted recordings around as well (but autoexpires them first when disk space crosses the above mentioned threshold).

[INDENT]Marc[/INDENT]

---

### Post by menny on 2008-07-28
Hi Marc,
I've check the configuration again:
Auto expire method: Lowest priority first
LiveTV max age: 1
priority weight: 1
Extra disk space: 10 <- is this "Free Disk Space Threshold"?
Auto expire instead of delete recording: unchecked.

Am I configured correctly?

---

### Post by mrand on 2008-07-28
> **menny said:**
> Hi Marc,
I've check the configuration again:
Auto expire method: Lowest priority first
LiveTV max age: 1
priority weight: 1
Extra disk space: 10 <- is this "Free Disk Space Threshold"?
Auto expire instead of delete recording: unchecked.

Am I configured correctly?

Yes, extra disk space is the name of it now.  Everything looks correct.  

Are you having the problem now?  If so, what is the output of the "df" command from a Unix shell?  Also, are there any log files in in /var/log that are growing very rapidly, such that it would prevent mythtv from keeping the filesystem space available?

Also, take note of this from the [mythtv wiki]("http://www.mythtv.org/wiki/index.php/Storage_Groups")
> If Myth is not recording to a filesystem, it does not autoexpire programs <...>so until a recording starts and is being written to the filesystem in question, no programs will be expired from that filesystem. 

[INDENT]Marc[/INDENT]

---

### Post by nickrout on 2008-07-28
> **tgm4883 said:**
> Sounds like the recording directory is on the same partition as the as root, which isn't ideal.

You can either fix that, or in either the frontend setup or mythtv-setup there is a setting for amount of free disk space to keep.

unfortunately this is the way the boneheaded mythbuntu installer sets it up for you, unless you decide to manually partition. Even then nothing tells you that you need to mount the data partition on /var/lib/mythtv.

---

### Post by tgm4883 on 2008-07-28
> **nickrout said:**
> unfortunately this is the way the boneheaded mythbuntu installer sets it up for you, unless you decide to manually partition. Even then nothing tells you that you need to mount the data partition on /var/lib/mythtv.

Your concern has been noted.  Please be advised that the installer is Ubiquity and getting a different partition recipe in there isn't exactly straight forward.

---

### Post by nickrout on 2008-07-28
What would be nice as a minimum is some documentation telling you where to mount a separate partition, ath the partitioning stage, would be useful.

On page 33 of the install guide it says > Your now able to choose how you wish to partition the disk space. It’s recommended that you select Guided Partition and the drive you wish to partition. and click the forward button. You can however manually partition your drive but it won’t be covered here. You would do this if you where to install the OS onto one drive and your recordings onto another. 

On page 77 it states > As long as you setup a separate partition for /var/lib during the initial setup, the default option here - /var/lib/mythtv will work &#64257;ne.

So page 33 recommends a guided partitioning (which ends up as one big / partition) whereas page 77 proceeds on the basis that you have set up separate partitions.

---

### Post by tgm4883 on 2008-07-29
> **nickrout said:**
> What would be nice as a minimum is some documentation telling you where to mount a separate partition, ath the partitioning stage, would be useful.

On page 33 of the install guide it says  

On page 77 it states 

So page 33 recommends a guided partitioning (which ends up as one big / partition) whereas page 77 proceeds on the basis that you have set up separate partitions.

Fixed in 8.10

---

### Post by tgm4883 on 2008-07-29
On a related note.  We are looking for volunteers to help write the documentation.  Let us know if you would like to help.

---

### Post by nickrout on 2008-07-29
yeah well i can't program to save myself so I guess thats a way to give something back. Where do I apply?

---

### Post by tgm4883 on 2008-07-30
> **nickrout said:**
> yeah well i can't program to save myself so I guess thats a way to give something back. Where do I apply?

Get on IRC on irc.freenode.net and come to channel #ubuntu-mythtv-dev and tell them you are here to help write documentation

---

