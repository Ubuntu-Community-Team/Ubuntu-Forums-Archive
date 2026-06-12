---
title: "make ram drive then share it on lan???"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-05
[http://www.ubuntuka.com/ubuntu-ramdisk-ramdrive-easy-way/](http://www.ubuntuka.com/ubuntu-ramdisk-ramdrive-easy-way/)


> scott@scott-P5QC:~$ mkdir -p /tmp/ram
scott@scott-P5QC:~$ sudo mount -t tmpfs -o size=512M tmpfs /tmp/ram/
[sudo] password for scott: 
scott@scott-P5QC:~$ mkdir -p /home/scott/ram
scott@scott-P5QC:~$ sudo mount -t tmpfs -o size=512M tmpfs /home/scott/ram/
scott@scott-P5QC:~$ 


I have no idea what I am doing! When I edited samba as the error message says, after a reboot, I still get the same error.
> 'net usershare' returned error 255: net usershare add: cannot share path /home/scott/ram as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.
So I tried doing the ram thing in my home folder and does not make a difference, still error message,

here is smb.conf showing the line
```
#

#======================= Global Settings =======================

[global]
# Let users share folders owned by someone else
;   usershare owner only = false
## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

```

---

### Post by sdowney717 on 2013-01-05
Kinda an odd request to do.
Situation is desired to do some further lan speed tests, this time to a ram drive 
run Lan Speed Test (program name) on win7 pc to ubuntu Pc network ram drive share.

I did get it to run a few times, but now gives permission denied errors.
What I did was put a folder in the ram folder owned by me and shared that without error, using nautilus.
Ran chown command on folder to make it owned by me.
Any ideas?

couple screens from win7 test did show it complete, then retry shows fail.

---

### Post by sdowney717 on 2013-01-05
ls -l for folder

```
scott@scott-P5QC:~/ram$ ls -l
total 0
-rwxr--r-- 1 scott scott  0 Jan  5 07:34 NW_SpeedTest.dat
drwxrwxrwx 2 scott scott 60 Jan  5 07:32 test
scott@scott-P5QC:~/ram$ 

```

any ideas?

---

### Post by sdowney717 on 2013-01-05
I just went back and tried to share ram folder and get a diff error.
Oddly, Lan Speed Test can create a file there but then cant read it.

---

### Post by sdowney717 on 2013-01-05
this is odd, I used win7 explorer and tried to copy a small tiny file into the /home/scott/ram/test folder and get a not enough space error?

When I delete files out of a ram drive, is the space used up anyway? that makes zero sense.

using nautilus says no space left on drive.
So when I delete files out of the ram drive, are they going to some kind of root trash?

---

### Post by sdowney717 on 2013-01-05
yes, these are hidden and use up the space!

---

### Post by sdowney717 on 2013-01-05
I dont think that a ram drive makes much difference to a lan speed test. Someone on a forum suggested using writing to a ram drive to eliminate hard drive getting involved in the process. PC with a lot of ram caching in the PC and large amounts of ram, it works like a ram drive anyway. 

I was looking at seeing how the gigabyte lan functioned without hard drive writing and maybe shows only slightly better speed. I have also used jperf and it shows higher MB/sec then the other 2 methods.

---

