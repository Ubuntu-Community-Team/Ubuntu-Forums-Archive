---
title: "new Linux user - mount command not working for me, error -22"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by navboy on 2009-02-18
Hello, i got Ubuntu installed, and my first task is to try to go into the terminal and connect to a windows share on my small network (to a Win XP Home PC with a shared folder than i regularly hit from another XP machine and sometimes from a Mac laptop using smb:// in Go-Connect to Server ...

i created a mount point /mnt/Bobpc and doing the following returns a wrong filetype, Bad Superblock etc message:


"$ sudo mount -t cifs //Bobpc/stevestuff /mnt/Bobpc"

all the Googling i've done produces contraditory results - use samba, don't use samba, use cifs (when i tried to use smbfs as the type it said it was being deprecated, and also i can't seem to find the "smbfs" app with get-apt that shows up in so many posts.

I notice i have an /sbin/mount.ntfs file but nothing like an /sbin/mount.cifs helper file - does Ubuntu not come with the ability to hit Windows share in the default install?   I'm so confused, this seems like it should be easier.  Any help greatly appreciated!

-steve

PS. in FF i can browse to smb://Bobpc/stevestuff and get a directory listing, no problem

EDIT: i take that back, i was using get-apt wrong, so now i installed smbfs, which is supposedly being deprecated, but now when i use cifs i get mount error 111 = connection refused, yet i cna go to the GUI and see the windows network, Bobpc, and the folder on it stevestuff

---

### Post by navboy on 2009-02-18
nevermind, i figured it out. Had to install winbind, had to use IP until i just now edited the /etc/nsswitch.conf to add "wins" to the line, after files for netbios name resolution

now what i'm not clear on is, if i use the GUI to go to a remote windows machine and open a file on it, is there a mount point or connection created that can be used in the terminal, or can you not get to that connection in the terminal without manually mounting a remote share there?


if anyone knows, i also have this exact same question for when you're on a Mac ...

---

