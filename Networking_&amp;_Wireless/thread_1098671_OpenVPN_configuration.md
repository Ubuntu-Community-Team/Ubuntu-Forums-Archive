---
title: "OpenVPN configuration"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by tondop on 2009-03-17
I configure VPNserver (openvpn) config and i dont now what does it mean item - "Which local IP address should OpenVPN listen on? (optional)".

My server have only one network card, that has external IP. This machine does not the local IP. What shall I fill in there?

---

### Post by tondop on 2009-03-17
My next question is, that how can i be sure that a port is open. i want to open port XYZ in ubuntu...

---

### Post by uzi09 on 2009-03-19
Sorry, I'm having trouble understanding your first question.

As far as your second question, chances are if you stuck with a basic install of OpenVPN, you'll just need to open a port on your router.

Please see the following link on how to port forward correctly (which will open a port on your router)
[http://portforward.com/](http://portforward.com/)

---

### Post by tondop on 2009-03-21
Thanks

Now I'm have other problems with configuring OpenVPN.

OK, I can connect to VPN server – no problem, but I cannot ping any other computer behind that server.

I can ping computer192.168.1.15 on LAN from VPNServer but I can't ping from VPNClient. This vpnclient is not from LAN..

I can ping over the VPN to the server (10.42.5.1), but I cannot ping to other internal boxe.

What's wrong?

---

