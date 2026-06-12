---
title: "Root full, how do I fix this?"
date: 2009-01-29
forum: Mythbuntu
---

### Post by Vague Craig on 2009-01-29
Hi all,

I'm feeling really stupid at the moment so please be patient, Mythtv crashed this morning after I left it viewing live tv all night (may have been drunk wehn I went to bed). 
Now the box can't log in and complains about the disk being full (the root partition? is full, I checked using gparted 11.8G full)I'm guessing that the livetv group is the culprit and is recording to the root partition (the log has always complained about this but I have no Idea how to stop this?)

How do I fix this, I simply don't understand how I know whether I'm looking at the root partition or the big partition? I'm new to linux(you probably guessed that) and am really confused as to how I know what disk/ partition I'm looking at. I can use shell via ssh to talk to the box, or is it easier to delete the offending recordings using the live CD?

I just really want to understand how I'm supposed to find what I'm looking at?!?! Also how do I delete files using the command line, I can find no command suitable?

Cheers,

Craig

---

### Post by canoemoose on 2009-01-29
Right.
Your problem is the same as the one in this thread: [http://ubuntuforums.org/showthread.php?t=1051678](http://ubuntuforums.org/showthread.php?t=1051678)

See if turning logging off solves the problem.
The command-line command to delete files is "rm" BUT read the link I'll edit onto the bottom of the post first!!

EDIT: Here it is! [http://ubuntuforums.org/showthread.php?t=911613&highlight=fork+bomb]("http://ubuntuforums.org/showthread.php?t=911613&highlight=fork+bomb")

---

### Post by Vague Craig on 2009-01-29
Brilliant, I'd read the post you linked to (both of them) but yet failed to work it out :oops: I deleted the huge log file that was stroed this morning and all is now well, thanks a lot, I was beginning to lose my sense of humour.

I still don't get when I'm looking at what partition, how do I know what I'm looking at?

I'm guessing it's ok to delete all these logs (if I don't want to view them)?

Cheers again, made my evening! (not that I'm actually going to watch tv now!)

Craig

---

### Post by Caps18 on 2009-01-30
It's understandable if you haven't used Linux/Unix very much.  The file system layout is a little weird at first, but it works.

Here is my file system is setup for example (I had to tell it to use the directories to use specific partitions.)
/ root (hard drive 1, 10GB partition 1)
|.../wherever log files are (still hard drive 1, 10GB partition 1)
|.../all other files (still hard drive 1, 10GB partition 1)
|.../var/lib/mythTV/Recordings (hard drive 1, 700GB partition)
|.../var/lib/mythTV/Video (hard drive 2, 900GB partition)

---

### Post by rupert80 on 2009-02-01
> **Vague Craig said:**
> Brilliant, I'd read the post you linked to (both of them) but yet failed to work it out :oops: I deleted the huge log file that was stroed this morning and all is now well, thanks a lot, I was beginning to lose my sense of humour.

I still don't get when I'm looking at what partition, how do I know what I'm looking at?

I'm guessing it's ok to delete all these logs (if I don't want to view them)?

Cheers again, made my evening! (not that I'm actually going to watch tv now!)

Craig

From a command prompt enter: df -v
You will get a result something like this:
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda1             76034016  18460252  53741864  26% /
tmpfs                  1036096         0   1036096   0% /lib/init/rw
varrun                 1036096       444   1035652   1% /var/run
varlock                1036096         0   1036096   0% /var/lock
udev                   1036096      2840   1033256   1% /dev
tmpfs                  1036096       716   1035380   1% /dev/shm
lrm                    1036096      2004   1034092   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3            644155280  25913908 585520180   5% /media/data1
/dev/sdb1             76920416    184216  72828792   1% /media/data2

The first line (after the header) relates to the root partition.  In all Unix or Linux systems, root is referred to as slash (/), so you can see from mine that root is 26% full.  It's a good idea to keep your volatile content away from the root partition in order to avoid the situation you have just experienced.

If it was a log file that filled root, then I suspect your use% figure for root would still be pretty high even after deleting the log file.  Most operating sustems start to have performance problems when file systems exceed 90% usage, especially when they're fragmented, so it's a good idea to give yourself room to move.

If you look in /var/log, you will see lots of log files, some compressed, some not. As log files reach a predetermined size, they are 'rotated' by adding a number to the end, then a new log file is created.  The higher the number, the older the log file.  If you are desperate for space and don't need to look at the log files, you could delete some of the higher numbered ones.

Alternatively you can adjust your log rotation settings using logrotate (srangely!).  Look at the man page with:
man logrotate
from a command line.

Hope this helps!

---

### Post by Vague Craig on 2009-02-01
Cheers guys, that makes a lot more sense, though the root partition on mine doesn't seem particularly full:
/dev/sda1             11535344   2156864   8792512  20% /
Which means that the log file I deleted to get the box running again must have been huge?
I'll have to have a look at whats in the logs later to see what it was actually complaining about!

Thanks again.

---

