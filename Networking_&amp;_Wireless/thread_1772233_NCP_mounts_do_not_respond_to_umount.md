---
title: "NCP mounts do not respond to umount"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by jmoseby on 2011-05-31
I have several ncp mounts.  If the novell server goes down, these mounts cannot be unmounted, nor will they remount when the novell server comes back up.  I cannot 'umount -f' to force it to unmount.  The only way I have found to recover is to force a server reboot.

Here are the relevant fstab lines:

```

#novell servers
FS1/admin /mnt/novell/FS1 ncp uid=root,gid=novell-users,mode=660,owner=root,A=FS1,passwdfile=/etc/novell-passwd     0 0
GW1/admin /mnt/novell/GW1 ncp uid=root,gid=novell-users,mode=660,owner=root,A=GW1,passwdfile=/etc/novell-passwd     0 0
DB1/admin /mnt/novell/DB1 ncp uid=root,gid=novell-users,mode=660,owner=root,A=DB1,passwdfile=/etc/novell-passwd     0 0
FW1/admin /mnt/novell/FW1 ncp uid=root,gid=novell-users,mode=660,owner=root,A=FW1,passwdfile=/etc/novell-passwd     0 0
FS3/admin /mnt/novell/FS3 ncp uid=root,gid=novell-users,mode=660,owner=root,A=FS3,passwdfile=/etc/novell-passwd     0 0

```There must be a more graceful way to handle ncp mounts when the novell server is going away and coming back.  Any comments welcome.

---

