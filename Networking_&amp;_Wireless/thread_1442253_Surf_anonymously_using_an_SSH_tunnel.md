---
title: "Surf anonymously using an SSH tunnel"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by carolija on 2010-03-29
HI,

I tried this :

> ssh -ND 9999 username@home_router_ip_address

and this is output :

“nani@jebe-kevu-ovaj-PC:~$ ssh -ND 999 [email]nani@nani.homelinux.com[/email]
Privileged ports can only be forwarded by root.
nani@jebe-kevu-ovaj-PC:~$ sudo ssh -ND 999 [email]nani@nani.homelinux.com[/email]
[sudo] password for nani:
The authenticity of host ‘nani.homelinux.com (192.168.0.195)’ can’t be established.
RSA key fingerprint is 7c:ce:72:cd:10:15:5a:e3:1a:b9:5c:b8:f0:82:3f:d0.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added ‘nani.homelinux.com,192.168.0.195&#8242; (RSA) to the list of known hosts.
[email]nani@nani.homelinux.com[/email]’s password:
ls
w
?
help”
-
So my question is wich password is he looking for exacly ?
user nani is main user at ubuntu after he asked me for password i typed my nani user password and i got in , after how you can see he ask me for onather password i tried the nani’s password but nothing is heppening ?

Please advice and thank you!

---

### Post by dmizer on 2010-03-29
Using a socks proxy tunnel is only partially anonymous. The DNS data cannot pass through the proxy and is therefore trackable.

As to your question, the first password request is locally for your "sudo" command. The second password request is to grant you access to the remote machine.

---

