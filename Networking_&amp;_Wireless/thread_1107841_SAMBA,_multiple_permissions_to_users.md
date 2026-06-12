---
title: "SAMBA, multiple permissions to users"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by CR34M3 CR4CK3R on 2009-03-27
Hi, I've recently set up a server for running a wiki and to act as a file server for other pc's running Windows. The wiki is up and running without problems, but the samba shares are not working as I would like. 

If someone could please help me or at least refer me to a guide, I would greatly appreciate it.

[Running Ubuntu intrepid]

The shares should operate as follows:
* userA, userB and userC will access the server. (users already created)
* the shares are located in /data/sambashares/... (with harddrives automatically mounting to folers within this foler)
     with the following structure:
        /data/sambashares/folderA
                      .../folderB
                      .../folderC
* userA should have read/write access to all three folders
* userB should have only read access to folderB
* userC should have read/write access to folderC

In all cases authentication will be required.


Please help me out, as I'm not sure how to specify multiple permissions in the smb.conf file.

Thanks,

-André

---

