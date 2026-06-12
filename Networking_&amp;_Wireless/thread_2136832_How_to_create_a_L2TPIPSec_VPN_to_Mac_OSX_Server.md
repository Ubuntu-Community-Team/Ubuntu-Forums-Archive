---
title: "How to create a L2TP/IPSec VPN to Mac OSX Server"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by hansheijmans on 2013-04-18
I configured a Mac Mini with OSX Server to act as a L2TP VPN server. Configuring is quite easy, just choose L2TP, fill out the VPN host name and Shared Secret. Also I made some changes to the router to allow VPN traffic to be forwarded to this server.

Setting up Mac OS X and iOS clients is just as easy. Just fill out the same info as configured on the server, provide a user name and password and voila, **done in 30 seconds **on each client!

Now I want to use my Ubuntu box as a L2TP client as well. I tried installing l2tp-ipsec-vpn and all packages it depends on (like xl2tpd, openswan etc.) but whatever option I choose in the GUI, I cannot connect to the Mac!

Googling around didn't provide me with the answer as well. All I could find were loads of configuration files examples all related to connecting to VPN servers other than Macs.

Can someone explain to me how I can connect to a L2TP VPN running on OS X server? It shouldn't be the first time this was done, I presume.

Thanks in advance!

---

### Post by hansheijmans on 2013-04-29
Seems like I'm the only one??

---

### Post by dotpage on 2013-06-21
> **hansheijmans said:**
> Seems like I'm the only one??

Not the only one, but it's a hard question to find an answer for. I have been looking for a while. The closest I got was - [https://launchpad.net/l2tp-ipsec-vpn](https://launchpad.net/l2tp-ipsec-vpn)

I am trying to work the bugs out... 

Have you had any luck?

---

