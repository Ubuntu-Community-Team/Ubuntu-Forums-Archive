---
title: "How to prevent NetworkManager from modifying '/etc/hosts'?"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by cioma on 2010-09-26
Latest NetworkManager adds the following line into my '/etc/hosts':
192.168.0.1 <my_hostname>

Because of that some applications can't properly create sockets as they expect hostname to be mapped to 127.0.0.1 (e.g. Mainsoft Mainwin-based apps).

Is there any way to prevent NetworkManager from modifying '/etc/hosts'?

Thanks in advance!

---

### Post by Iowan on 2010-09-26
Curious - my Lucid machine doesn't touch the file - but I have 127.0.1.1 defined with the hostname (127.0.0.1 is defined as "localhost").

---

### Post by cioma on 2010-09-27
Well, it's on Ubuntu 10.10 Maverick Meerkat.
Actually this is an intended behavior of the latest NetworkManager, for some reason it's considered to be a bad habit to alias computer hostname to localhost but I need it for the CAD software I use.
For now I made quick'n'dirty fix: manually edited '/etc/hosts' as I needed and set a read-only attribute to it. Now NetworkManager can't change it. But it would be great to know an 'official' solution for that.

---

### Post by ReimarBauer on 2011-04-05
have the same problem.  Software which is based on lmgrd don't work

I don't have seen that by rfc952 a sorted order of ip adresses must be given or that 127.0.0.1 must be always on top of the list. 

So why does it matter?

And If network manager must add something to the list, why is it on top can't it be on bottom?

---

