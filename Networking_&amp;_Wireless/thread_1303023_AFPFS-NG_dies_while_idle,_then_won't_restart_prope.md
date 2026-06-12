---
title: "AFPFS-NG dies while idle, then won't restart properly"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by neoneddy on 2009-10-27
```
Last login: Tue Oct 27 10:46:43 2009 from 10.0.1.5
shawn@MythTV:~$ afpfsd -d
Daemon is already running and alive
shawn@MythTV:~$ afpfsd -d
Daemon is already running and alive
shawn@MythTV:~$ afpfsd -d
Daemon is already running and alive
shawn@MythTV:~$ afpfsd -d
Starting up AFPFS version 0.8.1
```

This is on Ubuntu 9.10 Beta, connecting to an Airport (SMB/CIFS has it's own issues right now).

ANy ideas?

---

### Post by alexthepuffin on 2009-10-28
I'm the author of afpfs-ng, so I can shed some light on this.  I don't know that much about mythbuntu, though, so I can't help with how that integration is done.

afpfs-ng needs a daemon to take care of the AFP chatter.  That's called afpfsd.  When you do a mount (either through fstab or explicitly through mount_afp), it starts up afpfsd (as that uid) to maintain the state of all your server connections.

I'm not quite sure what you're doing, but afpfsd is responding correctly if the daemon is already running.  You could kill off the daemon by running:
afp_client exit

But why do you want to kill off afpfsd?  It should be ready to accept your afp_mount command.

- Alex


> **neoneddy said:**
> ```
Last login: Tue Oct 27 10:46:43 2009 from 10.0.1.5
shawn@MythTV:~$ afpfsd -d
Daemon is already running and alive
shawn@MythTV:~$ afpfsd -d
Daemon is already running and alive
shawn@MythTV:~$ afpfsd -d
Daemon is already running and alive
shawn@MythTV:~$ afpfsd -d
Starting up AFPFS version 0.8.1
```

This is on Ubuntu 9.10 Beta, connecting to an Airport (SMB/CIFS has it's own issues right now).

ANy ideas?

---

### Post by neoneddy on 2009-10-28
I should explain better.

I mount the apple Airdisk with an entry in the fstab, so from a fresh boot it works great.  Then withing 1 to 2 hours I try and play a movie and the mythtv frontend hangs for a bit (waiting on filesystem I assume), then goes back the play movie screen.  If I try and play it again, the system reports file not found.

if I try and ls the directory I get a " Transport endpoint is not connected Unknown error 1, 107."

So  I then do a 
```
sudo umount -l /airdisk
sudo mount -a 
```

After that all is well again, for another couple of hours.  Now if I'm watching a movie it works perfectly.. it's almost like it needs to be used every hour or so or it just pukes and dies.

I should also say that I'm using a Drobo connected to my Airport Extreme as it's air disk, while not in use the drobo does power down the drives and goes into a lower power mode, so it could be possible that the lag time is throwing off the afpfsd process.  However it usually pretty snappy.

on a slightly different note, I'd love to use SMB/CIFS mounting but when I do that the system can't get a directory listing, however all files and folders work as expected.  My solution for now is:

When I need to update my library I mount with AFPFS, then remount on SMB/CIFS for day to day use.  I'd love something that just worked, this all started after the upgrade to 9.4 / 9.10

Thanks for your help in all of this.

---

### Post by Niksss on 2010-07-01
I m testing Netatalk 2.0.5 on my unix machine with afpfs-ng. I m using afpcmd command to access the volumes on the netatalk server. the directories that i m creating via afpcmd are being created with permissions 000. I cannot browse thru them. 
Also when i check the status then 

**Unix permissions: No, Netatalk permissions broken: Unknown**

is shown. has unix permissions ny relation with the prob?

---

### Post by Zookalicious on 2011-05-16
I know I'm late to the party but I'm still having this problem on Ubuntu 10.04, 10.10, and 11.04.

Mounting the volume works great at first, and I can browse it through the command line for awhile (browsing through any graphical filemanager causes hangs and crashes) but randomly it will decide to give up. It seems to be like the OP said, that the daemon crashes or something. The following shows several things. First it crashes halfway through copying a directory of music
```

...
cp: cannot stat `./Stray From The Path - Make Your Own History/11 Make Your Own History.mp3': Transport endpoint is not connected

```Then here I try to view the directory that I was currently in, which seems to no longer be connected.
```

chris@HUSH:~/capsule/HUSHbackup/chris/Music$ ls
ls: cannot open directory .: Transport endpoint is not connected

```Now trying to unmount the volume (so I can mount it again) shows that the afps daemon stopped running and the volume was unmounted. (I can assure you that I did not unmount it. This happens quite frequently with no discernable pattern).
```

chris@HUSH:~/capsule/HUSHbackup/chris/Music$ afp_client unmount ~/capsule
The afpfs daemon does not appear to be running for uid 1000, let me start it for you
afpfs-ng doesn't have anything mounted on /home/chris/capsule.

```Finally when trying to reconnect the drive, I get this.
```

chris@HUSH:~/capsule/HUSHbackup/chris/Music$ mount_afp afp://chris:password@192.168.1.64/Backups ~/GLaDOS
Mounting 192.168.1.64 from Backups on /home/chris/GLaDOS
Unmounting volume Backups from /home/chris/GLaDOS
FUSE reported the following error:
fuse: bad mount point `/home/chris/GLaDOS': Transport endpoint is not connected
Unknown error 1, 107.

```I'm not sure if this is a different issue, but it certainly seems to be related. One thing to note is that I cannot remount the drive in the same folder, no matter what. In order to mount the volume again, I need to make a NEW folder and mount it there instead. By the end of a session I can end up with 5 folders sitting in a directory that I used as mountpoints because each of them gives this error message after they have failed once.

Any input is much appreciated.

---

