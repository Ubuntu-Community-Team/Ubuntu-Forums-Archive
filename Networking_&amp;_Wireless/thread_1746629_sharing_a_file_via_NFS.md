---
title: "sharing a file via NFS"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2011-05-02
Is it possible to share a file via NFS? Or only the folders can be shared?

For example I have shared /opt like this in /etc/exports
```
/opt                 192.168.1.0/255.255.255.0(rw,no_subtree_check,sync,no_root_squash)

```
and in the client's /etc/fastab I wrote:
```
192.168.1.1:/opt   /opt   nfs defaults 0 0
```

It is ok and work fine. How about sharing a file? What should I write in the /etc/fstab?

---

