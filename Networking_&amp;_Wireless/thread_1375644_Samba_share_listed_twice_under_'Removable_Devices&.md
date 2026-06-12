---
title: "Samba share listed twice under 'Removable Devices&quot;"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by mikebeecham on 2010-01-08
Hi there,

Since upgrading to Karmic, all my shares under 'Removable Devices' are listed twice...all was fine in Jaunty though, and I've done nothing to change them.

Would anyone have an idea how to resolve this.

In terms of what I see, there are all my shares with a white drive icon which, when clicked, do nothing.  I then have all the same shares with a metal drive icon which open up the share when clicked.

I understand that the icons may look different, depending on what icon theme you're using, but the principal will remain the same.

Thanks in advance.




Mike

---

### Post by Morbius1 on 2010-01-08
I'm lost. Could you explain a little more where you're seeing this "Removable Devices". In Nautilus? On the Desktop?

I'm not familiar with any "Removable Devices" and Samba. Is this a network share you're talking about or is this a locally installed external usb drive?

---

### Post by lavinog on 2010-01-08
A screenshot might be useful.

If you unmount all of the shares, and reconnect do you still get two shares listed?
You might need to purge your nautilus config files.

---

### Post by mikebeecham on 2010-01-08
Hi guys,

I am seeing duplicates in both Nautilus, and if I go to Places > Removeable Media (Desktop).

These are folders that currently exist on my Apple Mac, and have been set up in my /etc/fstab to allow me access to the the shares.

I hope this helps.




Mike

---

### Post by lavinog on 2010-01-08
> **mikebeecham said:**
> Hi guys,

I am seeing duplicates in both Nautilus, and if I go to Places > Removeable Media (Desktop).

These are folders that currently exist on my Apple Mac, and have been set up in my /etc/fstab to allow me access to the the shares.

I hope this helps.

Mike

Are you sure you don't have duplicate entries in fstab?

Can you unmount the shares?
Maybe one is from fstab and the other is from gvfs which is automounting it for you.

---

### Post by mikebeecham on 2010-01-08
lavinog,

You COULD be right, as I have gvfs installed.  So, which would be the better way to go...remove the entries from my fstab, or uninstall gvfs?

---

### Post by lavinog on 2010-01-08
don't uninstall gvfs because it is how you mount removable drives.
try removing the fstab entries.  You can put them back in if it doesn't turn out he way you want.

---

### Post by mikebeecham on 2010-01-09
Ok, I there were no duplicate entries in fstab....but I removed the ones that were in there.

Having saved fstab, umount -a, mount -a nothing appeared at all.  All of my shares were missing.

I then added the entries back into fstab, saved the file, umount -a (just to make sure!!), mount -a and all my shares were back, complete with duplicates.

Very confusing!

---

### Post by SecretCode on 2010-01-09
Although my Samba shares are fine, I have a similar situation with internal disk partitions that are mounted in fstab - **some** of them appear by disk label as well as by mount point name in the places menu. 

The places menu looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142999&stc=1&d=1263034542[/IMG]
- the 'Files' and 'Data' items are the puzzling ones, and they don't have a hard disk icon; not sure what that icon represents. The 4 items above are the volume labels for various partitions. 'Files' is /dev/sda8 mounted at /media/Files, label 'F_Bulk(5)'; and 'Data' is /dev/sda7 mounted at /media/Data, label 'Data(4)'. 

My fstab contains the following:
```
# ntfs partition "Data(4)", /dev/sda7
UUID=181C0FED1C0FC52A	/media/Data	ntfs-3g	rw,users,umask=0000,auto	0	0
# ntfs partition "F_Bulk(5)", /dev/sda8
UUID=58542063542045DA	/media/Files	ntfs-3g	rw,users,umask=0000,auto	0	0
# ntfs partition /dev/sda6
/dev/sda6	/media/sda6	ntfs-3g	rw,users,umask=0000,auto	0	0
```
I don't automount sda1, but that still shows in the menu (label "XP1(1)"). 

On the other hand, sda6 is automounted, but it doesn't have the extra places menu entry. What's different about sda6? Not currently mounted by uuid, and the mount point name /media/sda6 is the same as the dev name /dev/sda6.

I'm not in any hurry to solve this, but **mikebeecham**, it might help if you post a capture of your menu and the contents of your fstab.

---

### Post by alecz20 on 2010-02-22
Here is a screenshot of my duplicate entries:

Both "server" and "alex" are samba shares added in fstab so they are automatically mounted at boot. Their entries in fstab are identical, but only one is duplicated.

From the duplicated ones, one is mounted, and the other is un-mounted. If I try to mount the latter, I get an error message.

I have no idea where to start looking for solution.

Below is my fstab content:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=83d32761-7e35-4c46-b2cd-10bb24297d59 /               ext3    defaults,errors=remount-ro,relatime 0       1

# /dev/sda1 
#UUID=B840C83C40C802DC /media/sda1     ntfs    users,defaults,umask=007,gid=46 0       1

