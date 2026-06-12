---
title: "iptables for router"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by andyvr4 on 2012-01-05
Hi,

I'm trying to setup an ubuntu server to serve both files and act as a router between 2 internal networks and 1 external network (a cable modem).  I've got everything working (I can pass packets between the internal networks and all networks can get an ip address from dnsmasq and get outside, but right now both of the internal networks can get access to any services that are currently running on the server.  For right now the only service that I want the 2 internal network systems to be able to access is ssh.

All other requests I want iptables to block.  I was wondering if you guys could take a look at my firewall script posted below and let me know what I need to change in order to still let both internal networks get outside and for eth1 to access systems on eth0, but to not allow either eth0 or eth1 to access any ports except 22 on the server.

Thanks,
Andy

```
#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin

#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ethwan -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW ! -i ethwan -j ACCEPT

# Allow services
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 137 -j ACCEPT
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 138 -j ACCEPT
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 139 -j ACCEPT
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 445 -j ACCEPT

# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth1 -o ethwan -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o ethwan -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o ethwan -j MASQUERADE

# Don't forward from the outside to the inside.
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP

# Save the new rules
iptables-save > /etc/iptables.rules
```

---

### Post by andyvr4 on 2012-01-06
Does anyone have any suggestions?

---

### Post by jsra on 2012-01-06
Hello,
not quite sure I understood it right but I think this is the row you want to focus on:
```
# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state NEW ! -i ethwan -j ACCEPT
```

By this you allow all connection coming in from eth0 and eth1. So in this part
```
# Allow services
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```
you would have to block them.
Or you can delete the 1st row and then accept every single service you want to allow in 2nd part (Allow services).

Report back if that was what you wanted:)
jsra

---

### Post by Doug S on 2012-01-06
In addition to jsra's spot on comment.
128.173.14.84 reverses to Virgina Tech. Please confirm or deny if this is a school project. I have assumed that IP is from outside of your system, is that correct?
Also you said:> and for eth1 to access systems on eth0,but you didn't mention if eth0 is allowed to access systems on eth1, so I am assuming not.
 
Your question is far from trivial, be patient.

---

### Post by andyvr4 on 2012-01-06
Hi,

Thanks for the help guys a finally got everything working the problem was the line that jsra suggested.  I had confused what it was doing and forgot that it would let everything in.  After removing that line adding openings for dhcp and dns everything appears to be working properly.  Below is my final configuration.  The 128.173.14.84 address is a virginia tech address and this project does relate to tech work I probably should have blocked it out, but I forgot (it's a test system anyway so it doesn't really matter).

Thanks for the help!
Andy

```
#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin

#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ethwan -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ethwan -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow services
iptables -A INPUT -p tcp --dport 22 -j ACCEPT				#ssh
iptables -A INPUT -p udp -i eth0 --dport 53 -j ACCEPT		#dns
iptables -A INPUT -p udp -i eth1 --dport 53 -j ACCEPT		#dns
iptables -A INPUT -p udp -i eth0 --dport 67 -j ACCEPT		#dhcp
iptables -A INPUT -p udp -i eth1 --dport 67 -j ACCEPT		#dhcp
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 137 -j ACCEPT
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 138 -j ACCEPT
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 139 -j ACCEPT
iptables -A INPUT -p tcp -s 128.173.14.84 --dport 445 -j ACCEPT

# Setup Forwarding between interfaces (all none listed are blocked)
iptables -A FORWARD -i eth0 -o ethwan -j ACCEPT
iptables -A FORWARD -i eth1 -o ethwan -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o ethwan -j MASQUERADE

# Don't forward from the outside to the inside.
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP

# Save the new rules
iptables-save > /etc/iptables.rules
```

---

### Post by Doug S on 2012-01-06
glad you got it working. The iptables rule set you ended up with is pretty efficient.

---

### Post by jsra on 2012-01-06
No problem, you're welcome!:)
Mark this as solved btw:)

jsra

---

