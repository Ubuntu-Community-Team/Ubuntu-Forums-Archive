---
title: "slow samba/ftp reads, writes vary"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by xxxlalala on 2012-05-01
Hello,
i am connecting two PCs in my home network right now via  1GbEthernet. One is running Ubuntu Server 12.04 LTE the other is a  Windows 7 machine. 
I want to use the Server as Backup, but also as regular Storage. 
The  Server hat 3 2TB Drives in a ZFS raidZ array, wich gives me arround 120  MB/s reads to the local non ZFS drive (7200rpm HDD wich is maxed out  then), and arround 100 MB/s writes (also from the non ZFS HDD). I tested  that by copying Files via the console.
Via Samba or sFTP i get arround 78-90 MB/s writes to the Server sometimes only precisely 64 MB/s.
but constantly only arround 30 MB/ reads. 
i tested with iperf (with a live cd on the windows machine) and it hat constat 110 MB/s.
Is there anything i can do about that ?
i searched everywhere but everyone has problems with writes i have the opposite

---

### Post by xxxlalala on 2012-05-04
noone ?

---

### Post by xxxlalala on 2012-05-05
i did all the guides, ftp is 110 MB/S up and down.
is samba realy that slow ?

---

### Post by ppparadox on 2012-05-05
Actually there are some performance tweaks you can apply to your smb.conf
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

I'm going by memory here so i suggest you look them up before you apply them.

---

### Post by kid1000002000 on 2012-06-21
Having exactly the same problem. Anybody find a solution?

---

### Post by posicat on 2012-10-17
I'm having the same issues, across several protocols, NAT, Samba, FTP, Minecraft, even RDP, the connection between my sever and desktop is running at about 100-200kb/s.

Also I'm noticing the same effect on my Android phone, my TV (Netflix and Youtube) and more.  Desktop is Windows.

Ubuntu server is a 16-core Opteron 6212 with 16gb ram, I originally had e1000e built-in net cards, but replaced them with a Broadcom dual-ethernet card, with absolutely no change in speed.

---

