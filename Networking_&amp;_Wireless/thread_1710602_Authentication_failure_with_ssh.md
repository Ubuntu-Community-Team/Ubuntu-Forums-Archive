---
title: "Authentication failure with ssh"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by javiggvv on 2011-03-20
Hi,

I'm trying to connect to computers with ubuntu 10.10 by ssh. I have installed openssh-server and openssh-client. I can access from the first one to the other, but not in the other way. I have tried to connect from the second computer to itself to verify that the problem was not at the first computer, and it can not connect. It seems that the problem is in the password. Here is what I get when I do ssh:

javi@javi-PC:~$ ssh javi@192.168.1.128
javi@192.168.1.128's password: 
Permission denied, please try again.
javi@192.168.1.128's password: 
Received disconnect from 192.168.1.128: 2: Too many authentication failures for javi

I have attached output of ssh_config,hosts.allow and host.deny.

Please help me, I have tried several things but I can't find the solution.

Thanks

---

