---
title: "mount network folder"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2009-10-12
Have studied quite a few items in Ubuntu Forums but can't see anything that helps with my specific problem.

I'm trying to mount a folder in a networked windows xp computer (pc is bill-xp and folder (shared) is ubuntu

This 

$ sudo mount -t smbfs -o username=bill, password=*****  //bill-xp/ubuntu  /mnt/xp

produces just a whole lot of info starting with

"Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.

etc"

Can anyone help?

Bill Lancaster

---

### Post by uncle-c on 2009-10-12
> **bill-lancaster said:**
> Have studied quite a few items in Ubuntu Forums but can't see anything that helps with my specific problem.

I'm trying to mount a folder in a networked windows xp computer (pc is bill-xp and folder (shared) is ubuntu

This 

$ sudo mount -t smbfs -o username=bill, password=*****  //bill-xp/ubuntu  /mnt/xp


Can anyone help?

Bill Lancaster

You should try replacing smbfs with cifs and also change the syntax e.g :

```

unclec@unclec-desktop:/mnt$ sudo mount -t cifs //xxx.xxx.xxx.xxx/tmp -o user=unclec,password=******** /mnt/xp

```

Of course passwd is the password of the windows user and not your linux password.

---

### Post by bill-lancaster on 2009-10-12
Thanks a lot!
This worked

sudo mount -t cifs //192.168.2.4/ubuntu -o user=bill,password=***** /mnt/xp

$ mount shows

//192.168.2.4/ubuntu on /mnt/xp type cifs (rw,user=bill,password=***)

on last line.

However there's no change under Places (i.e. no reference to the mount) also my main aim is access the network folder from a basic programme and so if the 'mount' is just a folder on the desktop then I can't find a way to access it.

Any ideas?

---

### Post by bill-lancaster on 2009-10-12
Hold on!  I should have waited a bit.
Soon after sending the previous post I sent an email with an attachment and low and behold, there in the "insert attachment" panel is ubunto on bill-xp.

Still can't access the folder from my basic prog though

Bill

---

### Post by bill-lancaster on 2009-10-12
OK - why didn't I think of it!

"/mnt/xp" is the path to my network folder.

Thanks for all the help!

Bill Lancaster

---

### Post by Iowan on 2009-10-12
If the problem is [SOLVED], you can mark the thread as such using the option under **Thread Tools**.:P

---

