---
title: "nfs mount in fstab doesn't work (does in 10.04)"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by hvn on 2010-11-27
Hi,

I installed 10.10 yesterday and all seemed fine. Now I made an NFS mount in /etc/fstab like I use to in 10.04 

Kaapstad:/admin /mnt/Kaapstadadmin      nfs     defaults        0       0

but get this:

# mount -a
mount: wrong fs type, bad option, bad superblock on Kaapstad:/admin,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
#

In /mnt, /etc/hosts everything is set as should be. In other posts I'm reading other problems with nfs as well. Is there a bug?

---

### Post by SeijiSensei on 2010-11-27
Install the "nfs-common" package on the client.

---

### Post by hvn on 2010-11-27
> **SeijiSensei said:**
> Install the "nfs-common" package on the client.

Thank. Solved.

---

