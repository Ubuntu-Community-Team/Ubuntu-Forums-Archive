---
title: "Problems Mounting Windows XP Share"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by snuffy47 on 2011-01-09
Hello

I am tring to mount a Windows Share on my local network.

I have already mounted anothe linux drive with no problems but everytime I use this command in terminal it displays a help file

sudo mount -t smbfs //192.168.1.111/my pictures2 /media/DSPCPictures -o 

There is no user name and password to my knowledge required

> $ sudo mount -t smbfs //192.168.1.111/My Pictures2 /media/DSPCPictures -o
mount: option requires an argument -- 'o'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
Been following some how toos but can not figure out why this is happening

---

### Post by PatchesTheCaveman on 2011-01-10
Omit the *-o*, so it reads:
```
sudo mount -t smbfs //192.168.1.111/my pictures2 /media/DSPCPictures 
```

---

### Post by snuffy47 on 2011-01-10
@ Patches

Have not tried this yet but why do I omit the -o for a windows share?




> Hi,

Refer the following threads

[http://ubuntuforums.org/showthread.php?t=1420895](http://ubuntuforums.org/showthread.php?t=1420895)

[http://ubuntuforums.org/showthread.php?t=1398560](http://ubuntuforums.org/showthread.php?t=1398560)

Hope this helps.   [suseendran.rengabashyam]("http://ubuntuforums.org/member.php?u=986845")

---

### Post by snuffy47 on 2011-01-10
Okay I am getting frustrated

I have tried the above and went through the 2 how toos :(

The share on my windows machine is the My Pictures folder Tammy/Documents and Settings/Owner/My Documents/My Pictures

Using terminal I can not mount it.  It is however accessible from Places and Network

I need some help to get back to square one.

When the share is mounted in places were can i find it?

---

### Post by snuffy47 on 2011-01-10
Well I pulled a rabbit out of my hat.  I have no idea how this worked but it did.

First reference is how to have spaces in file path
[http://ubuntuforums.org/showthread.php?t=27823&page=2](http://ubuntuforums.org/showthread.php?t=27823&page=2)

Next reference is how I finally got it to mount
[http://ubuntuforums.org/showthread.php?t=1398560](http://ubuntuforums.org/showthread.php?t=1398560) but user name and pw

I used the fstab line that required a user and pass
//192.168.1.111/My\040Pictures2  /media/DSPCPictures  cifs     defaults,uid=1000,gid=1000,credentials=/root/.smbcredentials  0  0

and at the user name and password I used the user name and password on the windows machine.

I do not know if it was the \040 for spaces that made it work i maybes i could have mounted it the same as my other ubuntu share but i donnt care it is mounted :)  Let the sync begin

---

