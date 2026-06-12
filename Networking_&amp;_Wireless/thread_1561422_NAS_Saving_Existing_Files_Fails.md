---
title: "NAS Saving Existing Files Fails"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by chrisj802 on 2010-08-26
I have a really nuisance problem.
I have two NAS servers - different makes - both of which work perfectly under Windows XP. I can write new files, save existing files without error. Both servers have drives formatted to FAT32 - the only option - although the OS's are almost certainly an embedded Linux.
Both units are recognized by Ubuntu 10.04 - and I can write new files to them both without problem (although the directory does not refresh - I have to reload it).
I can also delete without problems. If I try and save over an existing file I get an error "Unexpected error: Invalid argument" - I presume the implied delete is failing but  am not sure.
New files also seem to be saved with the Read Only flag set.
OK - I can work round the problem by deleting the files (that works OK) and saving them anew. Works fine - but a backup is impossible as any changed file will give rise to the error.

Any ideas please?

(I have tucked both drives into the hosts files in /etc - although I attach by IP address (which is fixed) anyway.

---

### Post by Morbius1 on 2010-08-26
> If I try and save over an existing file I get an error "Unexpected error: Invalid argument"Are you getting that error in gedit?

There is a very old bug concerning that which should have been fixed already but ..... 

Try using something like leafpad and see if the problem persists.

---

### Post by chrisj802 on 2010-08-26
In gedit and everywhere else. A simple file copy in Nautilus from the Ubuntu machine to the NAS server falls over if the file exists.
I have just tried a live copy of Ubuntu 9.10. Same problem.

---

### Post by chrisj802 on 2010-08-26
This is a Gnome problem.
Having tried just about everything else I came across the references to .gvfs (the Gnome Virtual Filing System) which all said there were not any (maybe they meant many) problems.  So I switched to KDE, which I have on my machine, and lo and behold I can copy and overwrite files on my NAS drives.  Looks like I am going to have to be a Kubuntu person from now on!

---

