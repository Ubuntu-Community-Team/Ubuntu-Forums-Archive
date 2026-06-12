---
title: "Share an SSH Tunnelled SOCKS proxy?"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Halkus on 2011-02-06
I've opened an SSH Tunnel/SOCKS proxy on my Ubuntu server, which I've tested is working exactly as I had intended.

However I'd like to access it from my Windows PC which is on the same home network. 

Is this possible?

Edit : I should say that I got it working on the server only by ```
 ssh -D 55555 user@host 
``` However if I tried it with a port, e.g. ```
 ssh -D 192.168.1.101:55555 user@host 
``` then it doesn't work, not even on the server itself. 192.168.1.101 is the static assigned DNS of my server on the home network.

---

### Post by Halkus on 2011-02-06
Inexplicably it now works, with seemingly no reason why it didn't before!

---

