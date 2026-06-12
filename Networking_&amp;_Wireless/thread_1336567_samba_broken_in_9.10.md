---
title: "samba broken in 9.10"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by linuxonbute on 2009-11-24
I have an iomega nas box on my network. I had a share set up when running 9.04 and have been using backintime to do regular backups of my laptop.

About a week ago i upgraded to 9.10 and now I cannot figure out what is wrong.

I can mount the share to a directory on my home directory. I can create a directory under it and can save a file to it. However I cannot see them afterward, change to the directory or open the file.

To make sure it was nothing to do with the nas box I booted into a live 9.04, set up wireless networking, mounted the nas box share and everything is back to normal.

To make sure it was not the upgrade which was causing the problem I did the same thing with a live 9.10 disc. I can mount the share but still have the same problem. It seems to be something wrong with 9.10 but what?
How can I report a bug in launchpad if i don't know what is causing the problem?

Any ideas guys?
tia
Norm

---

### Post by linuxonbute on 2009-11-25
> **linuxonbute said:**
> I have an iomega nas box on my network. I had a share set up when running 9.04 and have been using backintime to do regular backups of my laptop.

About a week ago i upgraded to 9.10 and now I cannot figure out what is wrong.

I can mount the share to a directory on my home directory. I can create a directory under it and can save a file to it. However I cannot see them afterward, change to the directory or open the file.

To make sure it was nothing to do with the nas box I booted into a live 9.04, set up wireless networking, mounted the nas box share and everything is back to normal.

To make sure it was not the upgrade which was causing the problem I did the same thing with a live 9.10 disc. I can mount the share but still have the same problem. It seems to be something wrong with 9.10 but what?
How can I report a bug in launchpad if i don't know what is causing the problem?

Any ideas guys?
tia
Norm

Further information.
I checked smb.conf on my desktop ( 8.10 ) machine and it has 

workgroup = MSHOME

The NAs box has 
workgroup = WORKGROUP

I can mount the share and have full access from this PC

I edited smb.conf on my laptop and changed 
workgroup from WORKGROUP to MSHOME, restarted samba 
as an ordinary user I can mount the share on my laptop ( as before )
I mounted it to a directory on my home partition /home/norman/nas3

and now I get this:

norman@norman-laptop:~$ cd nas3
norman@norman-laptop:~/nas3$ ls

norman@norman-laptop:~/nas3$ mkdir test

norman@norman-laptop:~/nas3$ cd test
norman@norman-laptop:~/nas3/test$ ls

norman@norman-laptop:~/nas3/test$ touch mini.txt

norman@norman-laptop:~/nas3/test$ ls -l
total 0

norman@norman-laptop:~/nas3/test$ cd ..
norman@norman-laptop:~/nas3$ ls

norman@norman-laptop:~/nas3$ ls
norman@norman-laptop:~/nas3$ cd test

norman@norman-laptop:~/nas3/test$ ls

norman@norman-laptop:~/nas3/test$ echo "Hello World">mini.txt

norman@norman-laptop:~/nas3/test$ cat mini.txt
Hello World

norman@norman-laptop:~/nas3/test$ ls -l
total 0
norman@norman-laptop:~/nas3/test$ ls

norman@norman-laptop:~/nas3/test$ 


What is going on???????
Why can I create directories, files and put stuff in the files but not see them?
Any ideas guys?

---

### Post by Iowan on 2009-11-25
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To?

---

### Post by linuxonbute on 2009-11-25
> **Iowan said:**
> Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To?

Yes I have, but thanks for the suggestion.

My problem does not seem to be the same as any of the possible ideas there.

It just seems that something IS wrong with 9.10 if a live 9.10 doesn't work 

and yet a live 9.04 works fine.

---

### Post by Lvcoyote on 2009-11-25
I followed that "How To" and it worked for getting me to share Ubuntu with a XP machine, but Windows 7 was very stubborn.  Then a little while ago I did a system update and there were several Samba updates available.  I installed all those and now it works with Win7..... so, if you have not already, follow that "How To" and implement the changes he recommnds there.  Then use the update manager and get all the latest Samba updates.

---

### Post by linuxonbute on 2009-11-26
> **Lvcoyote said:**
> I followed that "How To" and it worked for getting me to share Ubuntu with a XP machine, but Windows 7 was very stubborn.  Then a little while ago I did a system update and there were several Samba updates available.  I installed all those and now it works with Win7..... so, if you have not already, follow that "How To" and implement the changes he recommnds there.  Then use the update manager and get all the latest Samba updates.

