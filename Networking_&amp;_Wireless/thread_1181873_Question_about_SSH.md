---
title: "Question about SSH"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by blazemore on 2009-06-08
Okay so I just got started with SSH.
I understand port forwarding.

I have a number of machines connected to a router, each running SSH.
Is there a way to connect to a specific one from outside the network (Over the Internet), knowing the LAN IP of the server in question, without using port-forwarding?

Example:

I am in an Internet cafe and want to connect to my torrent box. The IP of the torrent box is 192.168.1.103
The IP of the router is 82.55.2.255 (Made it up, I apologise if this is actually your IP :P)

Is there a way I can SSH into the torrent box?

Thanks!

---

### Post by superprash2003 on 2009-06-08
well you will need to open port 22 for ssh, or you could tell ssh to listen to another port , but an open port is required

---

### Post by brabo on 2009-06-08
as superprash already indicates... you need to forward a port from your router to the box. if you don't do that, the router doesn't know what to do with an incoming connection.
you can use different ports on the router to forward to different systems, like:
port 1111 to ip 192.168.1.1 port 1111
port 2222 to ip 192.168.1.2 port 2222
i would advice to choose a different port than 22, since there is much hammering on that port.
you set it through the Port option in /etc/ssh/sshd_config
also, set  PermitRootLogin to 'no'
you should use sudo.
don't forget to restart sshd through sudo /etc/init.d/ssh restart

hope that's clear enough.
brabo.

---

### Post by UBSec on 2009-06-08
Hi, 

If you want to access to your servers behind a router from the outside , you have some  choices.

> As it's been said before you need port forwarding (it seems you dont want to do so) .
Suppose u have an external IP address : 80.80.80.80 and a local LAN 192.168.1.0/24.
Suppose you have 3 ssh servers :
srv01 : 192.168.1.1 listeninng on port : 2221
srv02 : 192.168.1.2 listeninng on port : 2222
srv03 : 192.168.1.3 listeninng on port : 2223

On your router, you have to forward all traffics coming from 80.80.80.80:2221 to srv01,
80.80.80.80:2222 to srv02 ....

so when you will enter ssh 80.80.80.80:2221 you'll be prompted to log into srv01 and so on.

> If you don't wanna make port forwarding , unless you have your server listenning on 80.80.80.80: port ( where port can be whatever legal port), and when you get logged you can then ssh to your local servers. If there is no ssh server on your router (i can suppose) you need at least one port forwarding to the central server (which host  sshd) and then connect to the server.

> The third solutions is to establish a VPN (openvpn) which can make your hosts available from the outside ( type of vpn : host - to - LAN) . Here also you will need at least one port forwarding to join the VPN server. It's quite the same as the previous solutions , but you have the security and you will need only one ssh directly to yours servers.

UBSec

---

### Post by Iowan on 2009-06-08
I can't say I've tried (I don't have that many SSH servers on my network at the moment) but it *might* be possible to SSH into the router (if it has SSH server), then SSH from there to a different machine (if router also has SSH client).

---

### Post by terrrorr on 2009-06-08
Hi,

Notice: Best practice is that your router is your router and nothing else (of course some times they could be also firewalls but I think you got the point). You really do not want to open any access to your router from outside your LAN -> Do not use your router as a SSH-server even it is possible. 

Use port forwarding to access one of your servers (ie. server1) and manage other ones from there.



- Terrrorr

---

### Post by Iowan on 2009-06-08
> **terrrorr said:**
> Notice: Best practice is that your router is your router and nothing else (of course some times they could be also firewalls but I think you got the point). I'm inclined to agree - I even moved the DHCP server off the router.

---

### Post by blazemore on 2009-06-09
So there's no way of saying to the router - "I want you to send this request to the computer on your network with this address"?

---

### Post by mr.propre on 2009-06-09
Could hostnames work?

---

