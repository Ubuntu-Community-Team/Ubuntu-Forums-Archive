---
title: "[SOLVED] networking with windows"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by xly15 on 2008-12-22
I just installed Ubuntu 8.04. I need to network with my windows network. How do I do this?

---

### Post by DieB on 2008-12-22
probably this might be a hint:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by namdung on 2008-12-22
> **xly15 said:**
> I just installed Ubuntu 8.04. I need to network with my windows network. How do I do this?

To access Windows Share folder:

Press : Alt+F2
Type : smb://ipaddress/share (where ipaddress is the IP address of Windows PC and share is the name of the share folder) and click Run. 

You might need to provide credentials depending on the folder rights.

The Windows PC should also be available in Places-->Network

Hope this helps.

---

### Post by xly15 on 2008-12-22
thanks DieB that helped alot.

---

