---
title: "Slow SSH login after credentials"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by brady@wisc on 2009-04-17
I have Ubuntu Server 8.10 running OpenSSH server.  It takes around 20 seconds from the time I entered my password, connecting through SSH, till a command prompt is up.  This happens when using both putty and a terminal.  Here is part of the log file from putty where it hangs.  I tried using the "UseDNS no" and that didn't work. 

2009-04-17 01:18:19	Sent password
2009-04-17 01:18:22	Access granted
2009-04-17 01:18:39	Opened channel for session
2009-04-17 01:18:39	Started a shell/command

---

### Post by cviorel on 2009-04-17
Add ```
UseDNS no
``` to your /etc/ssh/sshd_config file, then restart ssh.

---

### Post by yufei on 2009-04-17
check two files

1, /etc/hosts, 
make sure your hostname is point to 127.0.<0|1>.1
2, /etc/nsswith.conf
change  hosts line like following.

#hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns

---

### Post by brady@wisc on 2009-04-17
I have added UseDNS no to my sshd_config file and restarted the SSH service.  This did not fix the problem.  I also checked my hosts and nsswitch.conf file and they were both correct.

---

### Post by yufei on 2009-04-21
I mean: change the the nsswitch.conf to 

hosts: files dns 

comment the original line (which include mdns)

---

### Post by brady@wisc on 2009-04-25
So should it look like this?

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

