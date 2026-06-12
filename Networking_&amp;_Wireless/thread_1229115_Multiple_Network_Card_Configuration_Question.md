---
title: "Multiple Network Card Configuration Question"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by herrdoktor330 on 2009-08-01
Hello all,

I'm trying to complete a project where I use 2 separate network cards on my ubuntu box. I'd like to have all of my network traffic go through network card 1 but have my samba server, vino server, and SSH server listen and accept connections on network card 2 only.

How would I make this happen? I tried googling an answer and came up flat.

Thank you.

---

### Post by Iowan on 2009-08-02
Just an opinion,, but it may require some iptables rules.  *Some* services can be bound too specific interfaces - dunno about the ones you listed.

---

### Post by firen on 2009-08-02
Dont know much about vino server ( you can quickly read about it in this thread [http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981) ),  but Samba and SSH Server do support listening on particular network interface only

for samba add this to the smb.conf

```
[general]
interfaces = lo eth0 192.168.1.0/24
```SSHD supports the following options in /etc/ssh/sshd_config

```
ListenAddress 192.168.1.1
```

---

