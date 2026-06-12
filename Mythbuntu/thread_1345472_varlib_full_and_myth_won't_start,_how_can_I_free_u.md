---
title: "/var/lib full and myth won't start, how can I free up space?"
date: 2009-12-04
forum: Mythbuntu
---

### Post by bglaze1 on 2009-12-04
I am getting an error when I boot up my mythbox that says:
"GDM could not write a new authorization entry to disk.  Possibly out of diskspace.  Error: No space left on device."
Then it sats that it "Could not start X server...check your syslog to diagnose....restart GDM when the problem is resolved."

This then just hangs and won't let me get to a command line.  If I boot up in the recovery mode I can get to a command line.
From what I can tell it looks like my /var/lib is full (I did a df -h and it was 100%).  I can't start myth to delete files, so I am stuck.  Is there a way I can recover this, or am I just out of luck?  Please any help you can give would be greatly appreciated. I have some big log files (in /var/log/mythtv) that I tried to delete, it didn't seem to free up any space.  I guess those are not on that partition though.  
Can I delete a file from /var/lib/mythtv/recordings to free up some space so it will at least let me boot myth again?  Or is that not a good idea?

---

### Post by t3chn0b0y on 2009-12-04
> **bglaze1 said:**
> I am getting an error when I boot up my mythbox that says:
"GDM could not write a new authorization entry to disk.  Possibly out of diskspace.  Error: No space left on device."
Then it sats that it "Could not start X server...check your syslog to diagnose....restart GDM when the problem is resolved."

This then just hangs and won't let me get to a command line.  If I boot up in the recovery mode I can get to a command line.
From what I can tell it looks like my /var/lib is full (I did a df -h and it was 100%).  I can't start myth to delete files, so I am stuck.  Is there a way I can recover this, or am I just out of luck?  Please any help you can give would be greatly appreciated. I have some big log files (in /var/log/mythtv) that I tried to delete, it didn't seem to free up any space.  I guess those are not on that partition though.  
Can I delete a file from /var/lib/mythtv/recordings to free up some space so it will at least let me boot myth again?  Or is that not a good idea?


The best thing to do is not get into this situation.. But what has been done, has been done... now to try to get you out of it.

In the setup you need to set the "Extra Disk Space" parameter.
Give yourself at least a gig of space to work with.. If at all
possible dont put your videos on the same partition or hard drive
as your recordings, that will stop this from ever happening.

At the boot screen see if you can't login safe mood
and go into the /var/mythtv/recordings and delete a video or two,
and do a reboot, this should give the system enough space to write
it's files..

There is a great program in the universe called bleachbit, its a
great little app for cleaning out unnecessary garbage..

but for the time being lets get ya back into the system..
and I highly recommend another drive/partition for the recordings.
its better safe then sorry..  It has happened to me too..

---

### Post by SiHa on 2009-12-04
When in the recovery mode, you can happily delete recordings from /var/lib/mythtv recordings, as Techno has stated.

This will, however, leave them still in the database, and in the recordings list. Myth will not allow you to delete the entry from the recordings list if the file isn't present.

To do it cleanly, I would suggest after deleting that you replace with zero-size files:```
$ rm [filename]
$ touch [filename]
```

At the recovery prompt you are root, so the file will be owned by root. In order that Myth can delete them, you probably will need to change the permissions```
$ chmod 666 [filename]
```

---

### Post by klc5555 on 2009-12-04
> **bglaze1 said:**
> I am getting an error when I boot up my mythbox that says:
"GDM could not write a new authorization entry to disk.  Possibly out of diskspace.  Error: No space left on device."
Then it sats that it "Could not start X server...check your syslog to diagnose....restart GDM when the problem is resolved."

This then just hangs and won't let me get to a command line.  If I boot up in the recovery mode I can get to a command line.
From what I can tell it looks like my /var/lib is full (I did a df -h and it was 100%).  I can't start myth to delete files, so I am stuck.  Is there a way I can recover this, or am I just out of luck?  Please any help you can give would be greatly appreciated. I have some big log files (in /var/log/mythtv) that I tried to delete, it didn't seem to free up any space.  I guess those are not on that partition though.  
Can I delete a file from /var/lib/mythtv/recordings to free up some space so it will at least let me boot myth again?  Or is that not a good idea?

If you can get to a command line, find a sacrificial recording under /var/lib/mythtv/recordings and nuke it. Even a half-hour SD recording will free up half a Gig, which should be more than plenty to allow the machine to boot. Then you can commence maintenance in a more normal fashion. This should work fine. Of course, the metadata for the recording that is no longer there can easily be deleted from the frontend once myth is starting normally.

If you can't get to a prompt, boot off the CD and mount the offending partition under something like /mnt, and again divest yourself of a sacrificial recording.

---

