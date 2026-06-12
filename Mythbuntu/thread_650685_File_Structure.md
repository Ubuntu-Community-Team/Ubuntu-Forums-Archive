---
title: "File Structure"
date: 2007-12-26
forum: Mythbuntu
---

### Post by tj71587 on 2007-12-26
Is there anyway to configure the way the files are saved.  I want to run samba so other PC's in the house can watch anything that I record.  I have it going to the directory, but the titles are unreadable.  Will this change when I order schedules direct, or is this the way it will be no matter what, or is there a way to change this?

---

### Post by murchball on 2007-12-27
AFAIK the naming convention for the files is based on tuner, channel, time and date and there is no way to change this (I could be wrong). I think the easiest way to watch on any PC in the house is either to install mythfrontend (linux or mac only) or to just use a browser and mythweb. Mythweb gives you a nice interface that will show you when a show was recorded and on which channel. Plus you can schedule recordings from here.

---

### Post by superm1 on 2007-12-27
Additionally, there are two other options:

mythtv-fusefs
This creates a fuse filesystem for recordings with easy to read names.   Install it and read it's documentation to learn more.

mythlink.pl
This is in /usr/share/contrib/mythtv-backend.  It creates symbolic links to all your recordings.  It has to be run pretty regularly (several times an hour on a cron job) if you want it to work well.

---

