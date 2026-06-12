---
title: "How to point the backend to a storage directory on a second hard drive"
date: 2014-08-03
forum: Mythbuntu
---

### Post by dylansob on 2014-08-03
Hi,

Sorry for the freshman question, but I'm just moving over from OSX to Mythbuntu and I'm kinda stuck.  I have Mythbuntu installed.  I want to move my storage groups to a second hard drive on my computer.  I guess I don't know the proper structure to where this drive is on Ubuntu.  On a mac it would be:  volumes/pvr/mythtv/recording.

This is the folder structure I am trying to point the backend to:  /pvr/mythtv/recordings.  Pvr is the name of my hard drive that I can see on the desktop.  When I try to assign that directory in the backend under storage directories, it tells me the directory doesn't exist.

Any help would greatly be appreciated.

---

### Post by ajgreeny on 2014-08-03
It will probably be in **/media/*username*/pvr** but without knowing more it's difficult to be certain.

Is the disk mounted automatically at boot?
 to what filesystem is it formatted, ext, ntfs, hfs+?
 do you have permission to write to that folder in the filesystem?

Let's have a lot more info please.

---

### Post by dylansob on 2014-08-04
Hi ajgreeny,

You are correct, the drive is mounted:  /media/username/pvr.  It is formatted in ext and I'm running Ubuntu 14.04 (most current, I believe).

I think it must be permissions, I can access it on my desktop without any problems.

Any help with permissions would be greatly appreciated.

Cheers.

---

### Post by Gillingham on 2014-08-04
Yes it sounds like a permission problem, I've just looked at mine I've changed the group the directory belongs to to mythtv for both the storage directories I use (one I'm the owner of and the other mythtv is but they both work).

So as a result when I run ```
ls -l /media
``` for the two mythtv directories I get:
```

drwxrwxr-x   3 mythtv mythtv 57344 Aug  4 17:18 mythtv
drwxrwxrwx   3 david  mythtv   127 Aug  3 21:34 sda3

```

As a note I've read elsewhere that mythtv is sometimes sensitive to the permissions of the mount point itself

---

### Post by dylansob on 2014-08-05
When I type ls -l /media, I get:

total 4
drwxr -x---+ 3 root root 4096 Aug 5 13:37 mythbuntu

So I don't think I'm seeing the drive.  I have 3 hard drives and one DVD in my system.  I can access everything from the desktop without issue.

If I call up the disks application, I see my drive and under Device it says: /dev/sdc1 and under contents, it says Ext4(version 1.0) mounted at /Media/mythbuntu/pvr.

So I'm very confused.  If it's permissions, I don't know how to set it.  I've gone all over google, and there are too many options.  I'm just learning Ubuntu and the frustration is driving me insane.  As far as the mount point, I'm not sure how to identify that, I thought it was /media/mythbuntu/pvr?

---

### Post by dylansob on 2014-08-05
Ok, so I got past some of my newbie stupidity.

When I use ls -l /media/ubuntu/pvr (which is my drive I want Mythtv to use for recording) I get:
drwx------    2 root          root              16384 Aug     5 12:50  lost+found
drwxrwxrwx 4 mythbuntu mythbuntu       4096 Aug     5 13:04  Mythtv

So I'm not sure what those permissions mean, but at least I know where the mount point is.

---

### Post by Gillingham on 2014-08-06
OK - I suggest you read up on the permissions e.g. such as a tutorial [http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions]("http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions"), as I'm not sure I'll explain it properly.

Each file has an owner and a group (a collection of users), in your case the directory belongs to mythbuntu and belongs to the group mythbuntu.  Now mythtv has a group of its own (in case it needs to be run by several users) which is called mythtv.  

The permissions are r read access w write access x execute, and each of the owner, group and everyone can have separate permissions. 

I think what you need to do is make your directory owned by the mythtv group.  This can be done by using the chgrp command
```
chgrp -R mythtv /media/ubuntu/pvr
```
the -R means that this change will be made recursively (i.e. to any files or directories in /media/ubuntu/pvr).  Given that you are the owner you shouldn't need to use sudo to change the group ownership.

Hopefully mythtv will now be happy when you point it to /media/ubuntu/pvr or /media/ubuntu/pvr/Mythtv

David

---

