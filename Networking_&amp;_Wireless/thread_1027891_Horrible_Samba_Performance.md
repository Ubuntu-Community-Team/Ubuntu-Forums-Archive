---
title: "Horrible Samba Performance"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by beers on 2009-01-01
Just built a server box (opteron 165, epox 9npa sli nforce 4 board, 1.5g ram, using onboard lan) to replace current one, moved HD's over and everything but installed on a fresh drive.

Copied the existing /etc/samba/smb.conf that seemed to be working well to the new server, as it was having abysmal performance (~190 KB/sec, 100mbit lan).  Config is as follows:

```
[global]

hosts deny = 0.0.0.0/0
hosts allow = 192.168.1.99 192.168.1.87 192.168.1.10*

socket options = TCP_NODELAY SO_KEEPALIVE IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
read prediction = yes
debug level = 0
hostname = Fileserver
workgroup = WORKGROUP
server string = fileserver
dns proxy = no
wins support = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
security = share
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
;   guest account = nobody
invalid users = root
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
usershare allow guests = yes

[various shares]
```

The thing is though, I can reboot the server and have full bandwidth for about 5 minutes, then the server rapidly begins slowing down.  

Any ideas?  I'm kinda new to linux so not sure where to go now.

---

