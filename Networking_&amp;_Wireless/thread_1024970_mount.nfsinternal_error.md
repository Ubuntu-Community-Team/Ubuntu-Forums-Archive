---
title: "mount.nfs:internal error"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by ndefontenay on 2008-12-29
Hi.

I'm trying to share my home directory between my desktop PC and a vaio laptop using wireless successfully \o/

Here's what I've done on the server side:

1) Edited /etc/exports content as follow:
```
 gksudo gedit /etc/exports
```

/home/nicolas 192.168.1.2(rw,no_root_squash,async)
/home/nicolas 192.168.1.4(rw,no_root_squash,async)
/home/nicolas 192.168.1.5(rw,no_root_squash,async)
/home/nicolas 192.168.1.3(rw,no_root_squash,async)

```
sudo exportfs -a
```

exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.2:/home/nicolas".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.4:/home/nicolas".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [4]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.5:/home/nicolas".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [5]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.3:/home/nicolas".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

2) here's what I've done on the client side:
```
sudo mkdir /media/nicolas
sudo mount 192.168.1.3:/home/nicolas /media/nicolas
```

mount.nfs: internal error

--------

Why do I have internal error and how can I debug this? I've also tried on cable network, it doesnt' work better.

---

### Post by ndefontenay on 2008-12-29
Also my hosts.deny looks like this:

portmap: ALL
lockd: ALL
mountd: ALL
rquotad: ALL
statd: ALL

and my hosts.allow looks like this:

portmap: (192.168.1.2,192.168.1.3,192.168.1.4,192.168.1.5)
lockd: (192.168.1.2,192.168.1.3,192.168.1.4,192.168.1.5)
mountd: (192.168.1.2,192.168.1.3,192.168.1.4,192.168.1.5)
rquotad: (192.168.1.2,192.168.1.3,192.168.1.4,192.168.1.5)
statd: (192.168.1.2,192.168.1.3,192.168.1.4,192.168.1.5)

I've tried with hosts names but I suppose I have to add the IPs and hostname to the hosts file first and it doesn't solve anything because the IPs are dynamics...

I'm following this how-to:

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

tried pretty much everything in it. reconfigured the portmap etc... to no avail.

---

