---
title: "USB Drive not being able to share through NFS and AUTOFS"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by ph.gachoud on 2013-01-20
Really borring situation, I have a USB Drive which is attached to my tower by autofs. When I want to share it with NFS and mount it to my laptop or whatever device @ home, I'm not able to do it. It works with samba but not NFS. I dont want to do it the tricky "windows" way to share my files through my network between 2 ubuntu workstations!
My configuration is following:
**Tower (Server): **
```
pg@pipoTower: ~/locations$ cat /etc/exports 
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/pg 192.168.1.0/16(rw,sync,no_subtree_check) 
/var/autofs/removable/usbData 192.168.1.0/24(ro,sync,no_subtree_check) 
pg@pipoTower: ~/locations$ cat /etc/auto.master
#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc  /etc/auto.misc --timeout=60
#/smb   /etc/auto.smb
#/misc  /etc/auto.misc
/net    /etc/auto.net 

/var/autofs/removable   /etc/auto.removable --timeout=2,sync,nodev,nosuid --ghost
#/var/autofs/removable   /etc/auto.removable --timeout=2,sync,nodev --ghost
pg@pipoTower: ~/locations$ cat /etc/auto.removable 
usbDataBackups          -fstype=auto    UUID="e445ba7b-eced-41f6-b9e8-4c50e59d5fa3"
usbData                 -fstype=auto    UUID="4b8272c7-52db-4671-8206-8cf1498390fc"
```**Laptop (Client):**
```
pg@pgLptp: ~/tmp$ sudo mount -vvv -t nfs 192.168.1.3:/var/autofs/removable/usbData mount2
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "192.168.1.3:/var/autofs/removable/usbData"
mount: node:  "mount2"
mount: types: "nfs"
mount: opts:  "(null)"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "192.168.1.3:/var/autofs/removable/usbData"
mount: external mount: argv[2] = "mount2"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw"
mount.nfs: timeout set for Sun Jan 20 19:54:15 2013
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.3,clientaddr=192.168.1.4'
```Stays and wait, does not complete this command here....
Note that I'm able to mount /home/pg the other exported directory on my laptop which is on hard drive from server....

THX!!!!!!!!

---

### Post by papibe on 2013-01-20
Hi ph.gachoud. Welcome to the forums ):P

First of all, I don't know if that is possible.

If I were you, I'd start with these thoughts:

1. Are you really using the just 2 bytes to identify your network (/16 format) instead of the standard 3 bytes (/24)? If you are not sure, could you post the result of the this command?
```
ifconfig
```
2. Have you try to first force the autofs mount on the server before trying to mount it remotely. For instance by doing:
```
ls /var/autofs/removable/usbData
```
You can test if the drive got mounted using either 'df' or 'mount -l'.

Once you are sure it is mounted locally, try mount it remotely. **Note:** you may need to increase the timeout to something closer to a minute so the drive doesn't unmount by itself during this test.

Let us know how it goes.
Regards.

---

