---
title: "Domain issues"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by ThLo on 2012-07-20
Hello to everyone,

I am new to ubuntu server, and I would like to ask some questions about some ubuntu domain issues:

I have a small domain on the ubuntu server where old xp workstations get connected on. The thing is that most of the machines cannot log on anymore. The few of them that still work are using the same username+pass as the others does cannot get connected to domain, the usual message "domain is not available" appear everytime. Nothing changed but it seems that there is a problem. Unjoining-joining the domain did not help.

When I have the same problem with windows server I know that there a few simple steps to follow to rejoin the domain, but now what about ubuntu, is there a quideline to help me manage this situation? :(

I use **webmin**, if anyone could help me I would appreciate it!

[I]Operating system     Ubuntu Linux 10.04.3
Webmin version     1.580
Kernel and CPU     Linux 2.6.32-41-server on x86_64
Processor information     Intel(R) Pentium(R) D CPU 3.00GHz, 2 cores[/I]

---

### Post by ThLo on 2012-07-22
Any help please? 
I would like to ask as well, how should I generally add other xp machines to this domain? 
Do I have to add it first to "ldap users and groups" and then join the pc to the domain, or should I join the domain first and I will see it in the users & groups? 
Is there a possibility not to be able to join the domain due to a "double" name on the domain without seeing it?

---

### Post by bakegoodz on 2012-07-28
Use the WINS option in smb.conf. Useing only NETBIOS is flaky and seems to work worse as time goes on. ie. XP SP1 didn't seem to have any problems with NETBIOS only setups

---

