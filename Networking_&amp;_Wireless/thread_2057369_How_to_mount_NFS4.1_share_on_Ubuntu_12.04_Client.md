---
title: "How to mount NFS4.1 share on Ubuntu 12.04 Client"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by susantadutta on 2012-09-13
[FONT=Courier New][FONT=Arial]Desperately looking for a solution to mount NFS4.1 share created on Windows 2012 System on to Ubuntu 12.04 Client. Getting the below error while mounting. Was also getting the same error on RedHat 6.2, but finally could able to mount successfully with “[FONT=Courier New]-o minorversion=1[/FONT]” option. But this option is invalid for Ubuntu. However I am able to mount using NFSv3 , i.e. with “[FONT=Courier New]-o vers=3[/FONT]”[/FONT] [/FONT]

[FONT=Courier New][FONT=Courier New][SIZE=1]# showmount -e 10.1.6.84[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]Export list for 10.1.6.84:[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]/nfsdata (everyone)[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]#[/SIZE][/FONT]
[/FONT][FONT=Courier New][SIZE=1]# mount -t nfs4 10.1.6.84:/nfsdata /nas1 –v [/SIZE][/FONT]
[SIZE=1][FONT=Courier New]mount.nfs4: timeout set for Mon Aug 27 16:21:23 2012[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs4: trying text-based options 'addr=10.1.6.84,clientaddr=10.1.9.1'[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs4: mount(2): Input/output error[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs4: mount system call failed[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]#[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]# mount -t nfs -o vers=3 10.1.6.84:/nfsdata /nas1 -v[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]mount.nfs: timeout set for Tue Aug 28 23:50:28 2012[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs: trying text-based options 'vers=3,addr=10.1.6.84'[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs: prog 100003, trying vers=3, prot=6[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs: trying 10.1.6.84 prog 100003 vers 3 prot TCP port 2049[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs: prog 100005, trying vers=3, prot=17[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]mount.nfs: trying 10.1.6.84 prog 100005 vers 3 prot UDP port 2049[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]10.1.6.84:/nfsdata on /nas1 type nfs (rw,vers=3)[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]#[/FONT][/SIZE]

---

