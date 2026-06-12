---
title: "All my recordings disappeared"
date: 2007-12-16
forum: Mythbuntu
---

### Post by butthash on 2007-12-16
So I had a bunch of stuff recorded. I was working on setting up the Volume Knob on Antec Fusion [http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion](http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion).

Then I noticed that all my recordings were gone. I don't think working on the volume knob had anything to do it, but who knows.

I checked the disk and they are really gone.

Anyone have this happen before?

---

### Post by butthash on 2007-12-18
Ok, so my recordings are still disappearing. Looks like they just delete themselves after a day. But I have them set to not auto expire, and they are still deleting themselves. I have over 400 gigs of free space left. Is there another setting that I am missing that makes this happen.

---

### Post by butthash on 2007-12-18
When I made my last post, I know a show I had recorded at 8:00pm last night was gone by 7:00am this morning. The only things that were left on my machine where shows from early this morning. Now in the 30 mins since my last post even those are gone and I have no recordings left.

Why would mythtv record something only to delete in a matter of hours later?

---

### Post by mjezell on 2007-12-18
I had something similar happen after we lost power several times the day before.  I had to go into the database using "phpmyadmin" and repair the tables.  Once that was done the recording were back.  Hope this helps.

---

### Post by butthash on 2007-12-18
I haven't shutdown the machine or anything. I checked the disk and the recordings really are just not there. It appears as if mythtv deleted them on purpose as they still show up under previously recorded shows. I checked all the logs in /var/log/mythv but couldn't find anything about deleting programs. Where does mythtv log what and why it is deleting?

---

### Post by majoridiot on 2007-12-18
configure the backend init script to log autoexpires:

```
$ sudo nano /etc/init.d/mythtv-backend
```

near the top, add **--printexpire** to the **"ARGS="** line, so it looks like this:

```
ARGS="--daemon --logfile /var/log/mythtv/mythbackend.log --pidfile $RUNDIR/$NAME.pid --printexpire"
```

that should log the deletions, if the backend is autoexpiring your recordings.

in the meantime, i recommend installing phpmyadmin to see if tables need repairing:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty#head-8bacc34bbec1a2dcd2cc4e54ad86209e04fe37c5](https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty#head-8bacc34bbec1a2dcd2cc4e54ad86209e04fe37c5)

if there are tabes that need repaired, make sure to go back and double-check the autoexpire settings in frontend setup after the repair.

also, make sure you have the MYSQL optimization options set in mythbuntu control centre advanced settings.

if all else fails, you can always add **--noautoexpire** to the ARGS list in the init script, which will prevent the autoexpire thread from being launched.  if you do this, you will need to manually delete any unwanted recordings **including** livetv recordings.

---

### Post by butthash on 2007-12-18
It appears that adding the --printexpire to the args just causes mythbackend to print what will be auto expiring, and not actually start the backend. 


michael@myth:/etc/init.d$ mythbackend --printexpire
2007-12-18 22:36:08.327 Using runtime prefix = /usr
2007-12-18 22:36:08.336 New DB connection, total: 1
2007-12-18 22:36:08.340 Connected to database 'mythconverg' at host: localhost
2007-12-18 22:36:08.342 Current Schema Version: 1160
2007-12-18 22:36:08.344 New DB connection, total: 2
2007-12-18 22:36:08.344 Connected to database 'mythconverg' at host: localhost
MythTV AutoExpire List (programs listed in order of expiration)
New Yankee Workshop: "Taunton Chest"      470MiB  Tue Dec 18 14:00:00 2007 [  0]


I'm still looking for a way to track why mythtv deletes something. Or maybe there is a setting that I am missing that allows mythtv to delete something hours after recording it. I have plenty of disk space so it shouldn't be auto expiring anything anyways.

---

### Post by butthash on 2007-12-18
Also I did a check and no tables need to be repaired.  This must be something set when the system is first created. After I had this problem the first time I reinstalled Mythbuntu and had the same issue again.

---

### Post by majoridiot on 2007-12-19
did you check frontend setup: tvsettings-->general-->autoexpire 
and make sure extra disk space is set to 0?

---

### Post by dannyboy79 on 2007-12-19
are you positive that your recording directory is set correctly and a partition with ample space is being mounted there? almost sounds like your recordings are being deleted to make room for new recordings. look at the following commands:

mount

sudo fdisk -l

