---
title: "NFS mount before network start?"
date: 2005-02-09
forum: Networking &amp; Wireless
---

### Post by michele on 2005-02-09
Hi

I have the impression that at boot the system tries to mount nfs systems before bringing up the network. Can anybody confirm?

Thanks

---

### Post by alastair on 2005-02-09
I'd be amazed that no one had noticed this yet. I only have a laptop (testing Ubuntu) but a quick check of the init links seems to be in order :

# find /etc/rc* -name '*netw*'
/etc/rc0.d/S35networking
/etc/rc6.d/S35networking
/etc/rcS.d/S40networking

# find /etc/rc* -name '*mount*'
/etc/rc0.d/S31umountnfs.sh
/etc/rc0.d/S40umountfs
/etc/rc6.d/S31umountnfs.sh
/etc/rc6.d/S40umountfs
/etc/rcS.d/S02mountvirtfs
/etc/rcS.d/S36mountvirtfs
/etc/rcS.d/S35mountall.sh
/etc/rcS.d/S45mountnfs.sh

So ... networking appears to start at #35 generally, and NFS at #45.

I have no NFS disks to mount as a test though (can't be bothered to check ...).

Any error/error logs would help with a specific problem perhaps.

---

