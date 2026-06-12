---
title: "Samba user permissions problem"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by MrDetermination on 2010-12-30
Hi,

I have a Samba server running on a box where I login to admin as user:
FRED

The Samba users are
SUE
JOE - Read only for specified paths (media playback access only user)

SUE can read/write to any directory under the share: Media

So all that is working fine.  As long as I do file operations remotely as SUE everything works remotely.

**Question**
How can I make it to where everything SUE does over Samba FRED automatically has permissions to edit when logged in locally (or SSH)?  Also, remember, Joe needs to be able to read where specified.

---

### Post by PatchesTheCaveman on 2010-12-30
From the Ubuntu machine, go to System > Administration > Users and Groups.  Click Manage Groups.  Make a group called media_users or whatever you want to call it.  Add JOE and SUE to that group.

Now, right-click on the Media folder, go to Properties, and go to the Permissions tab.  Change the group to media_users and give the group read and write permissions.  Then click *Apply permissions to Enclosed Files*.  That should do what you want.

If you prefer, you can also do all this from the command line:
```
sudo groupadd media_users
sudo usermod -G media_users JOE
sudo usermod -G media_users SUE
chgrp -R media_users Media/
chmod -R g+rwx Media/
```

---

### Post by Morbius1 on 2010-12-30
Whithout knowing how your current share is defined you could just add the following line to the definition:
```
force user = fred
```This will convert SUE to FRED so that when SUE adds a file it will save as owner = FRED.

You could also add the following lines:
```
force group = plugdev
create mode = 664
directory mode = 775

```When SUE adds a file it will save as owner:group = SUE:"plugdev " and permissions of 664 or 775 if it's a directory. By default every local user on the server is a member of the plugdev group.

---

### Post by MrDetermination on 2010-12-30
Thanks!  I'm all set.

---

