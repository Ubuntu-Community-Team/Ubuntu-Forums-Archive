---
title: "Repair (Rebuilding) Mythtv database"
date: 2013-03-13
forum: Mythbuntu
---

### Post by Ubu_Fester on 2013-03-13
Hi,
My mythtv video recordings are stored in two separate drives:
  drive 1:  (~600GB) volume:  /var/lib/mythtv/recordings2
  drive 2:  (~1.4TB) volume:  /var/lib/mythtv/recordings3

Last week, drive 2 HDD crashed, so I replaced that drive with a new 2TB drive and replicated the volume structure.  Basically, I now have a new empty /var/lib/mythtv/recordings3 volume up and running.

How does Mythtv manage that one day X number of recordings exist on ../recordings3 volume and the next day zero recordings are on ../recordings3 volume?

Do I need to run a script to fix the new, smaller listing of recordings?

Also, if in the future I happen to recover some recordings from the old drive, is there a way to put them back in the mythtv database? 

Thanks in advance!

---

### Post by klc5555 on 2013-03-14
> **Ubu_Fester said:**
> Hi,
My mythtv video recordings are stored in two separate drives:
  drive 1:  (~600GB) volume:  /var/lib/mythtv/recordings2
  drive 2:  (~1.4TB) volume:  /var/lib/mythtv/recordings3

Last week, drive 2 HDD crashed, so I replaced that drive with a new 2TB drive and replicated the volume structure.  Basically, I now have a new empty /var/lib/mythtv/recordings3 volume up and running.

How does Mythtv manage that one day X number of recordings exist on ../recordings3 volume and the next day zero recordings are on ../recordings3 volume?

Do I need to run a script to fix the new, smaller listing of recordings?

Also, if in the future I happen to recover some recordings from the old drive, is there a way to put them back in the mythtv database? 

Thanks in advance!

You could go into the delete recordings section of "manage recordings" and delete the metadata one-by-one for recordings that the backend reports as missing.

If there are going to be a lot of missing recordings, and if you are still on mythtv 0.25, you may use the find_orphans.py script, whose wiki page is here: [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py)

Nowadays, recordings without metadata (say, recovered from a nuked drive or elsewhere) that one wishes to add to a mythtv installation are supposed to be added to the mythvideo side of the installation. This is not the only possible solution, but it is the only currently supported one. So if you have a real expectation of recovering a lot of recordings from your former recordings drives and dropping these recordings into the new drives, you may wish to hold off purging metadata until this recovery has taken place. If, however, recovering recordings is something that is unlikely to take place, then you may find it less annoying to clean up your metadata either manually or by the script, with the expectation that if a recording here and there is recovered at some point in the future, it will be added to mythvideo.

---

### Post by Ubu_Fester on 2013-03-15
Thanks.  I was able to delete the recordings through the Myth frontend under "manage recordings".  

Thanks!

---

