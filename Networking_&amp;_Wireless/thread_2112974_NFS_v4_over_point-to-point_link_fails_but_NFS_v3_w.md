---
title: "NFS v4 over point-to-point link fails but NFS v3 works"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by arbuntoo on 2013-02-06
Hi

I've configured a point-to-point link to an NFS server which works with NFS v3 but not with NFS v4 (mount is ok but ls hangs). Importantly NFS v4 works from the same server over non-direct links so it's not NFS v4 itself which fails, just NFS v4 over this link.
I can see traffic on port 2049 with tcpdump so the link itself is ok too. Any ideas?

The link is configured like this:
auto eth2
iface eth2 inet static
 address 192.168.1.100 (that's my address)
 broadcast -
 pointopoint 192.168.1.1 (that's the server address)
 mtu 8150

---

