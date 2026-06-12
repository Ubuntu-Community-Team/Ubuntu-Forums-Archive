---
title: "Can't see Windows PC's in the workgroup"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by shuli on 2011-07-07
Hi everyone,

Total newbie here. I'm running Ubuntu 11.04. Here's my issue:

I'm the only Ubuntu PC in my office, the rest are running Win XP. I have Samba installed and a share setup and access to it from the other computers is working fine. My problem is that none of the XP PC's show up when I browse the workgroup in Nautilus. Here's my smb.conf:

```
[global]
workgroup = callcenter
netbios name = shuli-pc
server string = %h server (Samba, Ubuntu)
wins support = yes
security = share
name resolve order = lmhosts wins bcast host

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
security = share
restrict anonymous = no
domain master = no
preferred master = no

[testshare]
case sensitive = no
guest ok = yes
path = /home/shuli/testshare
read only = no

```

Any help would be greatly appreciated.

---

