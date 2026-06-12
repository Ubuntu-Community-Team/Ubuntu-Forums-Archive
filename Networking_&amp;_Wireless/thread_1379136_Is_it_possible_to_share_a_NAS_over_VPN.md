---
title: "Is it possible to share a NAS over VPN?"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by trstn on 2010-01-12
Ok, I'm a bit of a learner when it comes to ubuntu servers but getting there.

I've set up a karmic machine as a gateway/dhcp/etc using a machine with two internal hard drives.

I've just made the huge victory of sharing the second hard drive over VPN, the problem is though I want to share the NAS we have in the office over the VPN.

So.... internal harddrive is :

/media/secondrive

NAS is mounted at:

/media/edge

I've added both to /etc/samba/smb.conf

```
[edge]
    comment = Ubuntu edge server share
    path = /media/edge/
    browsable = yes
    guest ok = no
    read only = no
    create mask = 0755

[share]
    comment = Ubuntu secondrive
    path = /media/secondrive/
    browsable = yes
    guest ok = no
    read only = no
    create mask = 0755
```

But when I try to chown the folders to enable users to access them both, well, works fine on the internal drive but not so on the NAS.

```
tristanw@ubuntu:/media/secondrive$ sudo chown nobody.nogroup /media/edge
chown: changing ownership of `/media/edge': Permission denied
```

So.... is there any way to share the NAS drive?

---

