---
title: "slow copy speed to network volume"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2011-05-04
in mi fstab file i mount a smb file server at boot. the code is:

//<ip address>/data /home/eng-2/NAS smbfs credentials=/home/eng-2/.smbcredentials,dir_mode=0775,gid=1000,uid=1000 0 0

transfer rate to the server is approx 100 KB/s
whilst transfer rate from the server 16 MB/s

if i mount it from Places>connect to server. both to and from speeds are 16 MB/s

Why is it so slow when mounted through fstab?

---

### Post by Ceiber Boy on 2011-05-06
Bump!

---

### Post by Ceiber Boy on 2011-05-07
got it! changed smbfs to cifs. i.e

//<ip address>/data /home/eng-2/NAS cifs credentials=/home/eng-2/.smbcredentials,dir_mode=0775,gid=1000,uid=1000 0 0

i guess thats job done unless someone can explain the huge difference in the transfer rates between the two protocols.

---

