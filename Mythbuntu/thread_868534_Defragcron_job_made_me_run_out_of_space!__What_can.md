---
title: "Defrag/cron job made me run out of space!  What can I do?"
date: 2008-07-24
forum: Mythbuntu
---

### Post by dcwdrum on 2008-07-24
I am currently running Mythbuntu .21 and it has been running great for a few months now.  Last night I decided to go into the Myth Control Center and enable the nightly defragmenting and cron jobs because I figured it would be good for the system.  Today, when I went to check the TV listings in Mythweb I got this error: (sorry, I didn't copy the entire error message)

"SQL Error: Got error 28 from storage engine [#1030]"

From what I have found on Google, this means that I ran out of space on the installation partition.  Is this correct?

Here is how I have everything partitioned now. (13 GB for the OS)
```
+--Disk--+--Partition--+--Size--+--mount point---+--filesystem--+
|  Disk1  |     sda1     |  13 gb  |  /    (boot flag)  |       ext3       |
|  Disk1  |     sda2     |    2 gb  |  swap              |      swap      |
|  Disk1  |     sda3     |   50 gb |  /fileserver        |       XFS       |
|  Disk1  |     sda4     |   94 gb |  /mythtv/disk1  |       XFS       |
|  Disk2  |     sdb1     | 160 gb |  /mythtv/disk2  |       XFS       |
|  Disk3  |     sdc1     | 160 gb |  /mythtv/disk3  |       XFS       |
|  Disk4  |     sdd1     | 160 gb |  /mythtv/disk4  |       XFS       |
+----------+----------------+-----------+----------------------+------------------+

```

I still have plenty of storage space on my other partitions, however I'm not sure how to proceed with this.  Are there files that I can delete or possibly a different solution?  Any help would be great.

Thanks

---

### Post by tgm4883 on 2008-07-24
that seems odd.  I'd check log files and see if one of them grew huge.  Look in /var/log

---

### Post by dcwdrum on 2008-07-24
I just looked through */var/log* and nothing seems abnormal there.  After checking that I checked all of the directories under */* by viewing their properties to see if I could find any with a large file size.  What I found is my *home* directory using 9.3 GB of the 13GB allotted for the OS.

Under the home directory I have two subdirectories (*dcw177* (my user name), *mythtv*).  The *mythtv* directory is only 13.4 kb, however the *dcw177* directory shows 1251 items, totaling is 9.3 GB.  The only item I am able to see under the *dcw177* directory is *Desktop*.  So I think I may have narrowed down where the problem is, but I don't know how to see the 1251 files that are apparently making up this 9.3 GB.

---

### Post by dcwdrum on 2008-07-24
I found the problem.  I figured out how to display hidden files and found that I had a bunch of videos from using Mythstream hogging disk space.  I'm in the process of deleting those now and hopefully that should solve my problems.

Thanks!

---

