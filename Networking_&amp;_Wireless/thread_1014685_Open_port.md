---
title: "Open port"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by any.linux12 on 2008-12-18
HI!

I need to open a port in a server that I access by ssh. I already tried some commands that I saw in other treads but didn't work.



Please help!
I realy need that port open

---

### Post by The Cog on 2008-12-18
You open a port by starting a server that listens on that port. To install an SSH server, use the command:
> sudo aptitude install openssh-server
and the port 22 will be open to incoming connections.

If you have installed a firewall, you may also need to configure it to allow connections in to port 22. f you need help doing that, tell us which firewall you have installed. If you havn't installed a firewall, then no problem because a default Ubuntu installation doesn't firewall anything.

Beware, there are lots of password guesong bots out there. You may want to check your password strength and configure the SSH server to only accept connections from certain users and IP addresses by editing /etc/ssh/sshd_config.

---

