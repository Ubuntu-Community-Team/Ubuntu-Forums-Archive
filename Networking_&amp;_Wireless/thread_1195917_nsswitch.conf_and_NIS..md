---
title: "nsswitch.conf and NIS."
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by muxecoid on 2009-06-24
I do not know neither what NIS nor NSS I just want a problem solved...

 I do not have NIS and just create the same username with the same UID and password on all local machines (there are only 3 of them so far so it is NP. getpwnam_r(3C) fails to get the needed password for user on other local machine. I want to solve this without installing NIS.

Here is nsswitch.conf

```
passwd: compat
group: compat
shadow: compat

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
networks: files

protocols: db files
services: db files
ethers: db files
rpc: db files

netgroup: nis
```

No I do not understand what I just said, here is the mailing list thread where I was told to ask this on distro forums: [http://gridengine.sunsource.net/ds/viewMessage.do?dsForumId=38&dsMessageId=203283](http://gridengine.sunsource.net/ds/viewMessage.do?dsForumId=38&dsMessageId=203283)

---

