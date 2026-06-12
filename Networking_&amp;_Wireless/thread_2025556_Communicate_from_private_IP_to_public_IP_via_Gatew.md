---
title: "Communicate from private IP to public IP via Gateway"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by pradeepuppu on 2012-07-14
Hi,
 I am trying to connect the one computer(named Z) with public ip and another computer with private ip(named X) with the help of another computer as gateway(Y). Gateway(Y) is connected to the internet and it shares the internet to computer(X). The computer"Z" is connected to other network. Now i want to communicate From X to Z. I can able communicate with the same setup in Windows7 its working fine(but in reverse direction(Z to X) is not achieved in win7). The same setup with all computers Ubuntu as Os is not working. Can any one please help?
 Thanks in advance.:)

---

### Post by texpat on 2012-07-14
Hi there,

I'm a slightly out of my depth here, so please be patient if I do not understand the problem correctly.

To start with, you call "Y" a "gateway". I'll assume that could be a router. Communicating X-(Y)->Z is straigtforward, because Z has a public IP address.

To communicate to "X", which is on a private network (and probably has an IP-Address that looks something like 192.168.1.xx), you need the router's ("Y") public address. You can get that, for example, by going to [www.whatismyip.com](www.whatismyip.com) from a computer behind "Y", so for example from "X". If that IP address is dynamically allocated by the ISP, it will change from time to time and you need a service like dyndns.org* or similar to keep track of the changes and map the IP address to a domain name.

On your router you need to do two things:

1. Assign a static IP address for "X".
2. Enable NAT so that incoming traffic will be routed to "X".

How this is done depends on the router, but it should be described in the router's documentation.

*dyndns has changed a lot since I started using it, so you may have to find an alternative.

---

### Post by Kirk Schnable on 2012-07-15
Texpat, I understood the question the same way, and your solution is accurate. 

pradeepuppu, if we have misunderstood what you're trying to do, it might be useful to furnish us with a diagram. 

Kirk

---

### Post by pradeepuppu on 2012-07-16
Hi,
 Thank u Texpat and Kirk. 
 Sorry, I did not explained clearly what my doubt is?. 
@ Texpat i cannot use router as gateway. I want to use my computetr as gateway. 
I  can able to communicate in one direction X->Z via Y(gateway). but i  am not able to communicate in reverse direction (Z->X via Y). 
Some of my friends suggested to do port forwarding in ubuntu at gateway that means what ever the data coming to Y forwards to X.
  Is taht possible? Can you plz give your suggestions? @Texpat and Kirk. 

 For better understanding i am including diagram.



Y is connected to the internet via a USB modem. 
Z is connected to the internet (other network not as Y) via Ethernet cable.

---

### Post by pradeepuppu on 2012-07-16
Hi , this is my diagram

---

### Post by texpat on 2012-07-17
> **pradeepuppu said:**
> ... I want to use my computetr as gateway...

Yikes! This is well beyond my skills. You still need the routing and NAT functionality on "Y", so you need software to do that. This involves 2 network adaptors and fiddling with iptables.

Sorry, friend, I can only point you to this article: [http://forums.extremeoverclocking.com/showthread.php?t=213442](http://forums.extremeoverclocking.com/showthread.php?t=213442) and hope you're cleverer than I am.

Or perhaps someone else on these forums can help.

---

### Post by pradeepuppu on 2012-07-21
Thank you Texpat..

---

### Post by SeijiSensei on 2012-07-21
Are all these computers running Ubuntu?

One solution is to use OpenVPN to set up a static tunnel from the client with a private IP to the public machine.  Follow the steps in [this HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  Install the openvpn package with "sudo apt-get install openvpn" on both machines.

OpenVPN also has a version for Windows if one of these machines is running that.

---

### Post by bakegoodz on 2012-07-21
I'll chime in since I didn't see a clear answer to how one can reach a private ip (192.168.x.x, etc) from a public ip.

The issue is that public IP computers/devices only see other computer/devices with public IPs. So the computer with a public IP can only talk through the gateway/router to the computer with a private IP.

This works in one direction because when the Private IP computer makes a request through the Gateway and it uses NAT to keep track of conversations to the outside world and knows which computer to forward the conversation in it's own network.

It's more complicated the other way because the public computer doesn't have a direct way to access computers in the private network. (192.168.x.x is not a vaild IP address to a Public computer) 

Port forwarding is one solution, becuase different network services/protocals are assigned ports such ssh uses port 22. For example, you could setup the gateway to use ssh on another port number and have port 22 get redirected to port 22 on the Private IP computer. Port forwarding configuration would depend on what router/firewall software is running on the gateway.

Since all computers are under your control you could also setup a VPN. There are many software and hardware solutions. It basicly it sets up a Virtual Private Network that can "tunnel" over the Public Internet and connect 2 or more internet connected locations to have the same local network or rather same network range, such as 192.168.1.x

---

