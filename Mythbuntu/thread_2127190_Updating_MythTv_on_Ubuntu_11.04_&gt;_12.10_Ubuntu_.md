---
title: "Updating MythTv on Ubuntu 11.04 &gt; 12.10 Ubuntu w/Mythtv"
date: 2013-03-19
forum: Mythbuntu
---

### Post by grunge09 on 2013-03-19
I have the last pre unity Ubuntu v11.04 running Mythtv with 2 tuner cards on a gigabit connection..  I have a spare hard drive that would like to do a fresh install of latest ubuntu 12.10 and add mythtv to it.  

Almost forgot that my mythtv recorded data is not on the same box, I recently moved it to an Ubuntu Server PC across same gigabit network.  I ran out of room on the 2tb drive.

PC is:

AMD 965 3.4GHJz Quad Core
4GB RAM
2 TB Sata Drive
LG Sata DVD Drive

My question is this:

Can I backup and restore my config's to a new fresh install.

Or I do not have re-setup all my devices and program recordings.  

Please advise.  If so how.  Thanks in advance.

Update #1:

I had the original 1tb sata drive still in the box.  I had done a DD copy and then gparted re-size onto the 2TB drive.   Since I had went from the 1tb to the 2tb drive I added a PVR-500 and had moved all the /var/lib/mythtv data to /mnt/mythtv (mounted samba share on ubuntu server box).

I tried mythbuntu control center backup (off the 2tb drive) and restore (after moving power and data to the 1tb drive) and reboot, all kinds of errors.   So I added the PCR-500 card,(in backend config) , ran mythtvfilldatabase, updated all the paths to the /mnt/mythtv share (in backend config) 

BUT the 1tb older install does not see a lot of the recordings since the 2tb upgrade.  And the rules I have added since then are not there either.  

I re-plugged the 2tb drive back in and rebooted and it sees all the files.  

Where are the config files to make mythtv see all the data?

Update #2:

I ran :

mythtv backup on 2TB Drive

mysqldump -u mythtv -p -t mythconverg record recorded \ oldrecorded recordedprogram recordedrating \ recordedmarkup recordedseek > recordings.sql

mythtv restore on 1TB Drive (same mythbtv and ubuntu version and same mysql pswd) 

mysql -u mythtv -p mythconverg < recordings.sql

Checked Recordings and some are still missing as well as recording rules.  Still no help.

Update #3:  

Ran across these commands:

Make a backup of mythtv database file on 2tb drive

mysqldump --opt -u mythtv -p mythconverg > mythconverg.bak

**NOTE Backup went quick like 5 seconds, made a 306 MB file.

Copy of USB flash Drive and shut down them hook up 1tb drive and power up.

Restore a database file on old 1tb drive (from same location as 2tb drive \home\mythbackup folder) 

mysql -u mythtv -p -v mythconverg < mythconverg.bak

**NOTE** Restore took several minutes, you don't need the "-v" I added that to show me it was doing something.  the "iv" will spew all kinds of numbers and letters on your screen, then come back to a command prompt when done.  

I ran Myth Backend Config and just exited out, ran myth fill database, and then re-ran frontend, and WALA all my recordings are there, recording rules, etc.

problem solved.

---

