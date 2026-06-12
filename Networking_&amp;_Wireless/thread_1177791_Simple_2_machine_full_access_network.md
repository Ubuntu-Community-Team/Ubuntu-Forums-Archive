---
title: "Simple 2 machine full access network"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by vishnu on 2009-06-03
I'm having some issues with network file access on my home network.

SETUP:
   PC1 = Intrepid
   PC2 = Jaunty
   PC1 has a folder called "xfer" which is shared.
   PC2 can successfully access this folder and has read/write permission.

ISSUE:
   PC2 places a file into the PC1 "xfer" folder
   File is read/write for everyone
   PC2 accesses the file but it is read only


Is there a simple way to setup a share so that both users in samba workgroup have full access by default to any and all shares that are setup?

---

### Post by dmizer on 2009-06-03
Since both of your computers are Ubuntu, I highly suggest you use NFS instead of samba, as it's much easier to configure correctly.

Please see the 4th link in my sig for a good howto. You'll need to configure both computers as both a client and a server.

---

### Post by vishnu on 2009-06-04
solved.  needed the following in smb.conf

security = share
guest account = pcuser 
where pcuser is the user name user for that pc 

thanks for info dmizer. unfortunately i also have a hacked xbox that relies on a samba share to see video files on the linux pcs.

---

