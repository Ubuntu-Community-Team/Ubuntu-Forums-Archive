---
title: "User job to move file to different drive?"
date: 2010-08-29
forum: Mythbuntu
---

### Post by JMcFly on 2010-08-29
I've added a second hard drive to my system so my GF and I will each have our own (and Top Chef won't overwrite Sons of Anarchy), each with its own storage group.  But, all of her recordings are currently part of the default (aka my) storage group.  Can I create a simple user job to move those files to the new drive/group?

Is it as simple as telling the backend User Job #1 is "mv %DIR%/%FILE% /Myth2/RecordedTV/" or do I need to write it as a .sh file and call it?

---

### Post by ian dobson on 2010-08-30
Hi,

Can't you just configure the recording job to use a different storage group (Atleast I can see the selection box in Mythweb).

Just moving the recording to a different directory might not be enough. If you've setup a completely new storage group rather than just adding a new directory to an existing storage group, you'll also need to update the database table recorded so that the entry in the table points to the new storage group.

A it of bash/mysql should do it.

Regards
Ian Dobson

---

### Post by JMcFly on 2010-08-30
Wouldn't changing the storage group in the recording settings only affect future recordings? There are ~200 shows I'd like to move.

---

### Post by ian dobson on 2010-08-30
Hi,

Yes, changing the storage group for the recordings will only effect future recordings.

Did you create a new storage group or just append the new directory to the default storage group? (Default -> /dir1:/dir2).

If you just added a new directory to the existing storage group then you can just move the file, if you created a new storage group then you'll have to update the recorded table aswell when moving the recordings.

Regards
Ian Dobson

---

### Post by LowSky on 2010-08-30
take a look at this it should help

[http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

---

### Post by JMcFly on 2010-08-30
That's a solution for someone looking to move all of their recordings. We have about ~500 total with ~200 of them we'd like to move to the new drive but they're intermixed with the other ~300 so a user job sounds like the best way to do it.

---

