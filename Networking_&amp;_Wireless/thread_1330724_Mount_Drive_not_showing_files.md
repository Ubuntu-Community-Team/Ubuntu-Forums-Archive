---
title: "Mount Drive not showing files"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by jgallen23 on 2009-11-18
I'm using ubuntu 9.10 and I'm trying to mount a shared drive from my airport extreme.  I am able to mount the drive via:
sudo mount -t cifs //extreme.local/videos /media/videos

once I change into that drive though and run ls, nothing shows up.  The weird thing, though, is that I can change directories.  So I can type cd TV and it'll go into that directory, but when I run ls in that directory nothing shows up.

Also, if I mount the drive in nautilus, everything shows up fine, but I need terminal access to the drive.

Any ideas?

---

### Post by eremyja on 2009-11-18
just a shot in the dark but try dir instead of ls

---

### Post by jgallen23 on 2009-11-18
Nope.  That didn't work either :sad:

---

### Post by eremyja on 2009-11-18
could it be permission problems? try using sudo dir... its pretty weird that it shows it in nautilus but not the terminal...

---

### Post by eremyja on 2009-11-18
oh wait just reread your original post... if you mount the drive with nautilus can you see the files in the terminal?

---

### Post by jgallen23 on 2009-11-18
if I mount the drive in nautilus I can see the files in ~/.gvfs, but I'm not always able to use nautilus to mount the drive (normally I just ssh into the box).  What could nautilus be doing differently?

---

### Post by jgallen23 on 2010-01-02
bump.  Any ideas on this?

---

### Post by brunott on 2010-02-03
I have the exact same problem when mounting a Hard Drive that is being shared via my Time Capsule.  Could it have something to do with the fact that the shared drive is formatted using HFS+ ?

---

### Post by brunott on 2010-02-03
Ahh..  a little more browsing and I came across this page:

 [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/406466](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/406466)

The last post on the page gave me the solution...

The trick is the "  nounix,noserverino,  " in the next section.

My fstab looks like this now (and I can see all folders and files now) 

//Time-Capsule/MyBook/Backups             /media/TC_MyBook              cifs    user,rw,iocharset=utf8,nounix,noserverino,uid=1000,gid=1000,file_mode=0775,dir_mode=0775,credentials=/home/joebloggs/smb.pass 0 0

Hope this helps ;-)

Martijn

---

