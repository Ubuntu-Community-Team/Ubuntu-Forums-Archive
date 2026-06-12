---
title: "CIFS mount in fstab to samba 3.0.24"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by dolphs on 2009-06-03
Hi I experience problems connecting from Xubuntu 9.04 to a samba server ( also linux ). The idea is to get there anonymously with rwx rights and this works fine from my Win machine, I can easily connect to the set top box without supplying user/password, so with rwx rights.

Yet on my linux laptop, which has Xubuntu 9.04, I want to be able to create a cifs mount to that same box while booting up. At this moment /etc/fstab on my laptop shows " //192.x.y.z/media/hdd /media/stb cifs _netdev,guest,rw,soft,file_mode=0777,dir_mode=0777,noperm 0 0 " 


Which results in:
root@linuxdesktop:/media/stb# mount -a
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


smbclient -L "192.x.y.z" -U%

Domain=[HOME] OS=[Unix] Server=[Samba 3.0.24]

Sharename Type Comment
--------- ---- -------
Configfiles Disk Configuration files - take care!
Harddisk Disk The harddisk
IPC$ IPC IPC Service (DreamBOX dm8000 network services)
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.24]

Server Comment
--------- -------
A8930
DM8000 DreamBOX dm8000 network services

Workgroup Master
--------- -------
HOME      DM8000


I must overlook something because as you can see my Windows machine (A8930) can access /media/hdd on the stb, also NFS mount works but I like to find out where it goes wrong mounting with cifs

Please advise.

---

### Post by Iowan on 2009-06-03
I presume you've seen [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To?

---

### Post by dmizer on 2009-06-03
Additionally, it may help to refer to the 1st link in my sig for proper configuration of 192.x.y.z (DM8000)

---

### Post by dolphs on 2009-06-04
Yip howto is known. Just will fool around little more as it should work. cheers for replies

---

