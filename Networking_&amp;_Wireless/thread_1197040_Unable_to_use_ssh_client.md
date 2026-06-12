---
title: "Unable to use ssh client"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by bswilson on 2009-06-25
Recently, I have been unable to use SSH to remotely login to any system.  Something is goofy on my client system (Ubuntu 9.04).  This previously worked fine, and I think the problems started when I installed FileZilla (client), but I couldn't swear to that. 

Here's the problem I'm seeing:

```
$ ssh -v -v 192.168.1.2
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.2 [192.168.1.2] port 22.
debug1: Connection established.
debug1: identity file /home/bswilson/.ssh/identity type -1
debug1: identity file /home/bswilson/.ssh/id_rsa type -1
debug1: identity file /home/bswilson/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
```

Help!

Update #1: I just learned that my ~/.ssh directory was empty! So I regenerated my keys like you normally would, but that didn't fix my problem.

Update #2: I forgot to mention that I've also been able to use putty to connect from a Windows host on the same network; this proves nothing is wrong with my server system (the machine I'm trying to reach).

---

### Post by bswilson on 2009-06-25
I just learned that my **~/.ssh** directory was empty!  So I regenerated my keys like you normally would, but that didn't fix my problem.

---

### Post by bswilson on 2009-06-25
I forgot to mention that I've also been able to use putty to connect from a Windows host on the same network; this proves nothing is wrong with my server system (the machine I'm trying to reach).

---

### Post by bswilson on 2009-06-25
OK, well, I feel like a dumb-***.  The problem was that I was running a particularly chatty rsync script, and this was causing the DenyHosts package on my server to blacklist my laptop!  My laptop's DHCP address was added to my /etc/hosts.deny file.

I fixed this by adding my laptop's IP address to /etc/hosts.allow.

:popcorn:

---

### Post by Iowan on 2009-06-26
Glad "we" :rolleyes: could be of so much help. (Maybe next time...)

---

