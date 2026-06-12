---
title: "Tunnel?"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by djcraft on 2010-05-19
So here's the setup:

Ubuntu 10.04 host inbound port 22 open
FreeBSD 8.0 host no inbound ports open

Both hosts are running sshd currently. What would you do for the Ubuntu host to be able to ssh to the FreeBSD host? A tunnel?

---

### Post by anomie on 2010-05-19
You'd ssh to the FreeBSD host the usual way...
```
$ ssh foo@freebsd.host
```

If that's not working, run the following on your Ubuntu box (and post the output): 
```
$ nc -zvw 1 freebsd.host 22
```

And then run the following on your FreeBSD box (and post the output): 
```
# tail -20 /var/log/auth.log
```

---

### Post by djcraft on 2010-05-19
> **anomie said:**
> You'd ssh to the FreeBSD host the usual way...
```
$ ssh foo@freebsd.host
```

the freebsd host is behind NAT. port forwarding on the gateway is not an option

---

### Post by Hobgoblin on 2010-05-20
Then you need to set up a VPN.

Hamachi would do it if it's still available.

---

### Post by djcraft on 2010-05-20
> **Hobgoblin said:**
> Then you need to set up a VPN.

Hamachi would do it if it's still available.

Is there a way to do so without connecting to another network (hamachis servers)?

---

### Post by anomie on 2010-05-20
[QUOTE=djcraft]the freebsd host is behind NAT. port forwarding on the gateway is not an option[/QUOTE]

Now *that* is a detail to mention in your first post. ;) 

Yes, this is possible, and fairly simple. Read here: 
[http://linux.byexamples.com/archives/238/ssh-reverse-tunneling/](http://linux.byexamples.com/archives/238/ssh-reverse-tunneling/)

---

### Post by djcraft on 2010-05-20
> **anomie said:**
> Now *that* is a detail to mention in your first post. ;) 

Yes, this is possible, and fairly simple. Read here: 
[http://linux.byexamples.com/archives/238/ssh-reverse-tunneling/](http://linux.byexamples.com/archives/238/ssh-reverse-tunneling/)

That method works :)

---

