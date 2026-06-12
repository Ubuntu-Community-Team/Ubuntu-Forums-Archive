---
title: "Samba share and Vista machine"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by ks07 on 2009-09-03
Just recently I decided to set up a samba share on the home network. I went to the folder I wanted to share in root nautilus (/dev/sdb6, formatted as fat32 mounted at /media/shared) and right clicked > properties > share > share this folder.

I was asked to install samba and restart, so I did. No problems reported. I then returned to the folder and checked the other two boxes, guest access and allow write. After saving the changes, I edited smb.conf to put my ubuntu box into the correct workgroup and restarted. 

All well and good, until I booted my Vista machine and tried to access it. The PC appeared in the workgroup, but trying to open the folder gives an error stating 'access denied'.

I am running Ubuntu 9.04 and Vista SP1. Any ideas? :confused:

---

### Post by Iowan on 2009-09-03
Sounds like you may not have generated a Linux and/or Samba username/password (although "guest" would seem to negate the need for creating user). The Windows user will need to have a Linux account AND a Samba account.  I can never remember if it's **adduser** or **useradd** to create a Linux user, but then **smbpasswd** can be used to create/modify a Samba user.  More details via **man smbpasswd**.

May still need to activate "guest" account in */etc/samba/smb.conf*.

---

### Post by ks07 on 2009-09-04
> **Iowan said:**
> Sounds like you may not have generated a Linux and/or Samba username/password (although "guest" would seem to negate the need for creating user). The Windows user will need to have a Linux account AND a Samba account.  I can never remember if it's **adduser** or **useradd** to create a Linux user, but then **smbpasswd** can be used to create/modify a Samba user.  More details via **man smbpasswd**.

May still need to activate "guest" account in */etc/samba/smb.conf*.
Was about to do that, until I tried changing permissions on the folder. After failing miserably, I googled my problem and lo and behold it was all because it was FAT32. One word in a search makes all the difference.

Thanks for the help, I am going to try and follow [this posters]("http://ubuntuforums.org/showthread.php?t=273189") example to get it working. Will post back here if I run into problems.

---

