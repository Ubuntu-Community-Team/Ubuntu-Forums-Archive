---
title: "server unexpectedly closed network connection in ubuntu server"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by hariharangopal on 2013-04-08
Hi,

 I get the below error when I tried to connect the Ubuntu server from Windows machine via Putty... 

Server unexpectedly closed network connection.

Please Help me to solve it...

---

### Post by SeijiSensei on 2013-04-08
It cannot connect to the server's port 22.  Either you are not running an SSH server like openssh-server on the remote machine, or there is some type of filtering or firewalling that is blocking your access to the port.

---

