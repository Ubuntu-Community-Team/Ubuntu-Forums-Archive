---
title: "Sharing Folders and Files"
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by gpeck157 on 2006-02-17
Hi All,

I have a laptop running Breezy and Windows XP Media (dual boot), my wife's computer running Breezy, and my daughter's computer running Windows XP Home SP2. All are sharing a broadband connection no problem. My laptop and my daughter's desktop are wireless, and my wife's computer is directly connected to the router. I want to share folders and files between all three computers. Is there a "how to" that explains how to share files and folders between Breezy to Breezy (my computer to my wife's and hers to mine) and Breezy to Windows XP Home and Windows XP Home to Breezy (daughter to parents and back)?

I'm not having any problem at all connecting to the internet, nor any other networking problems. I just want to know how to share folders and files on a peer to peer home network with all of us connecting through a Linksys router between Windows and Linux.

Thanks...

---

### Post by bscbrit on 2006-02-18
You can share files between all three computers using SAMBA:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

The fact that some are wireless and some are wired is irrelevant.  They are all on the same network which is all SAMBA will need.

You can also share files/folders between linux computers using NFS but that only complicates matters in your particular case.

---

### Post by gpeck157 on 2006-02-19
[QUOTE=bscbrit]You can share files between all three computers using SAMBA:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Thanks,

I have a couple of questions. If the Windows folders on the other machine are not password protected then it is not required to create the .smbcredentials file?

For non-password protected files:

Add this line to /etc/fstab:

//192.168.0.1/linux       /media/sharename   smbfs   rw    0   0

This I.P. address is the address of the Windows machine and the shared folder? If so, does each of the machines require a permanent static I.P.? If not, how is it addressed? 

Since the /linux part of this line is the shared folder, does one need to put the entire path or just the name of the folder?

Under the /media/sharename am I correct in assuming that the "sharename" is the Windows sharename given to the folder on the Windows machine?

Thanks...

G

---

### Post by bscbrit on 2006-02-19
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)

The 2 links above should answer all of your questions.  However, come back if there is a specific issue that you cannot resolve.  Good Luck

---

### Post by gpeck157 on 2006-02-20
Thanks, I'll check them out and get back to you if need be. I appreciate the help.

G

---

