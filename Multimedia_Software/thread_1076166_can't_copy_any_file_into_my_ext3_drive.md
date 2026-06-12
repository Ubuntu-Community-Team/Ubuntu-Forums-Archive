---
title: "can't copy any file into my ext3 drive????"
date: 2009-02-21
forum: Multimedia Software
---

### Post by manuvaidya on 2009-02-21
hi, i recently installed ubuntu ultimate 2.0 on my dell laptop.....
installation went smoothly.... i really like the interface....

but the thing is i cant copy any of the files into my 2 ext3 partitions which are 100gb each apart from the root partition of 20gb which is also ext3 format....

i can copy/paste/extract files onto my desktop but not to my other drives...
when i try copying, it says permission denied.... what should i do now???
i enabled all the permissions for me and tried.. even then it says the same....
what should i do now???? help me pls urgent....:(

---

### Post by chmbrs on 2009-02-21
you need to be root to get access

you can try 

gksu nautilus

 in the terminal

---

### Post by manuvaidya on 2009-02-21
u r the man.... thanks a lot for this wonderful tip... i was very worried about it... u made my day.. was that so simple???? i searched the whole internet...to my surprise, i didnt find it anywhere.....

is there by any chance that i can make that command permanent only for me??? so that i can copy & paste any amount of file into any drive....is that possible???

---

### Post by Thirsteh on 2009-02-21
The easiest way to do that is to make a folder and chown it to your user account. Do something like:
```
sudo mkdir /mnt/myotherdisk/username
sudo chown username:username /mnt/myotherdisk/username
```

Your user account can now create files within that folder.

---

### Post by vanadium on 2009-02-21
I don'think your second suggestion is correct. "users" specifies that users are allowed to mount the volume, but does not grant them ownership.

Your first recommendation, though, is the way to go: create, as administrator, a directory on the drive and grant permissions to the user.

You can then take that one step further and make the volume readily accessible to the user. You can do this by creating a symlink in the users hom

```

ln -s /mnt/myotherdisk/username ~/data

```

would create a data folder in your home directory (a symbolic link, actually) that immediately takes you to the /mnt/myotherdisk/username folder on your other ext3 drive.

To get ownerschip of the entire disk (partition) you may chown the mount point itself.

---

### Post by Thirsteh on 2009-02-21
> **vanadium said:**
> I don'think your second suggestion is correct. "users" specifies that users are allowed to mount the volume, but does not grant them ownership.

True, thanks for pointing that out :-)

---

