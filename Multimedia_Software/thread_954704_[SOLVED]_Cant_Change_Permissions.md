---
title: "[SOLVED] Cant Change Permissions"
date: 2008-10-21
forum: Multimedia Software
---

### Post by naknak987 on 2008-10-21
I tried using gksudo nautilus to change permissions on some of my audio files from root to naknak987 so I could edit there tags. but nautilus won't let me. Please help.

(not shure if it went here or some were else, I figured I would put it here cause its for audio files. not just one, any that aren't already set for naknak987.)

---

### Post by naknak987 on 2008-10-21
Could someone just tell me how to change permissions for a external drive... everything on the drive and the drive it self. I tried some things from the Ubuntu wiki and documentation that didn't work.

---

### Post by naknak987 on 2008-10-21
*bumb*

---

### Post by vanadium on 2008-10-21
I guess your audio files are on a drive that is formatted with a file system that does not support unix permissions and ownerships. It is therefore normal you cannot change these.

---

### Post by naknak987 on 2008-10-21
Its ntfs and I had full permissions for it before last week. Probably because I had to reinstall cuz virtual box did something or wine did something. Not sure what caused it or what it even was, but my system was trashed, so I reinstalled and lost my permissions for my drive.

EDIT: Sorry for being dumb and asking dumb questions like that, I must be thee most annoying user on the forum...  Is there a reward for that?   LULZ

---

### Post by vanadium on 2008-10-22
You should be as specific as possible in describing your problem, what you want to do, etc. Otherwise, we can only guess. I guessed right in this situation.

I am still guessing, but I assume that you still can read the drive: you just are not allowed to write on it. This would lead me to guess that your drive is mounted though /etc/fstab, but in a way that you can only read to it. In order to be able to tell something for sure, execute the following commands and post their output here:

```

sudo blkid
mount
cat /etc/fstab
ls -l /media

```

---

### Post by naknak987 on 2008-10-22
Thanks for the help, but I reformated the 360 gig drive that was almost full and mad it a ext3. After I copied my files back on it I could then change the permissions. It took about 5 hours to copy them one way. I still don't think I couldn't change the permissions simply because it was a ntfs drive tho. Thats because before I reinstalled ubuntu, changing the permissions on it was no problem. Maybe you could recomend a different file system that would be better then both ntfs or ext3, that would be cool.

---

### Post by vanadium on 2008-10-22
> I still don't think I couldn't change the permissions simply because it was a ntfs drive tho.
That is your good right. Changing to ext3 was the best you could do.

---

