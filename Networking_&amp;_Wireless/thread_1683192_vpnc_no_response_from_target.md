---
title: "vpnc: no response from target"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by tnorgd on 2011-02-07
I have a macbook from which I connect to my company's  VPN using L2tp. This is a "shared secret" session. Now I want to  connect from a ubuntu box.  
  I've already done a lot of research on the web and installed vpnc, which is supposed to solve the problem. I put the following:
  IKE Authmode psk 

Local Port 10000 NAT 

Traversal Mode cisco-udp
  into /etc/vpnc/default.conf file and I give the right username/passwd from the command line when connecting, but the only results is "vpnc: no response from  target".
  One (possibly important) thing is that "Group name" in my mac's VPN Authentication settings is left blank.
  Can anyone help we with this?

---

