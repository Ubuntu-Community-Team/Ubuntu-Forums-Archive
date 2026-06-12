---
title: "Setting Up Sharing via SSH"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by Paul1914 on 2009-03-03
Hey Guys,

I'm new to the Ubuntu world, and have switched my home server from XP Pro to Ubuntu Server. I've been able to connect via ssh server and can execute commands on the server, but I've yet to figure out how to enable sharing of 2 of the 3 hard drives in the server. what commands would i need to run to add users and enable sharing? thanks

---

### Post by DGortze380 on 2009-03-03
> **Paul1914 said:**
> Hey Guys,

I'm new to the Ubuntu world, and have switched my home server from XP Pro to Ubuntu Server. I've been able to connect via ssh server and can execute commands on the server, but I've yet to figure out how to enable sharing of 2 of the 3 hard drives in the server. what commands would i need to run to add users and enable sharing? thanks

you're going to want to look at Samba

---

### Post by crokett on 2009-03-03
You can also tunnel Samba (or anything else really) through ssh. This gives you a secure file share that you could access over the internet if you wanted to.

---

### Post by Paul1914 on 2009-03-03
and how do i do this via ssh

---

### Post by DGortze380 on 2009-03-04
[https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html)

---

### Post by Iowan on 2009-03-04
Another [option]("https://help.ubuntu.com/community/SSHFS") (or [two]("https://help.ubuntu.com/community/SSHHowto")).

---

