---
title: "System drive full"
date: 2009-03-12
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-03-12
Using Mythbuntu 8.10, I have a mystery. The system was running along fine. I shut it down for 2 weeks while traveling, turned it back on March 3 and updated to newest (on the command line), and noted that the sound had died. I then left it on for another week while traveling some more, thinking to fix the sound upon my return. Now I'm back so I attempted to run updates again but the updater (GUI) hung up. Rebooting did not help.

I started a terminal session, ran update and discovered the following:

```
/var/lib/mythtv$ sudo apt-get update
[sudo] password ....
:
:
:
Fetched 3858B in 1s (2435B/s)
Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
/var/lib/mythtv$

```

```
/var/lib$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             11535344  11535324         0 100% /
tmpfs                   963844         0    963844   0% /lib/init/rw
varrun                  963844       352    963492   1% /var/run
varlock                 963844         0    963844   0% /var/lock
udev                    963844      2768    961076   1% /dev
tmpfs                   963844         0    963844   0% /dev/shm
lrm                     963844      2384    961460   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6            963913480 263684304 700229176  28% /var/lib
overflow                  1024      1024         0 100% /tmp

```

```
$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /var/lib type xfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=49d7eef2-4c91-41eb-80bf-0c33fc03998c /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=161b0223-d3e5-4b1a-a96f-207225a29b11 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=20f586a7-fc2f-4779-8791-5d0203d445aa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

The /dev/sda1 Ext3 partition is completely full! Recordings go to the xfs partition mounted at /var/lib, not full.

The daily backup logs show a full backup was 2,227,821,275 bytes on Feb 8 (start up backups for this install), 2,476,409,927 bytes on March 3, and then the next day the incremental backup had 356 new files, 9,462,950,846 bytes. This corresponds to the day when I turned the system back on and ran the updater. Don't know the current version of mythtv -- but it should be whatever was in the normal repository that day.

Question: how might this have happened and how can I recover the space short of reformatting and reinstalling? (not a problem really since there's nothing that I need to keep here, but a pain nonetheless).

If I repartition how much larger should I make / ?

Thanks,

DJ

---

### Post by DrJohn999 on 2009-03-12
OK, shoulda checked around in this forum first -- the mythfrontend.log exploded to 8.2 GB. I deleted it (along with the archived older ones); after reboot disk usage now shows at 34%. Apt-get update/upgrade/autoclean succeeded. Immediate problem solved. 

But...

Restarting the frontend, normal log entries appear. So, why the exploding log file immediately after the updates on March 3??

--DJ

---

### Post by Caps18 on 2009-03-13
That is the big question.  I wondered why there isn't a limit on log file size by default as well.

---

### Post by DrJohn999 on 2009-03-13
Exactly...

I'm considering restoring the log to the xfs partition where it'll fit, then looking for some indication of what happened. 

Anyone have some suggestions on how to comb through an 8.2 GB log file and what to look for? 

-- DJ

---

### Post by tgm4883 on 2009-03-13
A log file that large is going to be a pain for some tools, but I bet the problem will stick out like a sore thumb (probably repeats the problem 100,000 times or so).

The reason there isn't a size restriction on the log files, is because there isn't really a way to set one.  At the moment, log rotate is set to rotate the mythtv files daily.  It can be set to rotate at a certain size (or optimally both), but the log rotate job only gets run once a day, thus making having both options irrelevant (and a size one irrelevant, as it wouldn't help here).

We are open to suggestions though as to how to remedy this issue, but the only option I can think of is putting /var/log on it's own partition, which is not really a fix.

---

### Post by DrJohn999 on 2009-03-14
Mythfrontend.log is full with this:

```
 63736 2009-03-03 16:14:12.641 NVP: Prebuffer wait timed out 10 times.

```

and then with this:

```
2009-03-03 18:00:54.020 LiveTV forcing JumpTo 1
2009-03-03 18:00:54.020 LiveTV forcing JumpTo 1
2009-03-03 18:00:54.020 LiveTV forcing JumpTo 1
2009-03-03 18:00:54.020 LiveTV forcing JumpTo 1

```
There are about two screens worth of each time stamp millisecond value, starting at 17:00:02 March 3. The file has 171,912,425 lines (!) of which 99.996% are "...forcing JumpTo 1"

So, this error continued to fill the log until the drive maxed out. Without a clear cause I'm not sure this can be replicated, but it sure was fun!

-- DJ

---

### Post by Caps18 on 2009-03-16
> **tgm4883 said:**
> We are open to suggestions though as to how to remedy this issue, but the only option I can think of is putting /var/log on it's own partition, which is not really a fix.

Can it do a check of the previous line to see if it is the same error message?  It could overwrite it and only update the time in that case.

Is there any way to make it only record once a second instead of every millisecond?

The third option may be just to disable logging by default, but make it easy to access the logs from the command console if you do experience a problem it can be turned on and read easily.

---