# /dev/sda4
UUID=6113ab50-2d8c-4cbd-aca4-0cc8883fd2f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0




# network shares added by alecz
//192.168.0.100/server  /home/alex/lan/server/server  cifs  credentials=/home/alex/.smbcredentials,gid=alex,uid=alex,iocharset=utf8,file_mode=0777,dir_mode=0777,unicode,users  0  0

//192.168.0.100/alex  /home/alex/lan/server/alex  cifs  credentials=/home/alex/.smbcredentials,gid=alex,uid=alex,iocharset=utf8,file_mode=0777,dir_mode=0777,unicode,users  0  0

#//192.168.0.100/Public /home/alex/gaga cifs noauto,users 0 0

---

### Post by JohnnyC35 on 2010-03-04
I'm actually having a similar issue with this also. I'm not using Samba, these are just external hard drives that I have. They show up duplicated in Places and Nautilus. I had thought I had found a fix in a previous thread, it referred to mount manager. I installed it but sadly I cannot read Russian, I didn't find an English version. Here is a copy of my fstab if it will help:

> proc            /proc           proc    defaults        0       0
UUID=2c929bc6-a715-4dc4-a4ee-aa05b6af0b3c /        ext2    noatime,nodiratime,errors=remount-ro 0 1
UUID=523a4fea-32d2-4924-9c4f-ec6772557fb9 /home    ext2    defaults,sync,noatime,nodiratime     0 1
UUID=60ce04eb-8dc4-430d-aaf7-0864ca65f1fe   /media/Media1 xfs users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
UUID=a2b357b5-700f-4409-b8ed-b4df99f1656e   /media/Media2 xfs users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
UUID=26c94f5c-0708-4031-be12-ece4f0815c90   /media/Media3 xfs users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
UUID=4df339f3-1ef9-4516-9762-aad2f2d9160b   /media/Media4 xfs users,noauto,sync,noatime,nodiratime,allocsize=384m 0 1
UUID=14e63b39-c51b-466d-bb92-bcb956cd518e   /media/Media5 xfs users,noauto,sync,noatime,nodiratime,allocsize=384m 0 1
UUID=81ebbbd2-d799-4dd1-a59c-e3bfc090967c   /media/Media6 xfs users,noauto,sync,noatime,nodiratime,allocsize=384m 0 1One set of the Media drives I can open, the other comes up with this error:
> mount: /dev/sdb1 already mounted or /media/Media1 busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/Media1I tried renaming mtab and rebooting but that didn't seem to solve the issue. 

Thanks in advance if anyone can help.

---

### Post by lavinog on 2010-03-05
> **JohnnyC35 said:**
> I'm actually having a similar issue with this also. I'm not using Samba, these are just external hard drives that I have. They show up duplicated in Places and Nautilus. I had thought I had found a fix in a previous thread, it referred to mount manager. I installed it but sadly I cannot read Russian, I didn't find an English version. Here is a copy of my fstab if it will help:

One set of the Media drives I can open, the other comes up with this error:
I tried renaming mtab and rebooting but that didn't seem to solve the issue. 

Thanks in advance if anyone can help.

don't rename mtab.
I would edit your fstab to remove all but the first two entries (the media mounts)
gvfs handles this automatically for external drives.

---

### Post by alecz20 on 2010-03-11
I think I found a solution for my case.

All I did was to un-mount the drives (from the desktop): Right-Click -> Unmount. This worked because of the parameter users for those mount-points.

After un-mounting, the duplicate disappeared. When re-mounting (using reboot) there were no more duplicates. Ho-ray!


I guess this glitch still qualifies as a bug in the bug reports.

---

### Post by orangesplotch on 2010-04-08
I was having the same issue using sshfs in fstab to mount network drives. Came across this solution which worked for me:
[https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298/comments/9](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298/comments/9)

It's a bit redundant, but at least it gets rid of the double listing and allows the user to unmount the drive by right clicking on the desktop icon.

---

### Post by alecz20 on 2010-04-11
A follow-up for my solution:

The workaround I provided only works until the system is rebooted.


I have to entries in my /etc/fstab file, and they are completely identical with the exception of the network share, and the mount point.

Still, one appears twice in Computer, and places, but only one of the duplicates is mounted.

---

### Post by alecz20 on 2010-04-17
> **JohnnyC35 said:**
> I'm actually having a similar issue with this also. I'm not using Samba, these are just external hard drives that I have. They show up duplicated in Places and Nautilus. I had thought I had found a fix in a previous thread, it referred to mount manager. I installed it but sadly I cannot read Russian, I didn't find an English version. Here is a copy of my fstab if it will help:

One set of the Media drives I can open, the other comes up with this error:
I tried renaming mtab and rebooting but that didn't seem to solve the issue. 

Thanks in advance if anyone can help.

I found that shares will appear twice if you use UUID instead of /dev/sdaX.

---

