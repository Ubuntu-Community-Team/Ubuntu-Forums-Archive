---
title: "Connect from Mint desktpo to DFS share"
date: 2019-07-30
forum: MINT
---

### Post by serozha-x on 2019-07-30
Hi everybody!

In our company we decided to migrate user PC from  Windows to Linux Mint. But we have received problem. We can't connect to  DFS resources on our servers. 
We tried many variants to resolve  this problem. And somehow it have start works... But i connect to some  DFS resources. Not all. We don't understand why it works with SOME  resources.

Maybe can someone tell me how resolve this issue? Maybe someone have variant to force it work properly?

---

### Post by wildmanne39 on 2019-07-30
Hello and welcome to the forum.

*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by TheFu on 2019-08-01
I know nothing about DFS.

The native file server for all Unix-like OSes is NFS.  You should use that with centralized user management so userids and groupids are unique across all the different systems.  As a fallback, you could setup samba servers on Linux to replace the DFS.  Both samba and NFS can be used concurrently, to share the same storage.

Google found this: [https://www.activedirectory.ncsu.edu/ou-admins/ad-support-topics/mount-dfs-shares-within-linux/](https://www.activedirectory.ncsu.edu/ou-admins/ad-support-topics/mount-dfs-shares-within-linux/) .... looks like DFS is AD+CIFS+Kerberos.  Ewwww. I feel dirty.
NFS is much easier ... well, until you add Kerberos into that for NFSv4, which is probably a really good idea.

FreeIPA is a replacement for AD, BTW.

---

