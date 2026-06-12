---
title: "problems with ssh"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by davidebond on 2006-07-13
Hi,
    I've installed on Ubuntu 6.06 RC the open-ssh package in order to use it as a server besides as a client. But, I'm unable to log in ubuntu via ssh from a remote computer (Unix-darwin from Tiger). Ubuntu ask me for a password, I enter it. The answer: access denied. I tried to edit the sshd_config file enabling the 'enable empty password' option. Again, without result.

What can i do?

Thanks,

                                             davide

---

### Post by reacocard on 2006-07-13
try using
```
ssh -l your_ubuntu_username your_computer's_ip
```
then enter your login password

---

### Post by davidebond on 2006-07-13
Thanks, but it doesn't work. I tried with both protocols, 1 and 2, but with the same message:

ssh: connect to host 10.0.1.1 port 22: Connection refused

Hi,

                                        davide

---

### Post by javaJake on 2006-07-13
Do you have a firewall (firestarter) that could be blocking things?

---

### Post by davidebond on 2006-07-13
Good question... I've installed no firewall on Ubuntu and from Tiger I've 'opened' the ssh-access from remote pc. In fact, I can log in unix-Tiger FROM ubuntu.

Hi,

                                               davide

---

### Post by javaJake on 2006-07-13
> **davidebond said:**
> Good question... I've installed no firewall on Ubuntu and from Tiger I've 'opened' the ssh-access from remote pc. In fact, I can log in unix-Tiger FROM ubuntu.

Mmmm... OK. Well, it is unlikely there are firewall issues involved.

This is where I can no longer help davidebond. I don't have any other ideas. Could someone else pick up this thread? :D

---

### Post by skale on 2006-07-13
Try getting on to mine? 
try **ssh 24.99.65.244**
and **talk sameer**
post what happens?

---

### Post by javaJake on 2006-07-13
I hope I did what you asked for. :p 

```

jacob@ubuntu:~$ ssh 24.99.65.244
ssh: connect to host 24.99.65.244 port 22: Connection refused
jacob@ubuntu:~$ talk sameer
bash: talk: command not found

```

---