and make sure there's ample space for your recording folders mount point.

---

### Post by butthash on 2007-12-19
I have extra disk space set to 50 gigs, but I have a 500 gig drive with lots of extra space

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G   37G  394G   9% /
varrun               1008M  204K 1007M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   76K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile


```

This is just the standard mytbuntu filesystem setup.

---

### Post by dannyboy79 on 2007-12-19
and what is your recording folder? is it the standard folder? It doesn't appear like what I thought the problem could be from so I am not sure what to tell you. If your tables are all ok, and your scheduling options have the "don't auto-expire" thingy checked you should be ok. This is weird. There's nothing in the logs anywhere? /var/log/myth........?

---

### Post by majoridiot on 2007-12-19
> **butthash said:**
> I have extra disk space set to 50 gigs, but I have a 500 gig drive with lots of extra space...  This is just the standard mytbuntu filesystem setup.

that list has little to do with how your myth drive is partitioned, which is what it sounds like the problem could be
and is what dannyboy and i are getting at here...

for example,  in the "typical" mythbuntu installation you say you have,  if you followed the offical communtity guide, you
should have set up 3 partitions- root, swap and /var/lib which holds the recording directory.  if the drive was properly
formatted at set-up, then root will be 15-40 gigs or so (depending on your preference), swap is nominal and the
remaining space is allocated to /var/lib.

however, if you did not take time to carefully allocate the space at format, then you could be "running out of room"
with plenty of space left on the disk, which is a common mistake when setting up mythtv for the first time.  if you 
breeze through partitioning without paying close attention, it is easy to end up with a smaller root parition, a swap and
the remainder allocated as home.

if this is the case, then the bulk of your 500 gigs is allocated to the wrong directory- and since you are reserving
an extra 50 gigs, mythtv would think it is running out of space- because /var/lib is located in the root partition in a
"normal" linux partitioning scheme.

at this point, i suggest using qparted (or equivalent of your choice) to examine your partitions- paying special attention
to the size of whichever partition holds /var/lib (since this is the "standard" mythtv recording directory).  if the size of your
recording partition- minus the 50 gigs you are reserving- winds up being too small, then you have found your problem-
which is what it feels like to me.

if this is the case, then removing the 50 gig reserve will temporarily help.  once we determine how your drive is
partitioned and how the backend is configured, we can help you work out the changes needed to fix things without the 
need for a reformat or re-install.

please post the partitions, mount points and sizes of your mythtv drive per qparted and the location of your recording
directory-  per mythbackend setup.

also, don't forget that while we are helping you fix this, you can add **--noautoexpire** to the ARGS list in the mythbackend 
init script to temporarily halt all autoexpires and keep the shows you are currently recording but losing.

---

### Post by Furry_Fighter_20x66 on 2007-12-19
> **butthash said:**
> So I had a bunch of stuff recorded. I was working on setting up the Volume Knob on Antec Fusion [http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion](http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion).

Then I noticed that all my recordings were gone. I don't think working on the volume knob had anything to do it, but who knows.

I checked the disk and they are really gone.

Anyone have this happen before?

Have you got mythweb (port 80) exposed to the internet without a password? If so a search engine web crawler can come along and access your mythtv following all the links on each page including the ones that delete recordings.

---

### Post by butthash on 2007-12-19
> **Furry_Fighter_20x66 said:**
> Have you got mythweb (port 80) exposed to the internet without a password? If so a search engine web crawler can come along and access your mythtv following all the links on each page including the ones that delete recordings.

I would never have thought of that. But it looks like that is the problem. I didn't even know that mythweb was setup by default. And I had the mythtv box sitting behind a router. I use to have a webserver going that I forwarded port 80 to. I never took the forward off and by chance the mythtv box picked up the same ip address from DHCP as the old webserver.

Thanks for the idea.

---

### Post by dannyboy79 on 2007-12-21
mythweb is NOT set up by default. At least it wasn't for me on mythbuntu or feisty synaptic mythtv  packages. you can always check by issuing the following command

sudo aptitude show mythweb


if it shows 
State: not installed

than it's not installed.

It's either a database problem or a partition/mount point issue. I am not entirely sure how to do it, but have to tried recreating the mythconverg database?

---

### Post by butthash on 2007-12-24
Mythweb was setup by default. I added some security to Mythweb and I haven't had any problems since.

---

