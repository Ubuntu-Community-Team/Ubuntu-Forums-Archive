---
title: "nfs mount slow in precise"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by Nessined on 2012-06-03
My /home directory is mounted via NFS. After the login screen is shown (in my case kdm), the /home directory is not yet available. If I login at a console I see that following processes exist:
- mountall --daemon
- mount -t nfs -o rw,hard,intr 192.168.0.7:/home /home
- /sbin/mount.nfs 192.168.0.7:/home /home -o rw,hard intr

If I execute "sudo mount -a" the /home directory is mounted immediately and the 3 processes disappear. If I just wait and do nothing the /home directory becomes available after some time (minutes)

This gives me the impression that mountall starts to mount the /home directory when the internet connection is not yet available and that it only retries after a long timeout. 

I have the problems only with 12.04 precise amd64 and not with 10.04 lucid i386 (dual boot system).

Is there a way to delay mountall until the internet connection is available or reduce the retry timeout ?

---

### Post by Nessined on 2012-06-09
I have found a solution for this problem:
In /etc/fstab: specify option noauto for /home so that the directory is not mounted at startup.

Delay kdm until the ethernet connection is up (in my case eth0) and mount the /home directory before starting kdm. This is done via following modifications to /etc/init/kdm.conf:
- insert a new line "and net-device-up IFACE=eth0" after "and started dbus"
- insert a new line "/bin/mount /home" before "exec kdm"

---

