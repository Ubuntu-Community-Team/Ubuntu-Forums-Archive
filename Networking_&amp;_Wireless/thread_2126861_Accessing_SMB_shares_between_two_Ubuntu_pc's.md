---
title: "Accessing SMB shares between two Ubuntu pc's"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by jrohde on 2013-03-18
Hi

I have a server installed with Ubuntu 12.10 and Samba, and I have a workstation also installed with Ubuntu 12.10. Both pc's have joined the same workgroup, but I am unable to gain access the the home share on the server.

What is the best way to access shares on the server?

Thanks
Jakob

---

### Post by JRV on 2013-03-18
You don't need samba.
Try this:```

nautilus sftp://USERNAME@HOSTNAME/home/USERNAME

```

---

