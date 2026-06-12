---
title: "mount -t cifs - ERROR 115"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by myaso on 2013-01-17
Fellow UBUNTU-ans!
I am trying to mount a shared WIN-XP directory to a local mountpoint on UB 12.10. I found many similar posts referring to this same error (115), BUT with 1 important exception - they all dealt with network-named PC, and NOT an explicitly specified IP address. So their solutions were rolling around fixing the ability to resolve the names to IPs and vice versa.

My situation is different in that I am trying to use an IP address. Command is running from root:

root@home-ub2:~# mount -t cifs //192.168.1.2/PIX.MASTER /PIX.MASTER -o username=myself,password=
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
root@home-ub2:~#

What is even more perplexing, 1 day ago EXACTLY the same command worked OK. Apparently, something changed in the environment which caused it to stop working.

ANY ADVICE IS IMMENSELY APPRECIATED !!
Myaso

---

### Post by myaso on 2013-01-17
In some of the NON-ubuntu forums I found a suggestion it might be related to a firewall blocking.
IT turned out to be the case!
I had a firewall blocking the traffic on a PC. (Windows firewall somehow enabled itself).
Posting it here in hope some folks might find this info useful.

Thanks!
Myaso

---

