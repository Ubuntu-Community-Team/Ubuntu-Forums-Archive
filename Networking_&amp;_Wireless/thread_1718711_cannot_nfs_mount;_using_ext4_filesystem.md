---
title: "cannot nfs mount; using ext4 filesystem"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by j1mw3b on 2011-03-31
I have Ubuntu 10.04.2 LTS on my Thinkpad T42.
I seem be unable to NFS mount a remote filesystem - get the following message:

! jlap->root:/root>#sudo mount 192.168.6.4:/seagate /seagate
mount: wrong fs type, bad option, bad superblock on 192.168.6.4:/seagate,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have the following mount helpers:
/sbin/mount.fuse  /sbin/mount.ntfs-3g    /sbin/mount.smbfs
/sbin/mount.cifs  /sbin/mount.ntfs  /sbin/mount.ntfs-fuse

Have two NFS servers: OpenWrt Kamikaze and Debian 6.0.

Each of these servers can mount each others exported filesystems.

The NFS client Ubuntu laptop is using ext4 filesystems and I am trying to mount the remote (ext3 on Debian server, ext2 on OpenWrt server).

Is ext4 the issue, or am I missing some type of mount helper?  I looked with Synaptic and found none.

I started using ext4 because failed hibernate destroyed my root filesystems at least 3 times and hoping ext4 might help.

Thanks,

Jim

---

