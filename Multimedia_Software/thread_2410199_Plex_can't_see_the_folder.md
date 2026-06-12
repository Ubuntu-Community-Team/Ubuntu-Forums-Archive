---
title: "Plex can't see the folder"
date: 2019-01-12
forum: Multimedia Software
---

### Post by ghostbacon on 2019-01-12
I know that i have to give plex permission to access folders from root (which i have done) but for some reason it can't see the folder that i have just created in my home folder. It sees all other folders but can't see this one? I have made the directories /hdds/hdd3 and /hdds/hdd4 and mounted both of my hard drives into these locations with fstab. It's worked before so i'm baffled to why it isn't working now.

---

### Post by TheFu on 2019-01-12
Which file system is used by each mount?  **df -Th**
What are the permissions for the top level directories on each?  **ls -l /hdds/* ** , please.

Can you show the mount options in the /etc/fstab for these partitions?

Please use _code tags_ when posting, so things line up correctly.

---

### Post by ghostbacon on 2019-01-12
After reinstalling the OS completely and doing the whole process again, it showed up. I think it's because this time i installed plex manually instead of from the "Ubuntu Software" app.

---

### Post by TheFu on 2019-01-12
> **ghostbacon said:**
> After reinstalling the OS completely and doing the whole process again, it showed up. I think it's because this time i installed plex manually instead of from the "Ubuntu Software" app.

Highly doubtful.  Plex sets up a plex userid and a plex groupid regardless of how it is installed.  You can check this by running** id plex**. Here's mine:
```
$ id plex
uid=107(plex) gid=114(plex) groups=114(plex),44(video)
```

My plex media is stored here:
```
istar:/D/M$ ll -d .
drwxrwsr-x 1277 thefu plex 61440 Jan  9 07:29 ./
```
See the group and permissions?  I allow plex to delete the files, so the group has write permissions on the directory.  The "s" is from a chmod g+s command (also called setgid or set-group-id). This forces any new files or directories inside this directory to be created with "plex" as the group.  My "thefu" userid is also in the plex group. It wouldn't work if my useid wasn't a member of plex, the group.

But, more likely, the way the media storage was mounted changed by a subtle choice made at the time.  As long as the "other" permissions allow read, then plex will be able to see the directories and files for cataloguing and playback.  That is often sufficient.

BTW, giving "root" access to the files won't help plex.  Reinstalling isn't a big commitment if nothing else is setup or if you have a list of the previously installed packages and keep your HOME directory and other data on separate partitions from the OS.

Regardless, if you have a solution, please mark this thread solved - Thread Tools button - near the top. Help the community out.

---

