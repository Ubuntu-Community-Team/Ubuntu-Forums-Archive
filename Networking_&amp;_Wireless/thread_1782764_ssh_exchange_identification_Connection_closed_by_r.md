---
title: "ssh_exchange_identification: Connection closed by remote host"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by mgiann on 2011-06-15
Hi i need some help over here

i try to connect to a specific ip address  with ssh i have installed the ssh server and client.
i also try it by connecting with localhost  without any problem. But i keep taking this message
 if to try to connect to the ip address. i checked my hosts.allow and hosts.deny files and all 
are commented  in there (i think tha this should not be the problem). 


Thanks

---

### Post by mgiann on 2011-06-15
i also tried to restart ssh and i keep taking this message :

~$ /etc/init.d/ssh restart
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key
 * Restarting OpenBSD Secure Shell server sshd                  
start-stop-daemon: warning: failed to kill 2216: Operation not permitted
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key

---

### Post by eurospoofer on 2011-07-30
The line:

start-stop-daemon: warning: failed to kill 2216: Operation not permitted

suggests access and all the keys it couldn't find are usually rw only to root.
Are you sure the ssh demon is running under root?

---

