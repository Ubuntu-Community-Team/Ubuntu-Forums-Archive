---
title: "nmcli select default connection"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by mad_ady on 2010-12-23
I've noticed that nmcli can list and show you which is your default connection:

```

adrianp@frost:~$ nmcli con status
NAME                      UUID                                   DEVICES    SCOPE    DEFAULT  VPN  
Provider1 - eth0          ca62dd01-7225-4939-a5e8-bfc07169373b   eth0       system   yes      no   
Intranet - eth1           34188c63-1604-4c09-90ab-45e0baae5615   eth1       system   no       no   
Provider2 - eth5          23e096e2-14a8-4ab3-935a-b20e6045111f   eth5       system   no       no 

```

The connection marked with Yes has a default gateway installed in the routing table. I would like to be able to mark a different connection (e.g. Provider2) as default and have NetworkManager replace the default gateway with Provider2's gateway without having to shut down Provider1. I'd like to do this from nmcli (to be able to setup a script to do it when needed).

Is this thing possible/planned in the future?

Thanks

---

