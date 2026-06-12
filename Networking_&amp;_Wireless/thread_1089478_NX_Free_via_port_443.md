---
title: "NX Free via port 443"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by rozbarwinek on 2009-03-07
Hi

I have configured my shh well and everything work good on port 22, but when I change it to 443 (I have to), NX Free can't get authentication :|
I tried to disable Firestarter but it's still not working.
Any ideas?

---

### Post by albandy on 2009-03-07
First try to connect to ssh throght port 443.
ssh youruser@yourcomputer -p 443
then  ensure the client is configured to connect to port 443.

---

### Post by rozbarwinek on 2009-03-07
> **albandy said:**
> First try to connect to ssh throght port 443.
ssh youruser@yourcomputer -p 443
then  ensure the client is configured to connect to port 443.

It is working... just NX is not :|
But I have just noticed that it is not working on any port other than 22 :|

```
emil@emil-desktop:~$ ssh starykomputer@192.168.0.2 -p 443
starykomputer@192.168.0.2's password: 
Linux starykomputer-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
starykomputer@starykomputer-desktop:~$
```

I tried to change SSHDPort to 443 in /usr/NX/etc/node.cfg and server.cfg, but it didn't helped :/

---

### Post by albandy on 2009-03-07
you should open port 443 in sshd configuration

sudo gedit /etc/ssh/sshd_config
add the string "Port 443" after "Port 22" so your sshd_confg file should look like this:
[...]
# What ports, IPs and protocols we listen for
Port 22
Port 443
[...]

---

### Post by rozbarwinek on 2009-03-07
> **albandy said:**
> you should open port 443 in sshd configuration

sudo gedit /etc/ssh/sshd_config
add the string "Port 443" after "Port 22" so your sshd_confg file should look like this:
[...]
# What ports, IPs and protocols we listen for
Port 22
Port 443
[...]

What for? I said that ssh is working on port 443... just NX don't

---

### Post by spoilingmyself on 2009-08-16
hey 
i think u can tell me how ssh works on 443. on my machine it says connection refused.
i have tried disabling, modifying firewall iptables, add port 443 after port 22 in /etc/ssh/ssh-config. but it still doesnt work...
i have to browse on of the sites which needs 443 open but on my machine it is not.. please tell me how to asap.......
smiles ))))))

---

