---
title: "Cannot get NFS to work both ways"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by edrich on 2010-06-15
[FONT=Arial][SIZE=3]I wonder if anyone can help me. I have been using another Linux distro
(Xandros) for 3 years on one computer and have just installed Ubuntu 10.04
on a different computer. I am trying to network the 2 computers via simple
ethernet cards and a crossover cable so that I can gradually migrate
applications, data and peripherals from Xandros to Ubuntu. I am completely
new to Ubuntu and I am really struggling to get NFS to work. Each computer
can ping the other, so the hardware connectivity seems OK. I have shared
the relevant directories from each computer. I have followed malco2001's
excellent HowTo guide and have now reached the stage where Xandros, as
client, can mount directories on Ubuntu, as server, and see the files but
I cannot get Ubuntu, as client, to mount directories on Xandros. When I
attempt this from Ubuntu, using the command

# mount -t nfs 192.168.1.2:/home/richard /mnt/PC2_richard
(I have already issued from Ubuntu: # mkdir /mnt/PC2_richard)

I get the message: 

mount.nfs: mount to NFS server '192.168.1.2:/home/richard' failed: RPC Error: Success

The configuration of various files etc. is as follows:[/SIZE][/FONT]

[FONT=Courier New]Ubuntu
======
IP address: 192.168.1.1

/etc/exports
------------
/home/richard  192.168.1.2(rw,no_root_squash)

/etc/hosts
----------
127.0.0.1 localhost
#127.0.1.1 RP-3D-PC1
192.168.1.1 RP-3D-PC1
192.168.1.2 RP-CAT-PC2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hosts.allow
----------------
portmap: 192.168.1.2
ALL: 192.168.1.2: allow
ALL: ALL: deny

/etc/hosts.deny
---------------
[empty]


Xandros
=======
IP address: 192.168.1.2

/etc/exports
------------
/home/richard 192.168.1.1(rw,no_root_squash)

/etc/hosts
----------
192.168.1.2 RP-CAT-PC2 RP-CAT-PC2 # lan2
192.168.1.1 RP-3D-PC1.home RP-3D-PC1
127.0.0.1 localhost

/etc/hosts.allow
----------------
portmap: 192.168.1.1
ALL: 192.168.1.1: allow
ALL: ALL: deny

/etc/hosts.deny
---------------
[empty][/FONT]

[FONT=Arial]I should mention that Xandros does not have nfs-kernel-server installed;
instead it has nfs-user-server.

I am sorry if I have omitted or done something really stupid but I have
spent best part of a week on this with only partial success. I would be
very grateful for any help in solving this problem.[/FONT]

---

### Post by edrich on 2010-06-24
[LEFT]Since nobody has yet replied to my original posting, I thought it might be helpful to others to say that I have now reverted to Ubuntu 8.04LTS and the problem is no longer there. Each computer can mount file systems on the other computer and access the files therein. So maybe 10.04 is not really there yet (and admittedly I have subsequently seen a suggestion that new versions should not be installed for at least three months). Perhaps there is a lesson here for the testers.
[/LEFT]

---

### Post by redmk2 on 2010-06-24
> **edrich said:**
> [LEFT]Since nobody has yet replied to my original posting, I thought it might be helpful to others to say that I have now reverted to Ubuntu 8.04LTS and the problem is no longer there. Each computer can mount file systems on the other computer and access the files therein. So maybe 10.04 is not really there yet (and admittedly I have subsequently seen a suggestion that new versions should not be installed for at least three months). Perhaps there is a lesson here for the testers.
[/LEFT]

This is a pretty common problem with NFS version differences.  See [**_here_**]("http://ubuntuforums.org/showthread.php?t=1308241").

---

### Post by edrich on 2010-07-03
Many thanks for the link, redmk2. I tried adding '-o nfsvers=2' to the 'mount' command in Ubuntu 10.04 and NFS now works both ways. The 2GB limit may be an issue later on but for now things are just fine. Thanks again.

---

### Post by redmk2 on 2010-07-03
> **edrich said:**
> Many thanks for the link, redmk2. I tried adding '-o nfsvers=2' to the 'mount' command in Ubuntu 10.04 and NFS now works both ways. The 2GB limit may be an issue later on but for now things are just fine. Thanks again.

Your welcome.  Maybe someone else will create a more complete fix in the near future.  I doubt that you are the only one in this situation.

---

