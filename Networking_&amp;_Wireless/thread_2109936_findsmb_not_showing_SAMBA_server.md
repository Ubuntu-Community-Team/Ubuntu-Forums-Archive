---
title: "findsmb not showing SAMBA server"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2013-01-28
when I am logged into my workstation running Xubuntu 12.04 64bit if I issue 
```
findsmb
```
it only shows the localhost
```
findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.3     CORE2DUO       [LINUX] [Unix] [Samba 3.6.3]

```
what's weird is that there is a Western Digital MyBook World Edition 1TB NAS on the network as well as my main server running Ubuntu 10.04.4 which has a SAMBA server running. When I run findsmb on the Ubuntu 10.04.4 server this is what it shows
```
findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.3     CORE2DUO       [LINUX] [Unix] [Samba 3.6.3]
192.168.0.5     DELL          *[LINUX] [Unix] [Samba 3.4.7]
192.168.0.39    CIRCLE         [	LINUX         ]

```
so why does Xubuntu 12.04 64bit NOT show DELL and CIRCLE when I run findsmb on it? ANy help would be appreciated.

---

