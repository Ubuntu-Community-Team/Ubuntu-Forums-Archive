---
title: "Incorrect free space reported"
date: 2012-12-11
forum: Mythbuntu
---

### Post by bcg30506 on 2012-12-11
I have my database and recordings in a separate /var xfs partition.  I just noticed an inconsistency in the way mythbuntu is reporting disk usage.

If I do:
```
/var$ sudo du -hcs *
3.8M	backups
37M	cache
0	crash
83G	lib
0	local
0	lock
347M	log
0	mail
0	opt
420K	run
8.0K	spool
0	tmp
16M	www
84G	total
```

But df shows a different usage amount:
```
/var$ df -hT .
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda4      xfs    287G  101G  187G  35% /var

```

17GB is a fairly large discrepancy.  How may I resolve this?  Is this a sign that my disk has problems that could lead to failure?

---

### Post by papibe on 2012-12-11
Hi bcg30506.

That doesn't look that bad. Consider that, unless specially tuned, a regular ext3/4 partition will reserve 5% of its space to system specific purposes.

Take a look at the section **Modify Reserved Space** in this tutorial: [Installing a New Hard Drive]("https://help.ubuntu.com/community/InstallingANewHardDrive#Modify_Reserved_Space_.28Optional.29").

Let us know how it goes.
Regards.

---

### Post by dannyboy79 on 2012-12-11
The standard cause for this is some user process keeping a deleted file open. When this happens, the space is not visible via &#8216;du&#8217;, since the file is no longer visible in the directory tree. However, the space is still used by the file until it is deallocated, and that can only happen once the last process which has the file open either closes its file descriptor to the file, or the process exits. You can use the lsof program to try to find which process is keeping an open file. Usually it&#8217;s some log file, or some large data base file which gets rotated out, but some older process are still keeping the log file open.

---

### Post by bcg30506 on 2012-12-11
Okay, it may have been an open process.  Don't know if it was mythtv or mysql or something else, but I rebooted, and now it reports:
```
/dev/sda4      xfs    287G   89G  199G  31% /var
```
So it's only 5GB from the df report of 84GB being used.  Much better!

As for the tunefs utility the link in the first reply mentioned, that will not work for xfs file systems.  It is only for ext variants.

Thanks!

---

