---
title: "Having trouble with myth archive - where is the log file kept?"
date: 2008-01-05
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-01-05
I have not been able to get myth archive to work before, but I decided to try and figure it out.

I am trying to archive a recording to DVD and I am getting an error during mythtranscode, according to the log that is written to the screen.   Something about  it failing to get the stream info from the recording file...

I'd like to look through the log more carefully and maybe post it here.  Where is this log kept on the hard disk?

---

### Post by dflipb on 2008-02-19
i believe it is in  /var/lib/mythtv/

---

### Post by dflipb on 2008-02-20
I meant /var/log/mythtv/

---

### Post by dannyboy79 on 2008-02-20
i had this problem because I have a SBE that keeps it's recordings on it own drive (no NFS mounts) and when I chose to archive it to dvd, it failed and said it couldn't find the file. Maybe that's the same issue here? otherwise can't help you.

---

### Post by matthewgeier on 2008-03-01
/tmp/logs/mythburn.log
for what it's worth.

 I've never actually gotten mytharchive to work at all, ever, under Mythbuntu. I've just installed the mythbuntu 'svn' build today, and it STILL doesn't work.

 What's even more annoying, if I cut-n-paste the failed mythtranscode command line to a terminal window, it runs to completion with out error.

 I used to have my mythbox running Fedora Core 4 and the ATrpms build of Mythtv. I had mytharchive working on that system, I recently decided it was time for a OS upgrade and clean re-installed Ubuntu.  Mytharchive has never worked since.

---

### Post by Nikas on 2008-03-01
Work great with the solution found here:
[http://ubuntuforums.org/showthread.php?t=610856&page=2](http://ubuntuforums.org/showthread.php?t=610856&page=2)
Look at post #12.

---