### Post by lavinog on 2010-04-17
> **alecz20 said:**
> I found that shares will appear twice if you use UUID instead of /dev/sdaX.

That is interesting.  Will you be moving to lucid soon.  If so it would be good to know if this bug still exists.

---

### Post by alecz20 on 2010-05-02
I am currently running 9.10 and I have noticed some strange behavior.

First of all this happens to only one of the two shares that I have mounted. Also, it's always the same share, the one with my own name.

If the share does not appear twice, in a few minutes I get the DBUS Error message, saying it couldn't connect to the share, and that's when the duplicate share appears.

If I stay with duplicate shares, the DBUS error message does not appear again, but if I remove the duplicate (by un-mounting and re-mounting) the DBUS error message appears again along with the duplicate.

This behavior starts to really annoy me, especially because this is a fresh install !!!

I have no idea why DBUS (whatever it is) tries to mount an already mounted share.

---

### Post by beumont2 on 2010-06-03
I have the same problem! I have two samba shares on my server, one is password protected called "Private" the other one is open for everyone on the lan and its called "share". Only the Private share apperas twice in the menu. I have only one entry in fstab! Can anybody help me with this?

---

### Post by alecz20 on 2010-06-03
In my case, both are password protected. However only one appears duplicated.

I could not find what the difference is that only one is duplicated.

On the server that serves the shares, there are two shares:

/home/alex        -> appears duplicated no matter what
and
/home/share       -> appears correctly

The only way to fix this is to use a program called PyNeighbourhood.

PROS:
This program can really do magic!
You don't need to be root to mount or unmount.
You don't get any duplicates.
The icons is the same as the local drives (hence no duplicates I guess)
It uses your password from the account, not stored as plaintext in some .smbcredentials file

CONS:
I does not mount/unmount at boot-up/shut-down.

I really wonder how PyNeighmbourhood does it, because fstab can't do it properly.

---

### Post by beumont2 on 2010-06-03
I found a fix. :popcorn:

I have installed the package smbfs because it wasnt installed on 10.04 and now it works. It is depricated and I am still using CIFS to mount it thru fstab but the it helped.

---

### Post by beumont2 on 2010-06-03
I think the problem is solved when you install just the package samba-common. The SMBFS dependencies shows this! I have to test this.

---

### Post by alecz20 on 2010-06-03
I'll give it a try when i get home.

---

### Post by lapega on 2010-06-08
I have installed samba-common and the problem continues.

---

### Post by beumont2 on 2010-06-08
It works for me till now :)

I have installed the smbfs package.

---

### Post by alecz20 on 2010-06-08
smbfs was already the latest version on my system.

The strange thing is that this does not occur all the time, roughly about 80% of the time.

But always on the same share!
What is the thing with that share? Are home directories :evil:cursed:evil: in some way?

---

### Post by beumont2 on 2010-06-08
I would suggest to make a fresh install of 10.04, cant tell you why this happens :(

---

### Post by Siobhany on 2010-12-15
I still had this problem after fresh 10.04 install.

---

### Post by alecz20 on 2010-12-15
Surely there must be a way to troubleshoot this.

Why is it that one particular share is listed twice and not the others?

Details:

Remote computer shares:
/home/alex - shared as alex-server
/home/share - shared as server

Client computer:
alex-server listed twice
server listed once.

Why the discrimination???

---

### Post by [yas] on 2011-02-20
Hi all,
I found this issue again in Maverick (10.10), just trying to add shared folders through fstab gives me the same result (icon twice in "Places"). Reported in [Bug #444500]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/444500")

I had installed **smbfs** and **winbind** for netbios names resolution (as indicated in [MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")) and the unmount settings order.

So I found a workaround, because mounting the shared folders manually using command-line worked well (without repeated icon), I put the commands in a script to be executed when my wireless network gets up.

I added 02mapdrives file in /etc/NetworkManager/dispatcher.d/ giving it execution permissions, with the following content:
```

#!/bin/bash
if [ $1 == "wlan0" ] && [ $2 == "up" ] ; then
#mounting shared folders when wireless interface goes up
mount -t cifs \\\\server\\sharedfolder /media/sharedfolder -o users,noperm,credentials=/root/.smbcredentials,iocharset=utf8,uid=,gid=,file_mode=0777,dir_mode=0777
fi

```
(an idea adapted from a great [post]("http://ubuntuforums.org/showthread.php?t=1027192") from [Colie]("http://ubuntuforums.org/member.php?u=697649")=D>)

I didn't have the need to do anything about unmounting, seems that 10.10 is handling it correctly both in shutdown and in suspension modes.
Hope this helps someone else. ;)

---

### Post by DrTebi on 2013-01-27
I realize this is an old post, but in case someone is still looking for a solution to remove the duplicate samba share entries in the filebrowser, the solution is simple: Add a forward-slash after the share name in fstab:

```

//server/share/    /home/john/server/share    cifs  [...]
# here--------^

```

'found this solution here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=663140](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=663140)

---

### Post by wildmanne39 on 2013-01-27
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

