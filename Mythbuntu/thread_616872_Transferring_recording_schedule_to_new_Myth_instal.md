---
title: "Transferring recording schedule to new Myth installation"
date: 2007-11-18
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-18
I have an old Myth installation working at the moment, and I am building a new machine that's fast enough to handle HDTV.  The main thing I wish to keep from the old box, is my recording schedule.  By this, I mean the catalog of stuff that I have told Myth to record anytime it sees it in the future.

Is there any easy way to transfer this info to the new install. Is it just one mySQL table?  I am familiar with databases (Oracle etc) but not mySQL, so I welcome suggestions on how to go about transferring this data.

---

### Post by superm1 on 2007-11-19
I believe it should be sitting in a few tables actually.  You will need the tables that describe the old recorded programs as well as the schedule that is used for picking what to record.  I don't know the table names off hand though.

Install phpmyadmin. It's the easiest way to export and import this kind of stuff with a straightforward interface.

---

### Post by ubnewbie2 on 2007-11-19
> **superm1 said:**
> I believe it should be sitting in a few tables actually.  You will need the tables that describe the old recorded programs as well as the schedule that is used for picking what to record.  I don't know the table names off hand though.

Install phpmyadmin. It's the easiest way to export and import this kind of stuff with a straightforward interface.

I wish I could install phpmyadmin, but the old mythbox is a knoppmyth machine that's crashed so often that the apt-get system does not work anymore :-(

---

