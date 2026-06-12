---
title: "Can not delete recorded programmes"
date: 2012-02-05
forum: Mythbuntu
---

### Post by Billsputters on 2012-02-05
As the title says, I can't delete any programmes, and I've a 2GB drive full of stuff, some of which has to go.

I also can not watch any recorded programmes either, mythtv just stays in the programmes recorded list after a short while.

Been through many posts, and tried all the suggested solutions but getting nowhere fast.

---

### Post by nickrout on 2012-02-06
2G is nowhere near enough as most stuff will be in the order of 2G/hr minimum.

The rest sounds like permissions problems, but as you don't include any logs it is hard to say.

---

### Post by Billsputters on 2012-02-07
Doh! I did of course mean 2TB!

OK, backend logs as at ```

[http://pastebin.com/5VY8XGFj]("http://pastebin.com/5VY8XGFj")

```

Rights for the files are as follows

```
-rw-rw-rw- 1 mythtv mythtv   375467960 2011-01-05 17:30 2206_20110105170900.mpg
-rw-rw-rw- 1 mythtv mythtv       10498 2011-03-04 18:27 2206_20110105170900.mpg.64.100x75.png
-rw-rw-rw- 1 mythtv mythtv       55631 2011-01-05 17:41 2206_20110105170900.mpg.png

```

Which looks right to me. As an aside, I can't fathom out that if MythTV can record and playback a file, it must have the rights set correctly.

---

### Post by klc5555 on 2012-02-07
You say some stuff "has to go". How full is your root partition? If the command "df -h" shows your root partition has maxed out at 100%, then all kinds of odd errors will have begun to pop up and file corruption may have happened. mythconverg in particular. If you're unfortunately running a single-disk, single-partition system where /var/lib/mythtv/recordings (or whatever your recording directory is) is in the root partition, then maxing out the partition is particularly easy.

---

### Post by Billsputters on 2012-02-07
Root is grand

```
richard-be@mythtvbe:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  5.1G   13G  30% /
none                  1.9G  804K  1.9G   1% /dev
none                  2.0G  1.3M  2.0G   1% /dev/shm
none                  2.0G  388K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda7              78G  4.9G   69G   7% /home
/dev/sdb1             1.8T  1.4T  354G  80% /data
/dev/sdc1             1.9T  1.9T   20K 100% /mythtv
/dev/sda5              37G  280M   35G   1% /boot

```

Two discs are used for MytvTV, sdb1 and sdc1, one for films and music, other for recordings.

The stuff that has to go is old recordings that have been watched. Been away on holidays, and could quite happilly use MythWeb to set recordings, thinking that the old expired recordings would be deleted to make way for newer stuff. All I managed to do was fill the disk!

---

### Post by nickrout on 2012-02-07
Don't forget the backend runs as mythtv whereas the frontend runs as your desktop user. Does the desktop user have permission to delete?

---

### Post by Billsputters on 2012-02-07
OK, so I have a backend and two frontends, one being a laptop I use occassionally for that purpose.

These are programmes that have expired, or have been marked for deletion. I would have thought that the front end informs the backend to mark file x for deletion, rather than just doing it itself. Let the backend look after housekeeping and keep database up to date.

I can mark them for deletion in MythWeb as well, but nothing happens

---

### Post by nickrout on 2012-02-07
> **Billsputters said:**
> OK, so I have a backend and two frontends, one being a laptop I use occassionally for that purpose.

These are programmes that have expired, or have been marked for deletion. I would have thought that the front end informs the backend to mark file x for deletion, rather than just doing it itself. Let the backend look after housekeeping and keep database up to date.

I can mark them for deletion in MythWeb as well, but nothing happens

yes I think you may be right about how they are deleted.

There is a setting which doesn't ACTUALLY delete files you tell the system to delete, it puts themm in the deleted group, and only physically deletes them when you have run out of space. This is great if you (or family members) are too handy with the delete button - you can get the files back.

Do you have this set, and does it explain the behaviour you are seeing?

---

### Post by klc5555 on 2012-02-08
> **Billsputters said:**
> Root is grand

```
richard-be@mythtvbe:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  5.1G   13G  30% /
none                  1.9G  804K  1.9G   1% /dev
none                  2.0G  1.3M  2.0G   1% /dev/shm
none                  2.0G  388K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda7              78G  4.9G   69G   7% /home
/dev/sdb1             1.8T  1.4T  354G  80% /data
/dev/sdc1             1.9T  1.9T   20K 100% /mythtv
/dev/sda5              37G  280M   35G   1% /boot

```

Two discs are used for MytvTV, sdb1 and sdc1, one for films and music, other for recordings.

The stuff that has to go is old recordings that have been watched. Been away on holidays, and could quite happilly use MythWeb to set recordings, thinking that the old expired recordings would be deleted to make way for newer stuff. All I managed to do was fill the disk!

Having set the backend to do true file deletes rather than just expiring, try to delete a program from the frontend (not mythweb) and see what the results are. If the program listing seems to disappear for a couple of seconds, then reappears, the backend can't access the maxed out storage disk properly. The owner/group/permissions may have got messed up at the disk's directory mount point. Which seems to happen fairly frequently -to me at least- on dedicated storage disks after, say, a dirty shutdown/reboot after power glitches: at reboot the storage disks end up mounted as "root-root" again instead of "mythtv-mythtv".

 Or you may need to delete one or two recordings files manually from a prompt to make a bit of space on the disk for applications to work with, then proceed to delete programs away from the frontend program listings.

---

