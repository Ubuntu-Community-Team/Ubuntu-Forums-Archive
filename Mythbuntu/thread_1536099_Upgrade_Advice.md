---
title: "Upgrade Advice"
date: 2010-07-21
forum: Mythbuntu
---

### Post by Tteddo on 2010-07-21
So, I will have the parts this weekend to build a new MythBuntu box. My questions is as follows: I currently am running MythTV .21 (on Mythbuntu 8.04 as seen here ([http://ubuntuforums.org/showthread.php?t=1471186]("http://ubuntuforums.org/showthread.php?t=1471186")) and I want to preserve the recordings. I don't really care about the schedule as I am switching to a new digital card and all the stations will be different anyway.
So as I see it there are 2 ways to do this, the preferable way is to install Mythbuntu on the new machine, then restore the old database from the backup I make every night. Then do some voodoo like reinstall the MythTV packages so Mythbuntu will update the database to the new version.
The other way I can think of is to install Lucid then install the packages as seen in the previous post, restore the backup, then allow the update manage to update them. The downside to this is I am not using the whole MythBuntu install. Anyone have some input on this? I would really appreciate it!

---

### Post by tgm4883 on 2010-07-21
I would Install, restore DB, run mythtv-setup to set up your new stuff (in the process I believe it will upgrade your db) then you should be fine.

---

### Post by Tteddo on 2010-07-21
Install MythBuntu? That would be great. I'll report back on how it goes.

---

### Post by newlinux on 2010-07-22
I went from 8.04 to a fresh install of 10.04 on my master backend a couple of months ago (and an in place upgrade on many of my secondary backends). I just installed a fresh copy of ubuntu, installed mythtv (if you are install mythbuntu this happens automatically), restored the database, and then ran mythtv-setup to make changes to things in the new system and all was well. So just as tgm4883 describes...

---

### Post by Tteddo on 2010-07-22
> **newlinux said:**
> I went from 8.04 to a fresh install of 10.04 on my master backend a couple of months ago (and an in place upgrade on many of my secondary backends). I just installed a fresh copy of ubuntu, installed mythtv (if you are install mythbuntu this happens automatically), restored the database, and then ran mythtv-setup to make changes to things in the new system and all was well. So just as tgm4883 describes...

Ok! Wish me luck!

---

### Post by newlinux on 2010-07-22
Good luck and we're here to help

---

