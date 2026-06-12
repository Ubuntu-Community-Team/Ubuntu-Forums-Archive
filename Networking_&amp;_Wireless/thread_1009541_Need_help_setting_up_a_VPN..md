---
title: "Need help setting up a VPN."
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by illbashu on 2008-12-12
I went ahead and installed OpenVPN and i have it in my network manager.
I posted a screen on the thing, i need help setting it up so i can use HULU. What do i put in the fealds? Like gateway and stuff. Can you guys help me fill out the stuff so i can get it working? thx in advance.

---

### Post by Iowan on 2008-12-12
I haven't set up VPN yet... Have you seen [this]("https://help.ubuntu.com/community/SSH_VPN") help page ( or [this]("https://help.ubuntu.com/community/VPNClient") one)?

---

### Post by downhillgames on 2008-12-12
You'd think it would be loads easier to do it via network manager than make each person who connects to this fill out a config file, etc. How do we do it via network manager?

---

### Post by illbashu on 2008-12-12
i dont want to mess with annoying config files, does anyone know how to do it through network manager?

---

### Post by iskandarjon on 2008-12-13
I installed VPN to my PC
and I done it as like this
-------------------------------------
**# sudo apt-get install pptpd ipx**
-------------------------------------
after that need configure file */etc/ppp/chap-secrets* adding line as shown
-------------------------------------
**name pptpd password "*"**  # here is "*" means dynamic ip address for client

and then need configure file */etc/pptpd.conf* adding line as shown
------------------------------------
[B]localip 172.20.0.1
remoteip 172.20.0.2-100[/B]
------------------------------------

Enter commands to the prompt
[B]# echo 1 > /proc/sys/net/ipv4/ip_forward
# echo 1 > /proc/sys/net/ipv4/ip_dynaddr[/B]



That's all we done it.
And if you would like clients to use Internet through the server as shown
----------------------------------------------------------------
**(clients)--------vpn-------(server)----------->(Internet)**
----------------------------------------------------------------

Enter command to the prompt
iptables -t nat -A POSTROUTING -o eth0 -s 172.20.0.0/16 -j MASQUERADE

That's all,

I am sorry in my bad English

---

