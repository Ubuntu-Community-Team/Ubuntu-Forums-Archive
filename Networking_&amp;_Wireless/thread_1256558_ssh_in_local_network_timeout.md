---
title: "ssh in local network timeout"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by jackyang on 2009-09-02
Hi everyone

I've been stuck with this wired problem for several days. I've done lots of search about ssh configuration on Internet. But none of them solves my problem. 

Here my situation:

I have a desktop and a laptop at home both running ubuntu 9.04. They are connected via a wireless router. The desktop has IP address 192.168.0.100 and laptop is 192.168.0.101. So both in the same network. 

Both machine has a ssh server running. I tested it with ssh username@localhost and it works.
The problem is: neither of them can ssh to the other. The connection always timeout.

I followed some thread on Internet about disable ufw. Doesn't work either.

However, PING works between them.

I'm wondering whether it's a firewall of ubuntu that blocks the connection. But I think once ssh server has been setup using apt-get it should has already configured firewall accordingly, right? If it's not, how should I configure firewall?

Can anyone help me with this situation?

---

### Post by snakepit # on 2009-09-02
Try telneting to one of the remote's port 22 first to rule in or out the router and firewalls.

My first instinct is a protocol mismatch though.

/etc/ssh/sshd_config

---

### Post by bear24rw on 2009-09-02
how did you install the ssh server?
```
sudo aptitude install openssh-server
```

---

