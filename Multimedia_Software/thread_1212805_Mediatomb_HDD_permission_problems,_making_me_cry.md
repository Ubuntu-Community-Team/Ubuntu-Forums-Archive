---
title: "Mediatomb: HDD permission problems, making me cry"
date: 2009-07-14
forum: Multimedia Software
---

### Post by oxymoron on 2009-07-14
Hello,

Well 12 months on and another attempt at a linux homeserver! The only barrier now is mediatomb!!

I am having a real headache with permissions. I have mounted 2 hdd to mnt/storage1 and /mnt/storage2/

I have added them to fstab:

```
/dev/sda1       /mnt/storage1   ext3    users,auto,rw 0 0
/dev/sdb1       /mnt/storage2   ext3    users,auto,rw 0 0
```

I have created a group in etc/groups called media_write and added users "dean" and "mediatomb".

I have then run:

sudo chgrp media_write /mnt/storage1

sudo chmod 770 /mnt/storage1 -R

Now mediatomb will parse most folders within /mnt/storage1/TV/ but not all!!!

I cannot understand this at all. The amount of man hours I have lost to this stupid program!! May have to dust of my comp of XP at this rate!! (Deep breathes, staying calm :p)

What am I doing wrong?

EDIT: just made the permissions on the remaining folder that dont work 777 and now they parse data!! What permissions does mediatomb need on each folder inorder to add to database?

How do I also set each created file to have the correct permissions?

---

### Post by amak79 on 2009-07-19
> **oxymoron said:**
> What am I doing wrong?

EDIT: just made the permissions on the remaining folder that dont work 777 and now they parse data!!

Changing the permissions to 777 from 770 indicates that the **/mnt/storage1/TV** directory doesn't have the correct group ownership i.e. not owned by the **media_write** group.

Although you did run **chgrp** on **/mnt/storage1** it appears that you didn't run it with the -R (recursive) option. To correct this, change the permissions back to 770 and then run:

sudo chgrp **-R** media_write /mnt/storage1

> **oxymoron said:**
> What permissions does mediatomb need on each folder inorder to add to database?

MediaTomb only needs read permission.

> **oxymoron said:**
> How do I also set each created file to have the correct permissions

The default permissions are determined by the umask which on Ubuntu is 022. This will result in 644 permissions for files and 755 for directories. The system wide umask is set in /etc/profile but I strongly advise against changing it as it will affect all users. Users can safely override the system wide umask in ~/.bash_profile.

---

