---
title: "Mounting NFS during boot hangs system"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by martijntje on 2009-08-25
I have set up a NFS server. The goal is, among other things, to export /home and some data directories from this server. I have created an entry in /etc/fstab. Mounting with "sudo mount -a" works fine, however, during boot the system hangs with the message

```
mount.nfs4: can't get address for bart.lan
```The line in /etc/fstab is as follows:

```
bart.lan:/data  /var/data       nfs4            rsize=8192,wsize=8192,sec=krb5,_netdev  0       0
```

---

### Post by dmizer on 2009-08-25
Do you have a wired or wireless connection? Do you ever use wireless?

---

### Post by martijntje on 2009-08-25
For this, I do not use wireless.

---

### Post by dmizer on 2009-08-25
Install gnome-network-admin and then uninstall network-manager

Manage your network from system > administration > network

---

