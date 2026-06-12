---
title: "Running out of disk space"
date: 2008-08-24
forum: Mythbuntu
---

### Post by Steve_M on 2008-08-24
I have, on a couple of occasions, run out of disk space on my drive as free space is not being reported correctly. If I log inb to a terminal I get the following message: 
```
Total Disk Space: Total space is 473,179 MB, with 162,894 MB used (34.4%)
```

however if i type in df
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            478543640 356808348  97618116  79% /
varrun                 1031060       248   1030812   1% /var/run
varlock                1031060         0   1031060   0% /var/lock
udev                   1031060        88   1030972   1% /dev
devshm                 1031060         0   1031060   0% /dev/shm
lrm                    1031060     45040    986020   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1            484535504 142384360 317731944  31% /storage
//192.168.1.101/media
                     472231344 229632072 218224252  52% /storage/videos
```

*note that the disk in question is /dev/sda1

Recordings will never auto expire as the system never feels the need to free up disk space, but as the recordings are on the same partition as the OS, the disk fills up and that corrupts the database and the system dies until I delete some recordings and repair the database.

How is the free space reported to myth and is there a way I can correct it without reformatting and reinstalling?

---

### Post by stevanbt on 2008-08-27
Hi,
What does MythTv report as it's freespace in Information Centre, System Status?

Thanks, Steve.

---

### Post by Steve_M on 2008-08-28
System status shows:
462 GB Total, 159 GB Used, 303GB (or 66%)Free

So basically the same as (incorrect) terminal logon screen

Mythweb's backend status page also shows the incorrect data. 

The installation is 4 months old and has always been incorrect, I assumed it was a bug crept in to the 8.04 version as I downloaded and installed that when it was just out. But didn't see it mentioned as a fault

x64 version also (in case it matters)

---

### Post by Archmage on 2008-08-28
For me it seems that you are recording your shows in /var , therefore you are runing out of disc space.

Kindly check your path settings.

---

### Post by Steve_M on 2008-08-28
> **Archmage said:**
> For me it seems that you are recording your shows in /var , therefore you are runing out of disc space.

Kindly check your path settings.

Is that a problem?
That is the default setting. Where should the recordings go to?

I'll swap my recordings to the other disk and my share files to the main drive, and see what difference that makes

---

### Post by Steve_M on 2008-08-29
I moved all my recordings to a different disk & that has solved the problem.

Thanks for the suggestion.

---

### Post by anonymousdog on 2008-08-29
I see this issue as a larger problem for anyone with multiple storage groups which reside on unique partitions/file systems.  Since "space available" seems calculated on the system as a whole, as long as there's space >"Extra Disk Space" on some/any file system, the backend won't see the need to expire/remove old recordings to make more room on storage groups/file systems that may be short on or out of space.

For example (even if you avoid storage on /var or the partition that holds / or /var), you have / on /dev/sda1, /storage_group0 on /dev/sdb1, and /storage_group1 on /dev/sdc1.  /storage_group0 is getting really full (say <1GB free), but / and /storage_group1 have a combined 300+GB free.  If I'm understanding the symptoms correctly, the backend won't detect a disk space problem until total disk space on the whole system falls below the "Extra Disk Space" parameter in MythTV frontend setup (which defaults to a really low 1GB).  Meanwhile, /storage_group0 is (essentially) full which creates errors when the backend tries to store new recordings there (and the db gets inconsistent with the file system).

If I'm making incorrect assumptions, chiefly that "Extra Disk Space" applies to combined free space on all file systems, please correct me, but I think I've seen behavior that supports it (that assumption).  I haven't allowed my machine to get low on space on / or /var; so, I can't confirm this.

If my assumption is correct, the problem is exacerbated in the very common upgrade scenario where (the default storage group is mostly full and) a user adds a new file system to the system in some way (i.e., new local disk, remote mount, etc.) and a new storage group on that space.  In this situation (where, by default, the videos directory and mytharchive temp directory share space with the default storage group on /var), the system runs out of free space for the default storage group, the mytharchive temp directory, and the storage location for MythTV videos at the same time.  Meanwhile the backend sees no disk space problem at all (and makes no attempt to free space on the file system that includes /var).

Ideally (IMHO), the backend would monitor each file system on which a storage group is defined, and it would attempt to maintain >"Extra Disk Space" of free space on each of these file systems.  In fact, I think the best solution would be for the "Extra Disk Space" parameter to be a property for each storage group.  Then, the user could set "Extra Disk Space" per storage group as he/she may want to maintain more space on a group that shares space with / or /var (or some other path) while allowing very small "Extra Disk Space" on storage groups whose underlying file systems don't have needs other than video storage.  A global "Extra Disk Space" parameter could still be used in the case that a per-storage-group isn't needed.

Am I way off here?  If not, these problems will even creep up even with single physical disk systems where multiple partitions and file systems have been created for /boot, /, /root, /var, etc.  Combined free space greater than "Extra Disk Space" would prevent the backend from detecting a free space problem, even if the file system holding the default storage group were almost full.

---

### Post by Steve_M on 2008-08-29
I had no entries for storage in the default group, the system just defaulted to /var/lib/mythtv/recordings. I figured it may have been due to not having an entry there so I checked my slave backend which does not yet have a tuner attached.

When I logged in to the terminal I had the following status

> Total space is __drive_total_total__ MB, with __drive_total_used__ MB used (unknown)


I set up the storage groups but that didn't change anything. This system has only one drive so it looks like I may have to partition the drive before I can reliably use it. 

I used both systems together with the previous version of mythtv without this problem so it seems due to the introduction of storage groups.

---

### Post by anonymousdog on 2008-08-30
Sorry, that was a bit of a thread hijack.  Wasn't trying to suggest a fix or anything wrong with your setup.

What does 'mythtv-status' on that slave backend return?  How about 'cat /etc/default/mythtv-status'?

---

### Post by Steve_M on 2008-08-31
Running systems status on the slave sows the same as on the primary. The values for diskspace should be added (at least were in my previous install)

This is the output of 'cat /etc/default/mythtv-status'
(and thanks, up till now I always opened a file in an editor to read it's contents :) )

```
$ cat /etc/default/mythtv-status
# mythtv-status Debian configuration
#
# You can run 'dpkg-reconfigure mythtv-status' to modify the values in this
# file, if you want. You can also change the values here and changes will
# be preserved.
#
# Do note that only the values are preserved; the rest of the file is
# rewritten.
#

