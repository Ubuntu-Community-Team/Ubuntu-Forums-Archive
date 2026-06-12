---
title: "foward lookup doesn't exist from mountd"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by whitmad on 2009-02-11
I'm setting up a new server on 8.10 and having trouble mounting NFS exports - I have the bind and NFS setup the same as on my old 7.04 server, but an attempt to BFS mount a directory on the server from a client fails and I ahve the following error in the server's daemon.log


> Feb 11 14:55:58 mrburns mountd[5241]: mount request from unknown host 192.168.0.
10 for /home (/home)
Feb 11 14:56:03 mrburns mountd[5241]: Fake hostname marge.sparkle.local for 192.
168.0.10 - forward lookup doesn't exist


I've checked my bind setup and it looks right to me (and works on the other server) - e.g., on the new server:

> david@mrburns:~$ host marge
marge.sparkle.local has address 192.168.0.10
marge.sparkle.local mail is handled by 10 springfield.sparkle.local.
david@mrburns:~$ host 192.168.0.10
10.0.168.192.in-addr.arpa domain name pointer marge.sparkle.local.
david@mrburns:~$ 


I'm sure I'm missing something obvious or have done something really dumb - any ideas gratefully received.

---

### Post by whitmad on 2009-05-13
Found it. It's a conflict with the zeroconf name resolution (which I'm not using anyway). Apparently zeroconf uses ".local" as an ad hoc domain - I guess I should change my internal tld from .local to something else, but for the time being removing the mdns4 entries from /etc/nssswitch.conf fixes it:

#hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns

---

