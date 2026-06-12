---
title: "I am not able to ssh after upgrading to 10.10"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by naarkhoo on 2011-03-24
After upgrading ubuntu 10.10 I realized that I am not able to ssh into our university server, I have to add that, there is not any problem from outsite ...

Here is my iptables,

> sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


---

### Post by naarkhoo on 2011-03-30
Here you can find the output of diagnosis version of ssh !
naarkhoo@Xoranux:~$ ssh -vvv alireza@interaction

> OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to interaction [130.225.75.208] port 22.
debug1: connect to address 130.225.75.208 port 22: Connection timed out
ssh: connect to host interaction port 22: Connection timed out


any idea?

---

### Post by naarkhoo on 2011-03-30
still ...

---

