---
title: "[SOLVED] Can't connect to backend"
date: 2007-11-07
forum: Mythbuntu
---

### Post by Azaghal_of_Belegost on 2007-11-07
Hey everybody,

I'm running a mythtv frontend/backend/desktop on 64bit gutsy gibbon, and everything was working fine until I started messing with my recording directory.  The first mistake I made was to simply change the directory without thinking to another partition, but I eventually figured out that the permissions needed to be set right, so I tried again.  Currently I have /var/lib/mythtv set up as an XFS partition.  I've changed the permissions to what you can see below:

drwxr-xr-x   3 mythtv        mythtv          23 2007-11-07 14:21 mythtv

The recordings folder has the following permissions:

drwxrwsr-x 2 mythtv mythtv 4096 2007-11-07 14:14 recordings

This setup was working fine after I initially installed it, but when I rebooted my computer today I'm running into the same problem as before, namely that the frontend keeps giving me an error message saying it can't connect to the backend.  I've tried searching Google and this forum, but so far I haven't found a solution to this problem.  Can any of you help me?

---

### Post by superm1 on 2007-11-07
> **Azaghal_of_Belegost said:**
> Hey everybody,

I'm running a mythtv frontend/backend/desktop on 64bit gutsy gibbon, and everything was working fine until I started messing with my recording directory.  The first mistake I made was to simply change the directory without thinking to another partition, but I eventually figured out that the permissions needed to be set right, so I tried again.  Currently I have /var/lib/mythtv set up as an XFS partition.  I've changed the permissions to what you can see below:

drwxr-xr-x   3 mythtv        mythtv          23 2007-11-07 14:21 mythtv

The recordings folder has the following permissions:

drwxrwsr-x 2 mythtv mythtv 4096 2007-11-07 14:14 recordings

This setup was working fine after I initially installed it, but when I rebooted my computer today I'm running into the same problem as before, namely that the frontend keeps giving me an error message saying it can't connect to the backend.  I've tried searching Google and this forum, but so far I haven't found a solution to this problem.  Can any of you help me?

Check out the backend log again in /var/log/mythtv/mythbackend.log

My own suspicion would be that you don't have the new partition configured to automatically mount

---

### Post by Azaghal_of_Belegost on 2007-11-07
I'm not exactly sure how I would tell if it was a mounting problem.  The partition seems to be mounting properly (I can access it in terminal and file browser).  In looking at the log, I noticed the following several times:

/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

The permissions for the lockfile are as follows:

-rwxrwx--- 1 mythtv mythtv          0 2007-11-04 22:25 nfslockfile.lock

Would it help if I posted the entire log file?

---

### Post by superm1 on 2007-11-07
> **Azaghal_of_Belegost said:**
> I'm not exactly sure how I would tell if it was a mounting problem.  The partition seems to be mounting properly (I can access it in terminal and file browser).  In looking at the log, I noticed the following several times:

/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

The permissions for the lockfile are as follows:

-rwxrwx--- 1 mythtv mythtv          0 2007-11-04 22:25 nfslockfile.lock

Would it help if I posted the entire log file?
Can you show the permissions for the whole directory?
```

ls -alhR /var/lib/mythtv
```

Perhaps something is being overlooked here.

---

### Post by Azaghal_of_Belegost on 2007-11-07
Here it is:

/var/lib/mythtv:
total 8.0K
drwxr-xr-x  3 mythtv mythtv   23 2007-11-07 14:21 .
drwxr-xr-x 55 root   root   4.0K 2007-11-05 07:27 ..
drwxrwsr-x  2 mythtv mythtv 4.0K 2007-11-07 14:14 recordings

/var/lib/mythtv/recordings:
total 7.8G
drwxrwsr-x 2 mythtv mythtv 4.0K 2007-11-07 14:14 .
drwxr-xr-x 3 mythtv mythtv   23 2007-11-07 14:21 ..
-rw-r--r-- 1 mythtv mythtv 2.3G 2007-11-05 20:01 1004_20071105185900.mpg
-rw-rw-rw- 1 mythtv mythtv  27K 2007-11-05 20:36 1004_20071105185900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.1G 2007-11-05 18:59 1046_20071105183000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 19:16 1046_20071105183000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 21:30 1046_20071105205900.mpg
-rw-rw-rw- 1 mythtv mythtv  35K 2007-11-05 21:48 1046_20071105205900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 22:01 1046_20071105213000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 22:18 1046_20071105213000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 23:30 1046_20071105225900.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 23:48 1046_20071105225900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-06 00:01 1046_20071105233000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-06 00:18 1046_20071105233000.mpg.png
-rwxrwx--- 1 mythtv mythtv    0 2007-11-04 22:25 nfslockfile.lock

---

### Post by superm1 on 2007-11-07
> **Azaghal_of_Belegost said:**
> Here it is:

/var/lib/mythtv:
total 8.0K
drwxr-xr-x  3 mythtv mythtv   23 2007-11-07 14:21 .
drwxr-xr-x 55 root   root   4.0K 2007-11-05 07:27 ..
drwxrwsr-x  2 mythtv mythtv 4.0K 2007-11-07 14:14 recordings

