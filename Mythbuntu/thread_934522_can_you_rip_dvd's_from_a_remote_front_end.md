---
title: "can you rip dvd's from a remote front end"
date: 2008-09-30
forum: Mythbuntu
---

### Post by mark467 on 2008-09-30
and if so how?

---

### Post by DemonBob on 2008-09-30
Well...

Depends on the setup. 

Setup 1: 

Remote Frontend. If the Remote frontend mounts the media directory's from the backend. Then you could sit at that front end and rip to the video's directory. 

Setup 2: (Might work)

Install Samba on the remote frontend, and share out the mountpoint for the dvd driver i,e /media/cdrom

Then mount the share on the pc you want to rip it to, and rip it that way...

---

### Post by mark467 on 2008-09-30
Well i tried step 1 before. i get the video info in the rip screen but then it just goes to nothing to do waiting screen

---

### Post by uopjohnson on 2008-09-30
That happens when there is somethign wrong with the DVD.  Either it is protected by somethign that linux can't crack or it is scratched somehow.  Try an old dvd, or once you have made yourself to ensure that the process works.

---

### Post by mark467 on 2008-09-30
it is happening with all of them (all dvd's i try). I did change the setting under media settings location of dvd device from /dev/cdrom0 to /dev/scd0 then i changed it to /dev/dvd  and same thing. before that it didnt find a dvd in the drive.  it looks like its going to work then goes to nothing to do screen. i can watch movies fine from the backend on the front end (VIA NFS MAPPED FOLDER)

---

### Post by uopjohnson on 2008-10-01
Mythdvd leaves a log file in /var/lib/mythdvd/temp/mtd.log
You can check that for more info.  That is urually where you will find errors that directories aren't writable, which may be yoru problem.

---

### Post by mark467 on 2008-10-01
That seems to be it. It is a mounted nfs share that should be able to be written to though. I can copy stuff there from my windows box. 


16:49:17: Using DVD source: /dev/scd0
16:49:17: Error: DVDISOCopyThread could not open output file: /var/lib/mythtv/videos/UNIT_S2D3_001of
16:49:19: job failed: job dvd 2 1 -1 0 -1 /var/lib/mythtv/videos/UNIT_S2D3

---

### Post by uopjohnson on 2008-10-02
Can you write to that directory on your frontend?  Try:
[code]touch /var/libe/mythtv/videos/testfile[code]
Is that where your NFS share is mounted?

---

### Post by mark467 on 2008-10-03
Hmm I guess not. I get this:

mark467@mythf804:~$ touch /var/lib/mythtv/videos/testfile
touch: cannot touch `/var/lib/mythtv/videos/testfile': Read-only file system


What is confusing is that i can copy an iso from my windows box to that share with no authentication

---

### Post by mark467 on 2008-10-03
Is it something in the way i shared it? This is my line in /etc/fstab

192.168.1.25:/var/lib/mythtv/videos /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr

---

### Post by uopjohnson on 2008-10-03
It is probably a problem with the way it is mounted since you can write just fine from your windows box.  Mounting listed in teh fstab is doine by the root user so sometimes you have to mess aroudna bit with the permissions to get it working.
try
```

192.168.1.25:/var/lib/mythtv/videos /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr,gid=users,umask=000 

```
added ',gid=users,umask=000' to the options
You might also want to check the permissions on the mount point 
```

ls -l /var/lib/mythtv/videos

```

---

### Post by mark467 on 2008-10-04
drwxrwxr-x   2 mythtv mythtv  4096 2008-10-03 22:08 videos

are the permissions on /var/lib/mythtv/videos

and i tried changing the mounting as suggested but didnt change outcome.

---

### Post by mark467 on 2008-10-18
anybody have any suggestions. I coppied dozens of iso's from my windows box without changing anything....

---

### Post by uopjohnson on 2008-10-18
Sorry I lost track of this thread.  
Try:
```
sudo touch /var/lib/mythtv/videos/testfile
```
To see if it is a permissions problem or a mount problem.

---

### Post by mark467 on 2008-10-19
mark467@mythf804:~$ touch /var/lib/mythtv/videos/testfile
touch: cannot touch `/var/lib/mythtv/videos/testfile': Read-only file system


What is confusing is that i can copy an iso from my windows box to that share with no authentication

---

### Post by uopjohnson on 2008-10-19
You forgot the sudo, which will run it as root to ensure that it isn't a user permission error. 
```
sudo touch /var/lib/mythtv/videos/testfile
```

---

### Post by mark467 on 2008-10-23
ok with sudo i get 

/var/lib/mythtv/videos/testfile': Permission denied

---

### Post by mark467 on 2008-10-23
ok i did chmod 777 on the videos folder and it works now. 
my question now is how ccould the windows machine write to it but mythbuntu can not?

---

### Post by uopjohnson on 2008-10-23
It is a local permission problem.  Windows probably mounts all shares as read/write.  Its weird becuase I thought the umask=000 would have set the permission on the folder to 777.

---

### Post by mark467 on 2008-10-27
I usedchmod 777 on the folder, should i remove the umask=000 from my mount data? it works now though thanks

---

