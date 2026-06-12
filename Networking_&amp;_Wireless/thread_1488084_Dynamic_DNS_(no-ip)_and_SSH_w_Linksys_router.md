---
title: "Dynamic DNS (no-ip) and SSH w/ Linksys router"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by shanest on 2010-05-19
Hello,

I've read some guides on how to setup ssh with dynamic DNS, but can't seem to get it to work.

My Linksys router is currently set to forward port 22, so I don't know why SSH still gives:


ssh [email]admin@xxx.hopto.org[/email]
ssh: connect to host xxx.hopto.org port 22: Connection refused

In particular, I also have openssh-server running on the target machine.

Given that I have port forwarding enabled, why would this be happening?  If I try to login directly to the IP, I get the same refusal.

Best
Shane

---

### Post by tkoco on 2010-05-19
> **shanest said:**
> Hello,

I've read some guides on how to setup ssh with dynamic DNS, but can't seem to get it to work.

My Linksys router is currently set to forward port 22, so I don't know why SSH still gives:


ssh [email]admin@xxx.hopto.org[/email]
ssh: connect to host xxx.hopto.org port 22: Connection refused

In particular, I also have openssh-server running on the target machine.

Given that I have port forwarding enabled, why would this be happening?  If I try to login directly to the IP, I get the same refusal.

Best
Shane

Do you have a firewall running on the ssh-server machine? If you do, you need to tell the firewall to permit the incoming connection for ssh.

---

### Post by shanest on 2010-05-19
Yes; I thought I took care of this by unchecking a "Block Anonymous Internet Requests" box in the router's firewall config page.

---

### Post by Joe of loath on 2010-05-19
Where are you connecting from? I can't connect from school, as the firewall blocks most outgoing connections. But when I asked a friend to do it for me, he logged straight in.

---

### Post by shanest on 2010-05-19
An apartment building.

---

