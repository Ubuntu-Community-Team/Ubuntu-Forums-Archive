---
title: "Where is the network manager config file and VPN group passwords?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by void09 on 2009-02-01
I am trying to import a Cisco VPN client config file to VPNC/network manager.

This config file already contains the group password, in encrypted form. When I import the settings, the encrypted GROUP password is not imported. Why?

I can copy/paste it somewhere, but in which file? I don't know where network manager stores its password...

Thanks...

---

### Post by void09 on 2009-02-01
KVpnc (an alternative to the connection manager) allows me to import even the encrypted group password, but then it says "error: Invalid ISAKMP exchange type received"

I'm clueless.

This is incredibly complicated. I am just trying to get a standard vpn connection, and I have been forced to recompile kvpnc (against OpenSSL) from source, try several applications, read about some strange ISAKMP, PKI, IKE, whatever, ...

---

### Post by void09 on 2009-02-03
Solved:
[http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Sending a password to some unknown third party for decoding obviously is bad policy. Anyway, one step closer in getting network manager vpn to work.

ps. the connection still doesn't work, though.

---

