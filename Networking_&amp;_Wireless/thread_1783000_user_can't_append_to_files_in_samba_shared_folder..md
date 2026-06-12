---
title: "user can't append to files in samba shared folder."
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by kukker32 on 2011-06-15
[SIZE=4]_**Dear community i really need some help now.**_[/SIZE]

I'm setting up a network between 2 pc's where the one should act like "file server" and a normal pc to surf on internet. called ORLA-DESKTOP

and the other pc is called OLGA-DESKTOP a pc connecting to the server and automounting the shared folder to the desktop

Both pc's run ubuntu 10.04 Lucid Lynx

The shared folder is located on the server in
/home/orla/svenson

ORLA-DESKTOP have 2 users "olga" and "orla" in a group called "svenson"
OLGA-DESKTOP have 1 registered user "olga" also in group called "svenson"

users on ORLA-DESKTOP can read/write/append and so on and fully manage everything in the shared folder.

But on OLGA-DESKTOP the user can make a file on the pc and then drag'n'drop the file the the shared folder, and can also delete files in the shared folder. but cannot create a file directly into the folder like on ORLA-DESKTOP

I have 3 configuration files made.
2 for automounting, Located on OLGA-DESKTOP
1 for samba server configurations located on the server ORLA-DESKTOP

-----

The first one is /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=50e834e4-fec7-4377-98b7-d2aa89a860c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca5daf25-1bba-4c7f-b88a-8ca2e6654e6c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


#automount shared folder as a folder on desktop
#we've told ubuntu to get the proper login information
//*server IP* *address*/svenson /home/olga/Shared cifs exec,credentiels=/etc/cifspw 0 0
```and this one is the cifspw file which tells which information to use when automount
```

#This is the file that gives the proper login information when mounting the shared folder etc/cifspw
username=olga
password=(some password)
```and this is my samba configuration file
```

#Share parameters
[Shared]
;    workgroup = svenson
;    server string = Shared server for svenson family
;    security = SHARE
;    log file = var/log/samba.%m
;    max log size = 200
;    dns proxy = no
;    path = /home/orla/svenson
;    writeable = yes
;    browseable = yes
;    valid users = olga, orla
;    read only = no
;    guest ok = no
```To sum it all up the real problem is that OLGA-DESKTOP can't append to files in the shared folder. but users on the server have no troubles doing it..

link to screenshot
**[http://i51.tinypic.com/2a689ko.jpg](http://i51.tinypic.com/2a689ko.jpg)**

---

### Post by kukker32 on 2011-06-16
Bump :O i really need some help please  ...

---

### Post by capscrew on 2011-06-16
> **kukker32 said:**
> [SIZE=4]_**Dear community i really need some help now.**_[/SIZE]

I'm setting up a network between 2 pc's where the one should act like "file server" and a normal pc to surf on internet. called ORLA-DESKTOP

and the other pc is called OLGA-DESKTOP a pc connecting to the server and automounting the shared folder to the desktop

Both pc's run ubuntu 10.04 Lucid Lynx

The shared folder is located on the server in
/home/orla/svenson

ORLA-DESKTOP have 2 users "olga" and "orla" in a group called "svenson"
OLGA-DESKTOP have 1 registered user "olga" also in group called "svenson"

users on ORLA-DESKTOP can read/write/append and so on and fully manage everything in the shared folder.

But on OLGA-DESKTOP the user can make a file on the pc and then drag'n'drop the file the the shared folder, and can also delete files in the shared folder. but cannot create a file directly into the folder like on ORLA-DESKTOP

I have 3 configuration files made.
2 for automounting, Located on OLGA-DESKTOP
1 for samba server configurations located on the server ORLA-DESKTOP

-----

The first one is /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=50e834e4-fec7-4377-98b7-d2aa89a860c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca5daf25-1bba-4c7f-b88a-8ca2e6654e6c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


#automount shared folder as a folder on desktop
#we've told ubuntu to get the proper login information
//*server IP* *address*/svenson /home/olga/Shared cifs exec,credentiels=/etc/cifspw 0 0
```and this one is the cifspw file which tells which information to use when automount
```

#This is the file that gives the proper login information when mounting the shared folder etc/cifspw
username=olga
password=(some password)
```and this is my samba configuration file
```

#Share parameters
[Shared]
;    workgroup = svenson
;    server string = Shared server for svenson family
;    security = SHARE
;    log file = var/log/samba.%m
;    max log size = 200
;    dns proxy = no
;    path = /home/orla/svenson
;    writeable = yes
;    browseable = yes
;    valid users = olga, orla
;    read only = no
;    guest ok = no
```To sum it all up the real problem is that OLGA-DESKTOP can't append to files in the shared folder. but users on the server have no troubles doing it..

