---
title: "Help with mounting Mac network share on Ubuntu"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by NewYork12436 on 2008-12-04
I'm trying to mount a Mac network share on Ubuntu (Dapper, ver 6.06) to grab files for conversion in a Linux program. Unfortunately there are many picture files, possibly in excess of a TB altogether, so I need to grab them from the network share individually where the Linux program will convert them to a smaller size and store them on a local RAID.

The problem is I'm not finding any way to mount the mac drive so I can access its contents. The Mac's file sharing is enabled for all types (smb included). The setup is relatively simple, both machines are connected via a gigabit switch. In Ubuntu I can browse the Mac's drives simply using the smb://192.168.1.100 command, but this won't be available for browsing from the linux program.

I've installed samba and tried every combination of mount smbfs I can think of. The command "mount -t smbfs //192.168.1.100 /mnt/windows -o rw,username=xxx,password=xxx" simply brings up the usage list for the smbfs commands.

If I use the command "mount.smbfs ........." I get the same result.

If I try using "cifs" as the filesystem  I get "mounting the DFS root for a particular server is not implemented yet"

Now I assume that using another filesystem may be faster such as ftpfs or even afp directly with netatalk, but what are your suggestions??

Thanks!

---

