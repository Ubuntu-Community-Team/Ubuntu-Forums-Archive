---
title: "NFS auto-unmount when server is unavailable"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by Rob_H on 2011-05-15
I've set up NFS on a home server, which I connect to from my laptop. The server may or may not be available at any given time, so I've set up the mount options in **/etc/fstab** on the laptop to maintain responsiveness even if the server is not available at boot time:

```
virgon:/warehouse /warehouse nfs rw,proto=udp,bg,soft,timeo=30,retrans=3,intr 0 0
```

This works OK for the most part. But if the server goes away after the laptop has already mounted it, then pretty much EVERY operation in KDE, Dolphin, etc. hangs for a few seconds as it tries unsuccessfully to access the mount. Is there a way to automatically unmount the NFS share if the server goes away? Would using **autofs** instead of **/etc/fstab** help? (I tried to get autofs working earlier and ran into an error. But I'll try harder if it solves this problem.)

---

### Post by DaveQB on 2011-09-25
This is a great question.

I have moved over to autofs for this reason when working with NFS but it doesn't seem to have made a great difference for this issue. I still have unresponsive Dolphins windows etc even though the mount is not mounted and the server for that particular mount has gone away. I have a timeout set to 30 seconds. Trying to lower it to 10 seconds now.
:-(

---

### Post by jawilljr on 2011-09-25
I use [this script](http://ubuntuforums.org/showthread.php?t=1389291&highlight=autofs) for auto mounting/unmounting.  works great.

Jerry

---

### Post by DaveQB on 2011-09-26
Oh so a bash script to replace autofs functionality? Very interesting.
All this cause autofs hangs desktops when trying to mount non-existent shares. I am using KDE4 and am suffering from this bug...

---

