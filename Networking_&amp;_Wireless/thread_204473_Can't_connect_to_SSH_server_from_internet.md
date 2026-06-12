---
title: "Can't connect to SSH server from internet"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by detectiveinspekta on 2006-06-27
I can connect to it from other computers in the network, but I try to connect to it via another SSH server on the outside to it and it gives
```

Permission denied, please try again.

```

ATM I have a standard adsl router > switch > clientcps + linux server
So I don't think its a networking problem, havn't set up portforwarding, but I suppose NAT automaticly does that.

---

### Post by Simian on 2006-06-27
** sorry I only Read half your Post :-# **

( I was going to ask about your router and port forwarding )

---

### Post by scxtt on 2006-06-27
you'll have to forward port 22 to the IP address of the box you want to connect to from the "outside" - otherwise the request (from an IP outside your network) hits the router and has no idea where to go ...

---

### Post by detectiveinspekta on 2006-06-27
Ah yes thanks the portforward worked. I was told on irc that I didn't have to do this if I had NAT working. It would connect but didn't authenciate. Thanks

---

### Post by Nisun on 2006-06-27
I'm having a similar issue. Let me see if I can lay it out.

| Internet |---| Router |---| Ubuntu |

Basically I VPN in to the router machine then ssh in to the Ubuntu Box. I tried forwarding ssh though the Router to Ubuntu but its unresponsive. I have forwarded ssh to a slackware box and it seems to work fine. When I VPN in to the router I can ping and connect to every other machine on the network except the Ubuntu machine.

I remember it used to work but maybe I updated?

---

### Post by nzruss on 2006-06-27
Nisun, you've installed ssh?

```
 sudo apt-get install ssh
```

---

### Post by tturrisi on 2006-06-27
re the port forwarding:
best to config the ssh server to listen on something like 3022 or another port other than 22 for a home server, and config clients to connect to that port.  This is for security because an open port 22 is a target for undesirables.

---

### Post by Nisun on 2006-06-28
1) Yes I have SSHD installed..... perhaps my post was unclear. It works when im on the local network, but not from the internet or from VPN.

2) Changing the port number? Why would I even begin to mess things (change things) up when I dont have things working. Yes 22 is obviously SSH but I plan to only connect to this server over VPN or LAN.

---

