---
title: "Ubuntu 10.10 pitiful NFS performance"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by VirtualRoot on 2010-12-20
So this is my setup:

Server1 : Asus P5NT WS, Q6600, 8GB, Open Solaris 2009.06, ZFS, 2TB Seagate LP drive, tuned with 200 NFSD threads
Server2 : Asus X58 Sabertooth, Core I7 950, 8GB, Ubuntu 10.10 X64, EXt4, 2TB Seagate LP drive, tuned with 200 NFSD threads, using  nfs-kernel-server package

Client: MSI 785GB, Athlon II X4 640, 8GB, VMware ESXi 4.1

All three servers use Intel Pro 1000 NICs on PCI-E interfaces.

I'm using the following command to test write performance:
time dd if=/dev/zero of=pt count=5000000

Solaris local disk:  1min 5 sec
Ubuntu local disk:  1min 25 sec

ESXi -> Solaris : 2 min 2 sec
ESXi -> Ubuntu:  6min  22 sec <- Holy heck what's going on here?
ESXi -> Ubuntu: 1 min 21 sec when exported with async option

Why is Ubuntu so slow when using the async option?  Solaris uses noasync and only has ~25% performance penalty over Ubuntu's async.

What gives here?  Why is Ubuntu's NFS so slow as compared to OpenSolaris when both are using sync writes?

---

