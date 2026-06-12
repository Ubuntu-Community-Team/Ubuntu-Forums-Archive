---
title: "How to install Logitech Media Server 7.7 on Ubuntu 11.10 ?"
date: 2011-11-13
forum: Mythbuntu
---

### Post by gaskit on 2011-11-13
I'm trying to set up MythTv and Logitech Media Server (formerly Squeeze Server). I started with a Mythbuntu 11.10 iso got MythTV working. Then tried to install LMS from .deb file through Ubuntu Software Centre, but the install fails and screws the mySQL setup for MythTV.
 
I'm a total novice with Ubuntu and MythTV so still not sure where to find all the error logs etc, but I've seen a few similar posts where LMS installation fails.
 
So, before we get too detailed on error reports, can anyone that's done it tell me how to successfully install LMS7.7 on Mythbuntu 11.10 ? ( I believe it's something specific with this version combination - I know I could try Squeezserver 7.6.)
 
Thanks

---

### Post by william_1066 on 2011-12-28
Solution to this issue I have found documented here

[http://forums.slimdevices.com/showthread.php?t=91014&highlight=mythtv](http://forums.slimdevices.com/showthread.php?t=91014&highlight=mythtv)

---

### Post by paulyphonica on 2012-08-04
I am relatively new to Ubuntu and Linux, and I am having a problem with the Logitech setup.  What I am trying to do is to connect to a USB drive that hosts all of my media.  The drive itself is working properly, and was automatically mounted in /media folder as part of the Ubuntu 12.04 installation, and the path works when setting up a Samba share, so I know the path is correct.  However, when I look in the File System, it does not show in the /media folder there. And when I manually the path in the Logitech Media Server (7.7) --> Media Folders field, it is ignored, and the scan ends in a second, without any message.  As with the File System, the folder does not appear when I click on the Browse button in LMS.  Apparently there is something that needs to be done to make the drive fully visible.  My searches so far point to "fstab", "mtab", and "pmount".  I have tried several suggesions to no avail.  Please someone help me!

---

### Post by dangerous_d on 2012-08-08
What are the permissions of the mounted filesystem and who is the owner?

```
ls -l /media

```Did you format the drive on a different system or as a different user?  It is possible that you don't have permission to access the mounted filesystem.  You might try unmounting the auto-mount and then manually mount it with known permissions.

---

### Post by nickrout on 2012-08-09
> **paulyphonica said:**
> I am relatively new to Ubuntu and Linux, and I am having a problem with the Logitech setup.  What I am trying to do is to connect to a USB drive that hosts all of my media.  The drive itself is working properly, and was automatically mounted in /media folder as part of the Ubuntu 12.04 installation, and the path works when setting up a Samba share, so I know the path is correct.  However, when I look in the File System, it does not show in the /media folder there. And when I manually the path in the Logitech Media Server (7.7) --> Media Folders field, it is ignored, and the scan ends in a second, without any message.  As with the File System, the folder does not appear when I click on the Browse button in LMS.  Apparently there is something that needs to be done to make the drive fully visible.  My searches so far point to "fstab", "mtab", and "pmount".  I have tried several suggesions to no avail.  Please someone help me!

Are you sure the drive is mounted? check with the ```
mount
```command.

then check you can access the files as the user that runs LMS (I am not sure which user that is at present, but ```
ps aux|less
``` and search through for the running program will tell you the user it is running as). Let's call it logitechuser

```
sudo su -c logitechuser
ls -lR /media/mountpoint/path/to/music

```

That'll tell you if that user can see the files.

Also LMS does create log files. Have you looked at them after a scan?

---

