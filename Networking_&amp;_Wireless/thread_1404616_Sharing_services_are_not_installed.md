---
title: "Sharing services are not installed"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Alex F450 on 2010-02-11
Im running xubuntu on two identical machines and both need to have file sharing working. the first installed no problem and works perfectly but the second machine will not work.

On the second machine i installed it with the install button when you click of shared folders. after it installed i rebooted and it asked me to install again. I tried to install again but it just kept coming up with the install windows afterwards. I tried purging samba and reinstalling and it did not work as well.

Im kind of lost on what to do now?

---

### Post by johnson.d on 2010-02-12
You can probably try Installing the samba or NFS file sharing services using the following commands:

1) Samba

> $ sudo apt-get install samba

Let me know if you get some error messages when you attempt to install. If the installation succeeds, see if you are able to start samba service by:

> $ sudo /etc/init.d/samba restart

2) NFS

> $ sudo apt-get install nfs-kernel-server

See if there are any errors in installation and again if you are able to start the nfs service.

---

