---
title: "clementine music player suffers from amnesia part 2"
date: 2018-01-26
forum: Multimedia Software
---

### Post by hannabanana on 2018-01-26
Hi friends

I have the exact same issue as this old thread: [https://ubuntuforums.org/showthread.php?t=2175029](https://ubuntuforums.org/showthread.php?t=2175029)

Have tried with ext4 format and ntfs . When i add the folder on the local hdd (not OS disk) clementine scans,find and add all files to the library, allright.

After restart, the library is empty and i have to start over..:mad:

The folder is set to be read, changed and accessed by "everyone" . It´s an internal hdd and changing the folder to local:      home/music , makes clementine remember ?

Please have in mind that i am a new user;)

By the way, i´m on Lubuntu 17.10 and clementine version 1.3.1 . My music HDD is a wd green

Thanks in advance

---

### Post by Holger_Gehrke on 2018-01-28
Is the hard disk mounted on start-up ? I'm asking because I have my Clementine library on an external HD and if I start Clementine without the HD connected I get the same situation. Closing Clementine, connecting the HD (or mounting if it was plugged in but not mounted) and restarting Clementine fixes things on my system (the library is in an sqlite3 database, missing files are not removed from the db,so things like ratings -- which are normally stored in the db, not in the files -- don't get lost ).

Holger

---

### Post by hannabanana on 2018-01-31
Hello Holger

I found out that my local sata hdd was not set to automount at startup in lubuntu disk settings

It works now :-)

---