/var/lib/mythtv/recordings:
total 7.8G
drwxrwsr-x 2 mythtv mythtv 4.0K 2007-11-07 14:14 .
drwxr-xr-x 3 mythtv mythtv   23 2007-11-07 14:21 ..
-rw-r--r-- 1 mythtv mythtv 2.3G 2007-11-05 20:01 1004_20071105185900.mpg
-rw-rw-rw- 1 mythtv mythtv  27K 2007-11-05 20:36 1004_20071105185900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.1G 2007-11-05 18:59 1046_20071105183000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 19:16 1046_20071105183000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 21:30 1046_20071105205900.mpg
-rw-rw-rw- 1 mythtv mythtv  35K 2007-11-05 21:48 1046_20071105205900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 22:01 1046_20071105213000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 22:18 1046_20071105213000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 23:30 1046_20071105225900.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 23:48 1046_20071105225900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-06 00:01 1046_20071105233000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-06 00:18 1046_20071105233000.mpg.png
-rwxrwx--- 1 mythtv mythtv    0 2007-11-04 22:25 nfslockfile.lock
I want to say its that sticky bit you've got set on the directory.

its set to be drwxdrws.  Can you try making it drwxdrwx instead?

---

### Post by Azaghal_of_Belegost on 2007-11-07
I think I changed what you wanted me to, but I'm not sure.  Here's what ls -alhR /var/lib/mythtv gives me now:

/var/lib/mythtv:
total 8.0K
drwxr-xr-x  3 mythtv mythtv   23 2007-11-07 14:21 .
drwxr-xr-x 55 root   root   4.0K 2007-11-05 07:27 ..
drwxrwxr-x  2 mythtv mythtv 4.0K 2007-11-07 14:14 recordings

/var/lib/mythtv/recordings:
total 7.8G
drwxrwxr-x 2 mythtv mythtv 4.0K 2007-11-07 14:14 .
drwxr-xr-x 3 mythtv mythtv   23 2007-11-07 14:21 ..
-rw-r--r-- 1 mythtv mythtv 2.3G 2007-11-05 20:01 1004_20071105185900.mpg
-rw-rw-rw- 1 mythtv mythtv  27K 2007-11-05 20:36 1004_20071105185900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.1G 2007-11-05 18:59 1046_20071105183000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 19:16 1046_20071105183000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 21:30 1046_20071105205900.mpg
-rw-rw-rw- 1 mythtv mythtv  35K 2007-11-05 21:48 1046_20071105205900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 22:01 1046_20071105213000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 22:18 1046_20071105213000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 23:30 1046_20071105225900.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 23:48 1046_20071105225900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-06 00:01 1046_20071105233000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-06 00:18 1046_20071105233000.mpg.png
-rwxrwx--- 1 mythtv mythtv    0 2007-11-04 22:25 nfslockfile.lock

---

### Post by superm1 on 2007-11-07
> **Azaghal_of_Belegost said:**
> I think I changed what you wanted me to, but I'm not sure.  Here's what ls -alhR /var/lib/mythtv gives me now:

/var/lib/mythtv:
total 8.0K
drwxr-xr-x  3 mythtv mythtv   23 2007-11-07 14:21 .
drwxr-xr-x 55 root   root   4.0K 2007-11-05 07:27 ..
drwxrwxr-x  2 mythtv mythtv 4.0K 2007-11-07 14:14 recordings

/var/lib/mythtv/recordings:
total 7.8G
drwxrwxr-x 2 mythtv mythtv 4.0K 2007-11-07 14:14 .
drwxr-xr-x 3 mythtv mythtv   23 2007-11-07 14:21 ..
-rw-r--r-- 1 mythtv mythtv 2.3G 2007-11-05 20:01 1004_20071105185900.mpg
-rw-rw-rw- 1 mythtv mythtv  27K 2007-11-05 20:36 1004_20071105185900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.1G 2007-11-05 18:59 1046_20071105183000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 19:16 1046_20071105183000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 21:30 1046_20071105205900.mpg
-rw-rw-rw- 1 mythtv mythtv  35K 2007-11-05 21:48 1046_20071105205900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 22:01 1046_20071105213000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 22:18 1046_20071105213000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-05 23:30 1046_20071105225900.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-05 23:48 1046_20071105225900.mpg.png
-rw-r--r-- 1 mythtv mythtv 1.2G 2007-11-06 00:01 1046_20071105233000.mpg
-rw-rw-rw- 1 mythtv mythtv  33K 2007-11-06 00:18 1046_20071105233000.mpg.png
-rwxrwx--- 1 mythtv mythtv    0 2007-11-04 22:25 nfslockfile.lock
Okay so does it work now?

---

### Post by Azaghal_of_Belegost on 2007-11-07
No, unfortunately.

---

### Post by superm1 on 2007-11-07
> **Azaghal_of_Belegost said:**
> No, unfortunately.
You didn't mention how you were starting mythbackend.  Are you starting it via the init script?

```
sudo /etc/init.d/mythtv-backend restart
```

I'm running out of ideas! :)

---

### Post by Azaghal_of_Belegost on 2007-11-07
mythbackend had been starting upon reboot.  I just restarted it with sudo /etc/init.d/mythtv-backend restart and now it's working.  Do I need to do something else to get the backend running, or did I just need to restart it after I made the file changes?

---

### Post by superm1 on 2007-11-07
> **Azaghal_of_Belegost said:**
> mythbackend had been starting upon reboot.  I just restarted it with sudo /etc/init.d/mythtv-backend restart and now it's working.  Do I need to do something else to get the backend running, or did I just need to restart it after I made the file changes?
You just had to restart from the file changes.

---

### Post by Azaghal_of_Belegost on 2007-11-07
Alright, thanks a lot!
:)

---

### Post by venom986 on 2008-02-22
i'm having lockup issues with linuxmce when using mythtv and stumbled across this post.  i also have sticky bits on my directories, what was it about this that made you think they were the problem?

---

