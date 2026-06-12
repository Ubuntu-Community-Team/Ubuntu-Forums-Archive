---
title: "Setting up Iptables to allow only certain outbound traffic"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by Stratosmacker on 2011-06-16
I am running a headless Ubuntu 10.04.2 minecraft server. In a few days I am going away for three weeks and would like a friend to remote administer it. Here is the conundrum: I do not have a dmv (a real one, not the virtual one routers offer) to ensure my network (in this case my home network) is safe from any attacks on the server. I would like to use iptables to only allow outgoing minecraft connections. Being that iptables is incredibly daunting, does anyone know of a way to do this?

Best Regards,
Jesse O

p.s. Minecraft listens on 25565. I also have a webadministration specific to minecraft on 25000 and would like to be able to use ssh on the standard port.

---

### Post by manzdagratiano on 2011-06-17
This is what I do with allowing sshguard to use iptables to block attackers against ssh:

Place in /etc/rc.local:

```

# Let iptables (both regular IPv4 and IPv6 support) create a new chain
# in which sshguard will append blocking rules

iptables -N sshguard
ip6tables -N sshguard

# Update the INPUT chain to also pass the traffic to the sshguard chain
# at the very end of its processing. Specify in --dport all the ports of
# services sshguard protects:

# Block attackers for SSH, FTP, POP, IMAP services:

# iptables -A INPUT -p tcp --dport 21,22,110,143 -j sshguard
# ip6tables -A INPUT -p tcp --dport 21,22,110,143 -j sshguard

# Block attackers from all traffic:

iptables -A INPUT -j sshguard
ip6tables -A INPUT -j sshguard

# To make sshguard learn of login attempts:
tail -n0 -F /var/log/auth.log | sshguard &

```If I understand correctly, iptables merely logs information, and by itself will not prevent attacks; you need information from it to be fed to a guardian program, in my case sshguard. I would think you would employ something similar for the minecraft  server - whatever application you use as the equivalent of sshguard will  have to be fed information from iptables - and use the corresponding  port 25000 along with the others. As you can see, I block attacks against ALL traffic - you may use that if it suits you. It  should seem that sshguard should be usable in your case as well, unless someone more knowledgeable is able to suggest otherwise.

---

### Post by Stratosmacker on 2011-06-18
> **manzdagratiano said:**
> This is what I do with allowing sshguard to use iptables to block attackers against ssh:

Place in /etc/rc.local:

```

# Let iptables (both regular IPv4 and IPv6 support) create a new chain
# in which sshguard will append blocking rules

iptables -N sshguard
ip6tables -N sshguard

# Update the INPUT chain to also pass the traffic to the sshguard chain
# at the very end of its processing. Specify in --dport all the ports of
# services sshguard protects:

# Block attackers for SSH, FTP, POP, IMAP services:

# iptables -A INPUT -p tcp --dport 21,22,110,143 -j sshguard
# ip6tables -A INPUT -p tcp --dport 21,22,110,143 -j sshguard

# Block attackers from all traffic:

iptables -A INPUT -j sshguard
ip6tables -A INPUT -j sshguard

# To make sshguard learn of login attempts:
tail -n0 -F /var/log/auth.log | sshguard &

```If I understand correctly, iptables merely logs information, and by itself will not prevent attacks; you need information from it to be fed to a guardian program, in my case sshguard. I would think you would employ something similar for the minecraft  server - whatever application you use as the equivalent of sshguard will  have to be fed information from iptables - and use the corresponding  port 25000 along with the others. As you can see, I block attacks against ALL traffic - you may use that if it suits you. It  should seem that sshguard should be usable in your case as well, unless someone more knowledgeable is able to suggest otherwise.

So in order to allow the outbound traffic from minecraft, if I am not mistaken it uses other ports to send information to the client? This would mean having to open up outgoing ports as well. I think. Or is a similar setup to this all that I would need?

---

