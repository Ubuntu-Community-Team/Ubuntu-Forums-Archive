---
title: "LAN connection in 8.10"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by status001 on 2009-04-17
I'm using Ubuntu 8.10. I can connect internet using "sudo pppoeconf". But I cannot find any pc in Network places. I cannot use anykind of service of LAN. Cannot see any group like workgroup or mshome. I installed Samba, but didn't successful. Please give me an easy instruction to solve this problem. And please do not redirect me to any other page. If you want to help me, then please write it in this page. Thanks.

---

### Post by Crafty Kisses on 2009-04-17
Hey there, I just want to check a couple of things here, what are the results of the following command?
```
smbd -V
```
I wouldn't also mind seeing the results of this as well:
```
cat /etc/samba/smb.conf
```

---

