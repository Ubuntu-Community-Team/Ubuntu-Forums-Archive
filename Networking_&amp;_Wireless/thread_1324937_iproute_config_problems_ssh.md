---
title: "iproute config problems ssh"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by javabean420 on 2009-11-13
hello i am trying to figure out ssh and i am haveing routing problems.

i have between the 2 comps 2 routers... one closest to "client" (the one i am using TO connect) is ddwrt so its a bridge to the wireless router which the "server" uses to connect... i just can't seem to find the "right" manual that can help...

Specs
(client)lxde+ubuntu(not yet nuked gnome)9.10 + blowbox 380 addressed 192.168.1.2xx hardwired to DD-wrt(ed) wifi router at 192.168.1.x which is connected via wifi to main router at 192.168.1.x to which connects via wifi to the "server" at 192.168.1.1xx pista home/lxde+xubuntu9.10 the linux is the target of the ssh

thank you for your time

---

### Post by earthpigg on 2009-11-13
have you enabled port forwarding on your router?

the easiest way to test if this is the problem is to disable the router's firewall briefly and see if you can connect then.

---

