---
title: "SMB Shares from server"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by BULLIT22 on 2010-08-14
Hey everyone,

I'm having a bit of an issue. I have 7 HDD's shared over Samba from a Ubuntu 9.10 server. I'm having trouble getting access to them on all my pc's except for 2(out of the 4). On all the pc"s I get this when I type this command smbtree,

WORKGROUP
    \\UNIVERSE               universe server (Samba, Ubuntu)
cli_start_connection: failed to connect to UNIVERSE<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\DEADPOOL-DESKTO        deadpool-desktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to DEADPOOL-DESKTO<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

I even get this on one of the PC's I can connect with. Not sure what is going on.... Any help would be great. Thanks. 

P.S. all pc's have the Default WORKGROUP.

---

### Post by drdos2006 on 2010-08-14
I have had the same sort of problem ever since my last update.
My problem is unable to access the samba shares on my server. So I downloaded and installed the Graphical Firewall ( gufw ) so I could easily switch the firewall on and off when I needed to connect to the shares. With the firewall off smbtree works, firewall on, nothing is shown.

It is a good thing I use NFS as well as samba to backup my files.

regards

---

### Post by BULLIT22 on 2010-08-14
Sounds good, except for I can always see my share on 2 of my PC's, both running Ubuntu as well. Just does not make any sense why the other 2 can't.

---

### Post by BULLIT22 on 2010-08-15
Anyone else....? I can connect to the server by entering it manually.

---

