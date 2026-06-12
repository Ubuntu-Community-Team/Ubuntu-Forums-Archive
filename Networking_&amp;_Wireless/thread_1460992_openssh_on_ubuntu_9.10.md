---
title: "openssh on ubuntu 9.10"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by fgccampos on 2010-04-23
Hello

I have recently updated my machine with ubuntu 9.10 and all of a sudden I can't seem to connect to it via ssh. No configuration changes were made.
The machine accepts the connection, asks for my username and my password and then just freezes there.
I've fetched my logs and the authentication does occur, but It seems that both machines can't exchange any extra data.

Any known solutions for this case?

Thanks
Filipe

---

### Post by fgccampos on 2010-04-23
By the way...

ssh localhost on the machine doesn't work as well. same problem.

---

### Post by Maheriano on 2010-04-23
Need more information, I've been using SSH since 9.04 and it has worked with every upgrade. Try uninstalling/reinstalling SSH.

---

### Post by fgccampos on 2010-04-23
what info do you need?

reinstalled it twice already, no luck :(

---

### Post by Iowan on 2010-04-23
**sshd** is running (**ps -ef |grep ssh**)?

---

### Post by adam814 on 2010-04-23
Sounds like an issue with your configs.  If you haven't customized them too much you could try this:
```
sudo apt-get purge openssh-server && sudo apt-get install openssh-server
```

---

### Post by fgccampos on 2010-04-24
> **Iowan said:**
> **sshd** is running (**ps -ef |grep ssh**)?

> **fgccampos said:**
> Hello
(...)
**The machine accepts the connection, asks for my username and my password** and then just freezes there.


> **adam814 said:**
> Sounds like an issue with your configs.  If you haven't customized them too much you could try this:
```
sudo apt-get purge openssh-server && sudo apt-get install openssh-server
```

Thanks for the idea Adam.
Did that just now. Had to erase the entry for localhost in ~/.ssh/knwo_hosts in order to be able to connect locally, but the problem is still the same... after sending password it just freezes.

Filipe

---

### Post by adam814 on 2010-04-24
Maybe something useful is getting logged?  Try this:

```
grep sshd /var/log/auth.log
```

---

### Post by fgccampos on 2010-04-24
Apr 24 10:14:24 localhost sshd[8662]: Server listening on 0.0.0.0 port 22.
Apr 24 10:14:24 localhost sshd[8662]: Server listening on :: port 22.
Apr 24 10:14:44 localhost sshd[8675]: Connection from 192.168.1.101 port 1200
Apr 24 10:14:55 localhost sshd[8675]: Failed none for filipe from 192.168.1.101 port 1200 ssh2
Apr 24 10:14:57 localhost sshd[8675]: pam_sm_authenticate: Called
Apr 24 10:14:57 localhost sshd[8675]: pam_sm_authenticate: username = [filipe]
Apr 24 10:14:58 localhost sshd[8675]: Accepted password for filipe from 192.168.1.101 port 1200 ssh2
Apr 24 10:14:58 localhost sshd[8675]: pam_unix(sshd:session): session opened for user filipe by (uid

All seems normal.
Well I guess nobody has a clue on what's going on. Already submitted a bug at launchpad but got no reply so far.

---

