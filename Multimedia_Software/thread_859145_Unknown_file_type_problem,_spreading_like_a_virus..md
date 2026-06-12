---
title: "Unknown file type problem, spreading like a virus... very irritating."
date: 2008-07-14
forum: Multimedia Software
---

### Post by rogue2501 on 2008-07-14
ubuntu 7.10

hey all, had a problem come up recently.  i have a few avi files in question which are messed up for some reason, and i cant find a solution.

so basically, the avi files are on an external hard disk, one day, plug it in, and one of the files changes.  all the information had changed, and it cannot be deleted, or anything.  when selecting properties, the following information is displayed:

Basic tab
Name:  xxx.avi
Type: unknown type
Size: unknown
Location /media/disk-1/
MIME type:  application/octet-stream
Modified:  unknown
Accessed:  unknown

Permissions tab
The permissions of “xxx.avi” could not be determined.

even navigating to the files, using gksudo nautilus, try to delete and the file only disappears, but comes back everytime the device is plugged back in.

so i was like, ok one file, whatever.  than it started spreading to other files.  same thing, so 2 other files are now unplayable with the same problem.  upon research there had been postings about changing things in the mime section.  tried that, didnt work.  so, out of panic, well whenever their is panic, transfered everything off the main pc, reinstalled ubuntu fresh.  now everything works great, the spreading has stopped.  BUT those same files STILL have the same problem.

so, please let me know, how do i like hard force deletion of files.  i have already reacquired the files that are in question, so the broken ones i do not need anymore.

thank you for the help, much appreciated!

ps.  or if they can be recovered, that would be cool too.  :)

---

### Post by xc3RnbFO8P on 2008-07-14
Try to open it with Avidemux.
Maybe your HDD is taking the last gasp.

---

### Post by Vivaldi Gloria on 2008-07-14
Open a terminal, use

cd pathname

to go to their folder. Use "ls" or "ls -a" to see the contents if you want. Now you can forcibly delete a file with

```
sudo rm -f filename
```

or 

```
sudo shred -fu filename
```

But there is no recovery possible after these. You are warned!

The first one deletes the file. The second one not only deletes it but also writes zeros on it.

---

### Post by rogue2501 on 2008-07-15
great!  thanks for the posts i will try those options out tonight.  actually, one thing i didnt mention, was at the same time as this issue occured, ALL of my avi files become unplayable regardless of location, ie, ext harddisk, etc.  unplayable in the sense that double clicking i was met with an error, but when manually drag and dropping they all worked fine.  again, in this regard, i looked into the issue, apparently has happened to others, something with mime settings.  tried to solve it, didnt work, got frustrated, formated and now everything works great again.  its just those 3 files that the damage seems permanent.  

will be trying avidemux tonight, and if not, hard delete them.  i hope that works.  fingers crossed.  lol.

---

### Post by lukjad on 2008-07-15
Did you install/Uninstall anything?

---

