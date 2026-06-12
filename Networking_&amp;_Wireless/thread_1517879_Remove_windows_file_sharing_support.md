---
title: "Remove windows file sharing support"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by Vexiphne on 2010-06-25
Hi.

I've just installed Ubuntu on all our computers at home. (1 desktop and 2 laptops.)

I'm a total noob at this and when I installed network sharing I accidentally installed file sharing for Windows networks to. 
How can I remove windows networks file sharing and keep only ubuntu's own network file sharing?

We have wireless network and only Ubuntu machines connected to it :)

---

### Post by linux-hack on 2010-06-25
the windows file sharing module or software is samba.

if you want to uninstall it just do :

```
sudo apt-get purge samba
``` that way the config files will be deleted also.

Hope this helps

---

### Post by Iowan on 2010-06-25
You may need to install filesharing for Linux. [NFS]("http://ubuntuforums.org/showthread.php?t=249889") is native, but there are a couple more - like [vsFTP]("http://ubuntuforums.org/showthread.php?t=218630") or [proFTPd]("http://ubuntuforums.org/showthread.php?t=79588")

---

