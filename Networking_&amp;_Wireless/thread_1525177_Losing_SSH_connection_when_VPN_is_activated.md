---
title: "Losing SSH connection when VPN is activated"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by TL_CLD on 2010-07-06
Hey all,

A friend of mine is running Ubuntu. He used to run Windows XP, but he kept destroying it completely, and I soon got tired of fixing it for him. So I setup Ubuntu, and we're both happier people for it.  :)

BUT!

The other day he asked me to setup a VPN (PPTP) connection to his workplace, which I promptly did. It also just works, except for one minor problem: When he fires up the VPN connection, I lose the ability to connect to his computer over SSH. As soon as he shutdown the VPN connection, I can once again log in over SSH.

I use the SSH connection for basic maintenance and for tunneling port 5900 so I can assist him over VNC. Now if he needs help, he's forced to shutdown his VPN connection, before I can log in, which naturally is a bit of an annoyance.

Is it possible to solve this problem?

His nic is setup with DHCP.
Gateway is 192.168.57.1.
Port 22 is NAT'ed to 192.168.57.2, which is the IP his computer is assigned by the router (it's reserved to his MAC address).
When he connect the VPN, a new interface is created with the IP 192.168.1.32.

I'm very much _not_ a network expert. I can manage the very basic stuff, but beyond that I'm quite lost.  :)

---

### Post by TL_CLD on 2010-07-06
This appears to, perhaps, solve my problem:  [http://ubuntuforums.org/showpost.php?p=7301956&postcount=20](http://ubuntuforums.org/showpost.php?p=7301956&postcount=20)

I'm going to try that, and hopefully succeed in getting back my SSH access to the computer, despite having an active VPN connection.

---