# RUN:
#  Should we actually run and update the MOTD?
RUN=yes

# HOST:
#  What host should be check the status on?
HOST=localhost

# ARGS:
#  Any extra arguments to pass to mythtv-status (i.e., -e and/or -d).
ARGS=

# EMAIL:
#  A comma separated list of email address to send status emails to.
#
#  Set to none (or leave empty) to disable daily emails.
EMAIL=none

# EMAIL_ARGS:
#  Command line arguments that are used when sending the daily email.
EMAIL_ARGS=-email-only-on-alert
```

I tried 'sudo dpkg-reconfigure mythtv-status' to see if setting an IP instead of localhost but that made no difference. Once run, the output of that is

```
sudo dpkg-reconfigure mythtv-status
 * Stopping MythTV Status  mythtv-status                                 [ OK ]
 * Updating MythTV Status  mythtv-status                                        Unable to find any value for drive_total_total while looking at Total Disk Space
Unable to find any value for drive_total_used while looking at Total Disk Space
Something is wrong calculating the disk space percentage.
                                                                         [ OK ]
```

When I installed the slave backend I found it locked up whenever I tried to use the tuner, but initially figured it was a problem with the USB tuner I was using (support for that tuner was sketchy at the time), now I am wondering if the problem was due to not knowing where to put the recordings. 
I have a free weekend coming up soon so I will look at rebuilding that system from scratch and partitioning the drive. There is no valuable data there yet so as long as I can do that and restore it to being able to view programs by the end of the day I will be safe :)

---

