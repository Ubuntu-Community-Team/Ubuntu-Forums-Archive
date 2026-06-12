---
title: "AutoUpgrade to 8.04 not gone too well"
date: 2008-05-03
forum: Mythbuntu
---

### Post by nunrgguy on 2008-05-03
Broken so far:
Database connection
All file permissions reset to default rather than my custom ones
Bittorrent no longer working
Bittornado no longer working
xmltv not working
Database reset and doesn't find previous recordings
Old password compatability gone so cannot connect from xbox frontend
Nautilus not working

See what else I can find as I delve deeper...

---

### Post by kreegor on 2008-05-03
Hmmm that really sucks. The only thing that 'broke' with my 8.04 upgrade was the Mythbuntu loading screen doesn't come up anymore and instead I have

```

* Starting up something          [OK]
* Starting up something else     [OK]
* etc etc                        [OK]

```

Is there anyway to get back the normal loading screen instead of having lines and lines of the above?

Edit: This comes up before the MythBuntu splash screen and after the GRUB menu.

Solved: I ended up editing the /boot/grub/menu.lst file and uncommented the splash line. :)

---

### Post by nunrgguy on 2008-05-04
Right
Those problems are now semi-fixed, mainly permissions issues.
xbox user access rights to mythconverg were reset - had to change
folder permissions on music/recordings etc in var/lib/mythtv all reset - had to change
Folder permissions in user/.xmltv all reset - had to change
Bittorrent and the other one - seems to be some kind of xePython problem. Why?
Sacked them off and gone to Azeurius anyway.
Managed to pull xmltv listings for the first time in absolutely ages so actually some progress there but still getting the error I've posted elsewhere that no-one seems to know about, namely:
ICE default error handler doing an exit (), pid 6452 errno = 32
which occurs after DataDirect: Deleting temporary files 

Another permissions problem on a temp dir somewhere?

Why the upgrade needs to change all your file permissions I don't know but it's a bit of a pain to be sure.

---

