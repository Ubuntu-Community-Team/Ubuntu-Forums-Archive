---
title: "Can't mount NTFS network share in Ubuntu 11.10..."
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by del_fairley on 2012-01-07
I'm having problems mounting a shared NTFS network directory (on a QNAP NAS) from a new Ubuntu 11.10 machine (3.0.0-12-server kernel).
I have a 10.04 machine running on the same network, and I can mount the network drive fine from there. 
The 10.04 machine has the following packages & libraries installed to enable NTFS read/write support:
```
ntfs-config
ntfs-3g
libntfs10

```I can mount the network directory using the following command:
```
sudo mount -t nfs 192.168.1.100:/Qmultimedia /mnt/Qnap
```The 11.10 machine has the same packages installed:
```
ntfs-config
ntfs-3g
libntfs10

```I have enabled ntfs-config by creating a policy directory:
```
sudo mkdir -p /etc/hal/fdi/policy
```I have run the nfts-config tool:
```
sudo ntfs-config
```... and enabled NTFS write support for external devices.

When I try to mount the NTFS partition (which works fine on 10.04), I get the following error:
```
mount: wrong fs type, bad option, bad superblock on 192.168.1.100:/Qmultimedia,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```So, I still don't have NTFS support. Am I missing some other package or library to make this work on 11.10?
Thanks in advance!
-Del

---

### Post by del_fairley on 2012-01-07
*looks sheepish*
Problem solved - the issue wasn't NTFS.
As it's a network drive, I also need NFS support... doh.
Fixed by installing nfs-common:
```
sudo apt-get install nfs-common
```:-)

---

