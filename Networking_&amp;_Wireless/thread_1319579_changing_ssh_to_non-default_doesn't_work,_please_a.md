---
title: "changing ssh to non-default doesn't work, please advice."
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by redscorpion69 on 2009-11-08
sshd_config on my fedora server is modified to listen ssh on 8022.
nmap -sS localhost displays 8022/open/ssh.

On my ubuntu client ssh_config is modified to 8022 as well. There is no firewall blocking any of the connection between the two.

however, nmap -sS a.b.c.d (server) shows -> 22/closed/ssh.

ssh -p 8022 -v server@a.b.c.d on my client shows -=> debug1: connect to address a.b.c.d port 8022: No route to host.

How can i make this work, and why does nmap scan shows closed 22 instead of open 8022?

thx

---

### Post by redscorpion69 on 2009-11-10
does anyone know this?

---

