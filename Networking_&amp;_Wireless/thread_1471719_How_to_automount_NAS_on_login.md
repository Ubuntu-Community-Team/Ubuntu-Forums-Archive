---
title: "How to automount NAS on login?"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2010-05-03
This computer is a little netbook that I haul around with me. it's running ubuntu 9.10

In the office, I have a NAS networked on a Windows network. I can access the filesystem in Nautilus using Samba. I'm connecting to the network wirelessly, at wlan0.

The folder I want to access shows in Nautilus as smb://diskstation/storage%20central/

And in Terminal it shows as:
```
jackelliott@TheJackUbuntuNetbook:~$ ls .gvfs
storage central on diskstation
```How can I set ubuntu up so that when it has connected to the office network it also automounts that Windows share?

Many thanks for any tips.

---

### Post by Iowan on 2010-05-03
Is [this]("http://ubuntuforums.org/showthread.php?t=1186877") similar to what you're looking for?

---

### Post by Rocket J Squirrel on 2010-05-03
Um, yeah. That seems to pretty much cover it. 

Many thanks!!!!

---

### Post by Iowan on 2010-05-03
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is another option you may have seen (or not).

---

### Post by Rocket J Squirrel on 2010-05-03
Looks a lot more complicated than the first solution. 

Now I'm dealing with permissions. This should be a new thread but I'll post the matter here.

After mounting the share, I ran a backup here on the local machine using Simple Backup Suite which created a backup in /var/backup

So I want to copy, or mv, the resulting backup off to the shared folder. My first pass results in this:
```

jackelliott@TheJackUbuntuNetbook:~$ cp -r /var/backup/2010-05-03_17.21.32.135907.TheJackUbuntuNetbook.ful .gvfs/"jacks ubuntu on diskstation"
cp: cannot access `/var/backup/2010-05-03_17.21.32.135907.TheJackUbuntuNetbook.ful': Permission denied
```Drat. Maybe I can access it as su, so: 
```
jackelliott@TheJackUbuntuNetbook:~$ sudo su
[sudo] password for jackelliott: 
root@TheJackUbuntuNetbook:/home/jackelliott# cp -r /var/backup/2010-05-03_17.21.32.135907.TheJackUbuntuNetbook.ful .gvfs/"jacks ubuntu on diskstation"
cp: accessing `.gvfs/jacks ubuntu on diskstation': Permission denied
```Double drat.

Edit: the backups in /var/backup are owned by root. The share in ~/.gvfs is owned by me.

---

### Post by Rocket J Squirrel on 2010-05-03
Okay, talking to myself here. 

Solved the permissions issue with 

```
jackelliott@TheJackUbuntuNetbook:~$ sudo chmod 755 /var/backup/2010-05-03_17.21.32.135907.TheJackUbuntuNetbook.ful -R
```

and I can copy the backup as me.

---