Well, as I have said it doesn't seem to be the same problem as those mentioned and there are no updates available. As i don't really want to be without regular backups I am going to revert to 9.04 and maybe try it in a couple of months ( or wait for 10.04 )

---

### Post by dmizer on 2009-11-26
> **linuxonbute said:**
> Well, as I have said it doesn't seem to be the same problem as those mentioned and there are no updates available
You have at least one problem mentioned in the howto right here.
> **linuxonbute said:**
> workgroup = MSHOME

The NAs box has 
workgroup = WORKGROUP
Even though you many not think that the things listed in the howto match your situation, you should still make all the changes. Once you're done you'll probably find that your share works fine.

---

### Post by linuxonbute on 2009-11-27
> **dmizer said:**
> You have at least one problem mentioned in the howto right here.

Even though you many not think that the things listed in the howto match your situation, you should still make all the changes. Once you're done you'll probably find that your share works fine.

Yes, I know but the desktop works fine with that! Also I changed the NAS box to MSHOME, rebooted both the NAS box and my laptop and still had the same problem!

Anyway I will go through the howto again and apply everything. I would rather solve the problem than run away from it.

I still do not understand how a live 9.04 works but a live 9.10 doesn't.
After all in that situation I am not making any real changes myself, just configuring the wlan card, downloading samba and running it.

---

### Post by dmizer on 2009-11-27
> **linuxonbute said:**
> I still do not understand how a live 9.04 works but a live 9.10 doesn't.
After all in that situation I am not making any real changes myself, just configuring the wlan card, downloading samba and running it.

Because the running kernel in the Live CD is old, and doesn't have all the recent change applied. Some of the more recent changes (since the live CD) have broken things, and some of the kernel changes have fixed things.

---

### Post by linuxonbute on 2009-11-27
Ok I now have the following:

The NAS box has workgroup = WORKGROUP
=============================================================
smb.conf now has:-

# Change this to the workgroup/NT-domain name your Samba server will part of
#workgroup = WORKGROUP
	workgroup = WORKGROUP
        netbios name = norman-laptop

# What naming service and in what order should we use to resolve host names
# to IP addresses
	name resolve order = lmhosts wins bcast host

=============================================================

nsswitch now has:-

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

=============================================================

UFW rules :-

137/udp | allow | 192.168.1.0/24
138/udp | allow | 192.168.1.0/24
139/tcp  | allow | 192.168.1.0/24
445/tcp  | allow | 192.168.1.0/24
=============================================================

/etc/fstab has the line :-

//192.168.1.60/PUBLIC  /home/norman/nas2  cifs  password=MySecretPassword,uid=1000,gid=1000,username=norman  0  0

and the share mounts on bootup.

and a share on my desktop box has the line :-

//192.168.1.30/documents  /home/norman/nas1  cifs  password=MySecretPassword,uid=1000,gid=1000,username=norman  0  0

=============================================================

I have rebooted both the NAS box and the laptop.

I still have exactly the same problem.

norman@norman-laptop:~$ ls nas2

norman@norman-laptop:~$ mkdir nas2/test1

norman@norman-laptop:~$ echo "Hello World">nas2/test1/mini.txt

norman@norman-laptop:~$ ls nas2

norman@norman-laptop:~$ cd nas2

norman@norman-laptop:~/nas2$ ls -l
total 0

norman@norman-laptop:~/nas2$ ls test1

norman@norman-laptop:~/nas2$ cat test1/mini.txt
Hello World

norman@norman-laptop:~/nas2$ echo "Hello My World">>test1/mini.txt

norman@norman-laptop:~/nas2$ cat test1/mini.txt
Hello World
Hello My World

norman@norman-laptop:~/nas2$ ls test1

norman@norman-laptop:~/nas2$ 
=============================================================

I can do the same on the share from my desktop but I can see all the directories and files on it.

There are no updates to my system available.

Have I missed something?

---

### Post by dmizer on 2009-11-27
What is the output of

```
sudo ls /home/norman/nas2
```

---

### Post by linuxonbute on 2009-11-28
> **dmizer said:**
> What is the output of

```
sudo ls /home/norman/nas2
```

norman@mainbox:~$ sudo ls /home/norman/nas2
[sudo] password for norman:
norman@mainbox:~$

---

### Post by linuxonbute on 2009-11-28
Also

 ls -l nas?
nas1:
total 36
-rwxr--r-- 1 norman norman   255 2008-09-28 20:37 fileit.py
drwxr-xr-x 4 norman norman  4096 2008-10-07 16:24 laptop-7-10-2008
-rwxr--r-- 1 norman norman 21426 2008-07-23 19:43 notknown.odt
-rw-r--r-- 1 norman norman  2416 2008-07-07 23:46 Unsaved Document 1

