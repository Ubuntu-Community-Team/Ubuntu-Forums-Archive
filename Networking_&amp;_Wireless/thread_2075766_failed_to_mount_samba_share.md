---
title: "failed to mount samba share"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by DrScum on 2012-10-24
I have a network with a Ubuntu 10.04 and a Ubuntu 12.04 client. I want to mount a samba share from the 12.04 client on the 10.04 machine in order to perform directory synchronization.

sudo mount -t cifs //192.168.0.174/SJ-2012-13 /media/SJ-2012-13 -o username=xxxxxxx,password=xxxxxx yields:

retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

however, smbclient -L 192.168.0.174 yields:

Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	NewData         Disk      
	SJ-2012-13      Disk      
	IPC$            IPC       IPC Service (xxxxxx server (Samba, Ubuntu)

so the share I am trying to mount is available but I can't mount it. Beats me!

Any help is appreciated.

---

