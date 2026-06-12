---
title: "backup now from mcc"
date: 2012-07-02
forum: Mythbuntu
---

### Post by jim09 on 2012-07-02
Cant get backup now to work from the mcc.  A scheduled backup seems to work. A box pops up and says finished but no file is produced.  I tried a few different directories but no luck.  No error logging appears to take place. Any suggestions?

---

### Post by tgm4883 on 2012-07-02
> **jim09 said:**
> Cant get backup now to work from the mcc.  A scheduled backup seems to work. A box pops up and says finished but no file is produced.  I tried a few different directories but no luck.  No error logging appears to take place. Any suggestions?

Launch mythbuntu-control-centre from the command line and try the backup again. It should print errors to the terminal. You can also see if there are any logs in /var/log/mythtv/ or /var/log/mythbuntu/

---

### Post by jim09 on 2012-07-03
I'm running mythbuntu 12.04.  No error message when mcc run from a terminal window.  Nothing in the log files.  There have been a couple of crash reports.  That may have occurred when I run mythbackup.py from the command line.  The msgs indicates IO err permission denied trying to write the log and backup files.  I notice the scheduled backup seems to run as root and backup now as user.

---

### Post by tgm4883 on 2012-07-03
> **jim09 said:**
> I'm running mythbuntu 12.04.  No error message when mcc run from a terminal window.  Nothing in the log files.  There have been a couple of crash reports.  That may have occurred when I run mythbackup.py from the command line.  The msgs indicates IO err permission denied trying to write the log and backup files.  I notice the scheduled backup seems to run as root and backup now as user.

Hmm, if you change the permissions on the log file so it has access to write to it (like 666) can you do a manual backup?

---

### Post by jim09 on 2012-07-03
No change.  Scheduled backup works, backup now doesn't. Tryed with and without the database ticked.  No luck.  Also purged and re-installed mythbuntu-bare-client.

---

### Post by tgm4883 on 2012-07-03
> **jim09 said:**
> No change.  Scheduled backup works, backup now doesn't. Tryed with and without the database ticked.  No luck.  Also purged and re-installed mythbuntu-bare-client.

Odd. I'll take a look at it when I get home.

---

### Post by tgm4883 on 2012-07-07
Sorry it's taken me so long to get back to this. I've identified the issue and have pushed a fix. It should show up in the Mythbuntu repositories in a few hours. Make sure the Mythbuntu Updates repository is enabled in MCC

---

### Post by jim09 on 2012-07-07
Thanks for the fix.  Is working now.  I was also having trouble getting the restore to work when I was testing.  Did the fix deal with that or is it something different.  I was able to take the files from the archive and restore them manually.

---

### Post by tgm4883 on 2012-07-07
> **jim09 said:**
> Thanks for the fix.  Is working now.  I was also having trouble getting the restore to work when I was testing.  Did the fix deal with that or is it something different.  I was able to take the files from the archive and restore them manually.

I'll have to look at that as well, as I only did a fix for backup. Are there any error messages?

---