nas2:
total 0

nas3:
total 0

Nothing is mounted at nas3 but the iomega box is mounted at nas2

---

### Post by dmizer on 2009-11-29
> **linuxonbute said:**
> Also

 ls -l nas?
nas1:
total 36
-rwxr--r-- 1 norman norman   255 2008-09-28 20:37 fileit.py
drwxr-xr-x 4 norman norman  4096 2008-10-07 16:24 laptop-7-10-2008
-rwxr--r-- 1 norman norman 21426 2008-07-23 19:43 notknown.odt
-rw-r--r-- 1 norman norman  2416 2008-07-07 23:46 Unsaved Document 1

nas2:
total 0

nas3:
total 0

Nothing is mounted at nas3 but the iomega box is mounted at nas2

You mean, you have more than one share on the iomega box, and some work correctly (namely nas1)?

---

### Post by linuxonbute on 2009-11-30
> **dmizer said:**
> You mean, you have more than one share on the iomega box, and some work correctly (namely nas1)?

Sorry, no, I meant nas1 is on my desktop PC 

and nas3 is where I mount a USB drive I sometimes connect to my desktop PC 

and share on the network. 

I usually only connect it to backup some of my son-in-laws windows stuff.

What I have now done is comment out all my fstab entries for any share, 

changed the //192.168.1.60/PUBLIC folder to have no password required

rebooted the laptop and then 

norman@norman-laptop:~$ gvfs-mount smb://192.168.1.60/PUBLIC
norman@norman-laptop:~$ ls .gvfs
public on 192.168.1.60

norman@norman-laptop:~$ ls .gvfs/public\ on\ 192.168.1.60/

norman@norman-laptop:~$ mkdir .gvfs/public\ on\ 192.168.1.60/test1

norman@norman-laptop:~$ ls .gvfs/public\ on\ 192.168.1.60/
test1

norman@norman-laptop:~$ ls .gvfs/public\ on\ 192.168.1.60/test1/

norman@norman-laptop:~$ echo "Hello World"> .gvfs/public\ on\ 192.168.1.60/test1/mini.txt

norman@norman-laptop:~$ cat .gvfs/public\ on\ 192.168.1.60/test1/mini.txt



Hello World

norman@norman-laptop:~$ echo "Hello My World">> .gvfs/public\ on\ 192.168.1.60/test1/mini.txt

norman@norman-laptop:~$ cat .gvfs/public\ on\ 192.168.1.60/test1/mini.txt

Hello World
Hello My World

norman@norman-laptop:~$ echo "test2">.gvfs/public\ on\ 192.168.1.60/test1/next.test
norman@norman-laptop:~$ ls -l .gvfs/public\ on\ 192.168.1.60/test1/
total 1
-rwx------ 1 norman norman 27 2009-11-30 20:26 mini.txt
-rwx------ 1 norman norman  6 2009-11-30 20:35 next.test
norman@norman-laptop:~$ rm .gvfs/public\ on\ 192.168.1.60/test1/next.test
norman@norman-laptop:~$ ls -l .gvfs/public\ on\ 192.168.1.60/test1/
total 1
-rwx------ 1 norman norman 27 2009-11-30 20:26 mini.txt

Now, if I run from the command line
. backintime-gnome and point the backup to /home/norman/.gvfs/public\ on\ 192.168.1.60/

It is complaining about not being able to set times:

rsync: failed to set times on "/home/norman/.gvfs/public on 192.168.1.60/backintime/new_snapshot/backup/home/norman/Photos/2008/11/19": Operation not supported (95)

at the moment it is still creating directories and hidden file ( I think ) so I will leave it running overnight.


So what is different doing it this way?

---

### Post by linuxonbute on 2009-12-02
> 
Now, if I run from the command line
. backintime-gnome and point the backup to /home/norman/.gvfs/public\ on\ 192.168.1.60/

It is complaining about not being able to set times:

rsync: failed to set times on "/home/norman/.gvfs/public on 192.168.1.60/backintime/new_snapshot/backup/home/norman/Photos/2008/11/19": Operation not supported (95)

at the moment it is still creating directories and hidden file ( I think ) so I will leave it running overnight.


So what is different doing it this way?

Well, it seems it created all the directories but did not store any files!!

Thanks for the help so far but if no-one can suggest anything else I can 

try I will revert to 9.04.

---

### Post by linuxonbute on 2009-12-02
bump

---

