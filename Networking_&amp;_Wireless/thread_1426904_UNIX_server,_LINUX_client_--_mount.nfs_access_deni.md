---
title: "UNIX server, LINUX client -- mount.nfs: access denied by server"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by ishmael1851 on 2010-03-10
I'm trying to add a Linux client to an existing NFS setup running on a UNIX server (which I did not setup), but it's not working.

Here's what I have so far:

I created a mount point called /mnt/SCIENCE


In /etc/fstab,  I have added:

192.168.1.7:/export/science2 /mnt/SCIENCE nfs rw,hard,intr,rsize=32768,wsize=32768 0 0

When I try to mount with 'mount -a', I get:

mount.nfs: access denied by server while mounting 192.168.1.7:/export/science2

The output of 'showmount -e 192.168.1.7' is:

Export list for 192.168.1.7:
/export/install             all-computers
/export/apps                all-computers
/export/projects            all-computers
/export/science1            all-computers
/export/science2            all-computers
/export/science3            all-computers
/export/scratch             all-computers
/export/stmp                all-computers
/export/var/log/all_systems all-computers
/export/var/mail            all-computers
/export/var/message_boards  all-computers
/export/ck                  sci32,sci11


Other computers on the network are able to access /export/science2 just fine, so the problem isn't on the server side (I don't think).  Those computers use automount though, so I can't just copy/paste their fstab files.  Any ideas?  Thanks for the help!

---

### Post by johnson.d on 2010-03-11
You can do the following checks:

1) Check firewall settings on the server and the problem client to see if there are any host based restrictions preventing the problem client from accessing NFS.

3) Check whether the NFS client is able to mount shares from other NFS servers.

4) Compare the nfs mount arguments between the working clients and the problem client.

4) Use a sniffer on the problem client and see if you get any hints for the root cause.

---

### Post by ishmael1851 on 2010-03-11
Ok, I found the problem.  I had to be added to the netgroup (/etc/netgroup).  Thanks for your suggestions!

---

