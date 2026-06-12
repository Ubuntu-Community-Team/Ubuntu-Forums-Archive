---
title: "Question on migrating myth"
date: 2008-02-24
forum: Mythbuntu
---

### Post by eagle63 on 2008-02-24
Hi, I'm a current Myth user running on an Ubuntu (Feisty Fawn) machine.  I'd like to upgrade to Gutsy Gibbon, but I'm going instead of running regular Ubuntu desktop I'd like to install MythBuntu 7.10.  Here's the steps I think I need to follow for this to work successfully, but I'm hoping you all can review this and let me know if I'm missing something critical.

For some background info, I've got a 500GB hard drive seperated into 2 partitions: a 50GB partition for the OS and myth, and a 450GB partition which is solely for the recordings.  

Step 1: Shutdown myth and backup my mysql database.  

Step 2:  Format partition 1 (the OS, not the recording files) and install MythBuntu 7.10 on top of it.  

Step 3: restore the mysql DB file.  

Since the DB holds all of my settings, once I restore it I should be good to go, right?  Or will the new MythBuntu console force me to go through and re-setup everything?  I'm an experienced Myth user but would be brand new to MythBuntu.  Please let me know if you see any holes or problems with this plan of attack, thanks!!

---

### Post by majoridiot on 2008-02-26
your plan of attack looks sound to me- and i've done the exact thing many times with no problems.
just make sure to note your NEW mysql password, so myth will be able to access the db.

once mythbuntu is installed, you can skip any backend configuration and the mythdatabase fill.  once
everything is installed and rebooted, drop the (pretty much empty) mythconverg, restore your 
backup, restart the backend and you should be good to go.

---

### Post by eagle63 on 2008-02-26
Thanks - one more question:  There's probably a good chance that the version of Myth on MythBuntu 7.10 is higher than the current version I'm on.  How will it handle any potential DB upgrades?  If I install MythBuntu, then restore my old DB, I've now missed out on any data migration/upgrade scripts right?  

Hmmm, I may need to rethink this a bit...

---

