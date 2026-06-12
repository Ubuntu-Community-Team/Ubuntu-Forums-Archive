---
title: "fstab samba mount, sub-directory permission issues"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by midiman127 on 2010-04-21
I have a weired problem with the solution probably staring in my face. I just cannot find it... Here my setup:

- Server on 192.168.1.116 running kubuntu 9.10 and samba
- Different clients in private network using ONE share as a common server drive. 
- Windows 2000, XP and 7 all work connecting to share with credentials
- The linux systems are using the followin line in fstab:

//192.168.1.116/theshare /media/server cifs username=shareuser,password=sharepwd,iocharset=utf8,codepage=cp437,uid=1000,gid=1000 0 0

If I use the command line on the linux client (9.10; 386 or amd64) I can create multi-level subdirectories on the server with the mkdir command.

mkdir /media/server/level1
mkdir /media/server/level1/level2

But if I do this:

cp /tmp/level1 /media/server -r

and level1 has a sub sub-folder level2 the command fails. Only level1 gets created and level 2 is missing. The error I get is:

cp: cannot create directory `/media/server/level1/level2': No such file or directory


THOUGHTS? THANKS!!!

---

