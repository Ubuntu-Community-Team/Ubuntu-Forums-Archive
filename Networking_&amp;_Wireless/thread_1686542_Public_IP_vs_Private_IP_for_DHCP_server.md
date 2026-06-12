---
title: "Public IP vs Private IP for DHCP server"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by wesg on 2011-02-12
My Ubuntu server is now providing routing duties to my network, but I'm having trouble opening ports to my network. I have a DynDNS account, so the IP is always current, but I can't ping even my IP directly.

My network map looks like 

Internet > SpeedTouch DSL modem with DHCP > eth1 > Ubuntu > eth0 > LAN

With the modem providing a 192.168.1.xx IP to eth1, I can browse fine. The default gateway is my modem. I switched to the public IP of the modem so I could use iptables for firewall duties, but I was locked out of the internet. No gateway was set when I did that, but eth1 received the public IP of my modem. 

Suggestions? How can I use the public IP assigned to eth1?

---

### Post by YesWeCan on 2011-02-12
When you say you switched tothe public IP of the modem, exactly what do you mean?
Why do you think you need to do this to use iptables?
Why do you want eth1 to have your public IP address?

---

### Post by wesg on 2011-02-12
> **YesWeCan said:**
> When you say you switched tothe public IP of the modem, exactly what do you mean?
Why do you think you need to do this to use iptables?
Why do you want eth1 to have your public IP address?

#1 The modem I have offers the ability to give a device on the network the front facing public IP of the modem itself. Kind of like a DMZ configuration on other routers. Essentially instead of eth1 having an IP of 192.168.0.xxx it has the ISP one (69.xx.xx.xx or whatever)

#2 I'm thinking i need to do this because right now I can't even ping my IP for a response, which means I can't run any services behind my firewall for outside access. That's my whole goal.

#3 I may not need to even use the public IP, but i was thinking that this might be the only way to get the network set like I want.

---

### Post by YesWeCan on 2011-02-12
Would you post the output of 'route -n' and 'sudo iptables-save' on your Ubuntu PC?

Re #2 are you are trying to ping the public IP address of the modem from...somewhere(?)...and getting no response?

---

### Post by wesg on 2011-02-13
With a public IP, I can't access the internet. Normally, route -n shows 1 gateway, the IP of my modem. With a public IP on eth1, I don't get a gateway. 

I was only able to ping the public IP when I was using the standard local IP configuration. WIth a public IP, I couldn't ping anything.

---

### Post by mips on 2011-02-13
> **wesg said:**
> 
My network map looks like 

Internet > SpeedTouch DSL modem with DHCP > eth1 > Ubuntu > eth0 > LAN

With the modem providing a 192.168.1.xx IP to eth1, I can browse fine. The default gateway is my modem. I switched to the public IP of the modem so I could use iptables for firewall duties, but I was locked out of the internet. No gateway was set when I did that, but eth1 received the public IP of my modem. 

Suggestions? How can I use the public IP assigned to eth1?

You cannot do that. Think about what you just did for a second. You assigned the public ip to eth1 but your server/router has no way to talk to the remote end. It's ethernet and it does not know about dsl protocols which the modem/router handles. Your dsl modem/router needs that public ip to communicate to the isp and you cannot use that address twice in your own network.

If you want to use the public ip put your dsl router/modem into bridged mode. Configure your ubuntu box do handle the PPPoE connection to your ISP. The PPPoE session will now terminate locally on your ubuntu box and you can apply rules on the PPPoE interface.

I would still however advise you not to go this route as it essentially removes the extra layer of security (via NAT) your dsl router provides. Rather try and get port forwarding on your dsl router to work.

---

### Post by wesg on 2011-02-13
Thanks, mips,
when I get some time later this week I'm going to try to set up the modem to be just a modem. Maybe that way I can initiate the DSL connection from Ubuntu and have a direct connection. 

Might also see if my ISP can switch me to a cable connection :D

---

