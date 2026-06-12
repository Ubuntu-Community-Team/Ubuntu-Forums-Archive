---
title: "My Sansa Fuze suddenly turned 'read only'."
date: 2010-07-09
forum: Multimedia Software
---

### Post by Arazu on 2010-07-09
It worked fine with the base install of 10.4 but somewhere along the way it stopped working and became read only.

Autodetect and MTP modes cause only the Fuze to show up in Rhythmbox. However the track numbers are all wrong and some things are garbled. MSC mode, which I used in the past, shows the Fuze and card both in Rhythmbox and on the desktop. However it's in read only mode.

Any thoughts?

---

### Post by wilee-nilee on 2010-07-09
Does the sd card have a little switch on it and is it set to lock.

---

### Post by tekkidd on 2010-07-09
Have you tried formatting the SD card in Gparted and then using slapping it in the Fuse and letting it recreate the filesystem

---

### Post by I8NY on 2010-07-10
i had this problem too, just remount it or replug it in with MSC mode.

update: i now have the same problem too.  It must be spreading, lol.

---

### Post by Chronon on 2010-07-10
UMS devices will commonly be mounted as read-only if the file system is damaged.  Doing a fsck can sometimes find and repair problems that cause this.

---

### Post by Arazu on 2010-07-19
I'm sorry it took me so long to get back to this. I've been too busy with work to play with it.

The file system does appear to be corrupt on the Fuze.

GParted had this to say when I attempted to check it:

[INDENT]GParted 0.5.1

Libparted 2.2
Check and repair file system (fat32) on /dev/sdf1  00:00:00    ( ERROR )
     	
calibrate /dev/sdf1  00:00:00    ( SUCCESS )
     	
path: /dev/sdf1
start: 0
end: 7683071
size: 7683072 (3.66 GiB)
check file system on /dev/sdf1 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
dosfsck -a -w -v /dev/sdf1
     	
dosfsck 3.0.7 (24 Dec 2009)
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
open: No such file or directory

========================================[/INDENT]

I tried resetting the Fuze to factory settings but that didn't help.

I'm at a loss as to what to do now.

I welcome any thoughts you all might have.

---

### Post by Arazu on 2010-07-20
Bump for the morning people. =)

---

### Post by cabbrick1243 on 2011-02-27
You need to reformat the entire device by going to settings>system settings>format.
Just worked for me.

---

### Post by Chronon on 2011-02-28
nvm.

---

### Post by jimasbille on 2012-07-01
Reformatting worked for me as well.

---

