---
title: "OpenSSH configuration for tunelling"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by pagirard on 2009-01-05
Hi All,

I am trying to tunnel a port on my home machine to my work one.

I've reviewed many topics on this forum and found very good information but I cannot get the tuneling to work.

Basicaly I can ssh my computer at home, using putty on my windows work machine but the port I am trying to forward does not work.

I've modified my /etc/ssh/sshd_config to include the line
AllowTcpForwarding yes

After restarting the machine, the port forwarding worked once (!) but the next day and follwing I would get a "cannot connect error" when I'm trying to reach the webpage [Http://localhost:7777](Http://localhost:7777) (7777 being the port I'm trying to forward from home).

I'm also changed the LogLevel to VERBOSE in my sshd_config file but I can't find any information about the broken connection.

This issue could be a putty configuration one but I was wondering I someone could point me to a log file/man page that I could read to debug the problem from a server stand point.

I've compared my putty configuration to other how-to/tutorials for the tunnel section and could not find anything wrong.

Thanks for the help in advance.

Pierre

---

