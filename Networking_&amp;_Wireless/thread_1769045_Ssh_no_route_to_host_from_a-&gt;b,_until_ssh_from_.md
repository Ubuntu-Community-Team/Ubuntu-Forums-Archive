---
title: "Ssh no route to host from a-&gt;b, until ssh from b-&gt;a"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by InkyDinky on 2011-05-27
I have two computers on a Lan. 
Both are running sshd.
I tried to connect from A( old Dell Inspiron Laptop running Arch) to B (old P3 desktop w/usb wireless card running Ubuntu 10.10).
I received a no route to host from A->B when attempting to ssh.
I then walked over to B and ssh'd successfully from B->A.
I went back to A and then successfully ssh'd from A->B.

Any thoughts on why connecting the reverse way somehow solved the problem? I feel like the ssh from B->A wasn't exactly necessary. I feel like an ssh out from B to any computer would've done the trick. I feel that there are some issues with the usb wireless that may be the problem but don't know how to go about solving them.  I feel like the outbound connection somehow 'wakes up' the lazy wireless card.

Any thoughts or ideas?

Thanks.
Nick

---

### Post by papibe on 2011-05-27
That happened to me when I replace the default DNS (the router) for OpenDNS. I achieved better times while browsing, but the machines in my LAN stopped knowing each other.

There's a simple solution: use avahi services. That basically consist in an simple name broadcast system. If both machines are running it (Ubuntu does it by default), you can access both computers using the 'local' domain:

```
user@A:~$ ssh B.local
```
or
```
user@B:~$ ssh A.local
```
Hope it helps.

---

