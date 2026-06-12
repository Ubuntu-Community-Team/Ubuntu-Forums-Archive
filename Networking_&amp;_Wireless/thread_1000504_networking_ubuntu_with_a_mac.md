---
title: "networking ubuntu with a mac"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by AvvY on 2008-12-03
I'm still relatively new to both mac and Ubuntu, so I'm not sure where to start in regard to networking my two machines. I know it has something to do with Samba, and have that installed on Ubuntu, but not sure where to go from there. I've done networking with WinXP before, but never with linux/mac. It is a wired ethernet network through a router. I would like to access the hdd's in the Ubuntu machine from the mac primarily.

Thanx

---

### Post by prshah on 2008-12-03
> **AvvY said:**
> not sure where to start in regard to networking my two machines. I know it has something to do with Samba

See [this post]("http://ubuntuforums.org/showpost.php?p=4904711&postcount=4") for a step-by-step guide to use Samba network shares on your network.

You need not just use samba, though. You can also use other networking such as NFS (Networking File System) or scp (Secure Copy) but each varies according to your actual use. For example, scp is good for a single, one-shot networking operation to xfer files from one computer to another. In contrast, NFS (or Samba) is recommended when you want persistent network connections between two computers.

Post back if you need more details.

---

### Post by m_l17 on 2008-12-03
You can also setup an ftp server in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd]("http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd")

To connect use any ftp client software on the mac. Like [_Cyberduck_]("http://cyberduck.ch/")

---