link to screenshot
**[http://i51.tinypic.com/2a689ko.jpg](http://i51.tinypic.com/2a689ko.jpg)**

Do you have a copy of the original smb.conf file?  The smb.conf you displayed does not look correct.  

Please post the output of ```
testparm -s
```

What are the permissions on the shared directory.  Post the output of```
ls -l /home/orla/svenson
```

---

### Post by kukker32 on 2011-06-16
> **capscrew said:**
> Do you have a copy of the original smb.conf file?  The smb.conf you displayed does not look correct.  

Please post the output of ```
testparm -s
```What are the permissions on the shared directory.  Post the output of```
ls -l /home/orla/svenson
```

will do tomorrow when im at school again :)

---

### Post by capscrew on 2011-06-16
Okay by me.

---

### Post by kukker32 on 2011-06-17
output of testparm -s

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[svenson]"
Global parameter workgroup found in service section!
Global parameter server string found in service section!
Global parameter security found in service section!
Global parameter log file found in service section!
Global parameter max log size found in service section!
Global parameter dns proxy found in service section!
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]

[svenson]
    path = /home/orla/svenson
    valid users = olga, orla
    read only = No

```The output of ls command
```
total 24
drwxrwxrwx 2 orla orla    4096 2011-06-16 08:07 Documents
-rwxr--r-- 1 olga svenson 1032 2011-06-15 13:08 fstab
drwxrwxrwx 2 orla orla    4096 2011-06-15 09:55 Holiday films
drwxrwxrwx 2 orla orla    4096 2011-06-14 12:03 Holiday pictures
drwxrwxrwx 2 orla orla    4096 2011-06-14 12:17 Shared music
-rwxr--r-- 1 orla svenson  382 2011-06-15 11:45 smb.conf
-rw-r--r-- 1 olga svenson    0 2011-06-16 08:03 TESTFILE

```fstab and smb.conf in that folder is just for tranfering/backup between the machines and not needed for anything..

also i don't know how all the semicolons are in the smb.conf, but i can remove them if needed.

---

### Post by capscrew on 2011-06-18
> **kukker32 said:**
> output of testparm -s

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[svenson]"
Global parameter workgroup found in service section!
Global parameter server string found in service section!
Global parameter security found in service section!
Global parameter log file found in service section!
Global parameter max log size found in service section!
Global parameter dns proxy found in service section!
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]

[svenson]
    path = /home/orla/svenson
    valid users = olga, orla
    read only = No

```The output of ls command
```
total 24
drwxrwxrwx 2 orla orla    4096 2011-06-16 08:07 Documents
-rwxr--r-- 1 olga svenson 1032 2011-06-15 13:08 fstab
drwxrwxrwx 2 orla orla    4096 2011-06-15 09:55 Holiday films
drwxrwxrwx 2 orla orla    4096 2011-06-14 12:03 Holiday pictures
drwxrwxrwx 2 orla orla    4096 2011-06-14 12:17 Shared music
-rwxr--r-- 1 orla svenson  382 2011-06-15 11:45 smb.conf
-rw-r--r-- 1 olga svenson    0 2011-06-16 08:03 TESTFILE

```fstab and smb.conf in that folder is just for tranfering/backup between the machines and not needed for anything..

also i don't know how all the semicolons are in the smb.conf, but i can remove them if needed.

There are many errors in your smb.conf file.  For example ```
Global parameter workgroup found in service section!
Global parameter server string found in service section!
Global parameter security found in service section!
Global parameter log file found in service section!
Global parameter max log size found in service section!
Global parameter dns proxy found in service section!
```

The Global parameters belong under [Global].  The shares should be defined *below* all the global definitions

The best thing to do is to replace the file with an *unmodified copy* of smb.conf.  Then, the only modification needed is changing the security to share and adding the folder you wish to share which should look like this```

[Shared]
  path = /home/orla/svenson
  writeable = yes
  browseable = yes
  read only = no
  guest ok = yes

;  valid users = olga, orla

```

I would start with the valid users section commented out.  The semi-colon means ignore (a comment).

This is not what I would do, but it is close to your idea.  Why did you chose to have *security = share* instead of the default *security = user* which is more secure?

---

### Post by kukker32 on 2011-06-20
Okay i found out what the problem is, it is that im mounting as root so only root users have rights. so i need to mount as normal user.
im making a new thread about that,,

---

### Post by kukker32 on 2011-06-20
i found the solution by editing fstab automount line to this

```
//192.168.0.101/svenson /home/olga/Shared cifs exec,credentials=/etc/cifspw,rw,uid=olga 0 
```

---

