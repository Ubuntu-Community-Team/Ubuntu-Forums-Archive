---
title: "Problem with SAMBA"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by beont on 2008-12-05
Hi all,
I have Ubuntu Server 8.04 (with Desktop environment)

  I have installed SAMBA n SMBCLIENT and SMBFS
  I made a folder and added at smb.conf

[I]
	comment = I disk
	path = /var/i
	guest ok = yes
	browseable = yes
	read list = @IREAL
	write list = @IREAL
	read only = no
	create mask = 0775
	directory mask = 0775


This works fine for other computers with windows XP on the network.

Now I want to mount for an UBUNTU Desktop 8.04 this folder
and i type

sudo mount -t smbfs -o username=ireal //192.168.0.10/var/i /mnt/i
 and I get an Error 8 no such device or address

note that at the my places section under Network  smb:  i can see the Ubuntu server 8.04 under the IREAL workgroup but i can not open it or see any of its contents

how can i fix this?

---

### Post by Iowan on 2008-12-05
[This]("http://ubuntuforums.org/showthread.php?t=288534") How-To might help.

---

### Post by LowSky on 2008-12-05
The link you providd doesn't work

---

### Post by superprash2003 on 2008-12-05
you havent specified password mount -t smbfs -o username=<name>,password=<passwd> //sambashare /mountpoint

---

### Post by Iowan on 2008-12-05
I fixed the link - it's also the same one as in my sig.

---

### Post by beont on 2008-12-06
I fixed it I think its a bug that ubuntu samba has. computer name cannot be the same as for the workgroup name. I had workgroup IREAL and Host name IREAL (in windows XP I could double click on the IREAL workgroup and then dble click on IERAL computer and view its contents but from the Ubuntu desktop under smb://ireal/ (which was the workgroup) a double click on Ireal pc had as a result the same path

thank you all for your replies 
glad to join the community

---

