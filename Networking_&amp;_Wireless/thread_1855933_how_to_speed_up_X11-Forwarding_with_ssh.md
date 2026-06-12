---
title: "how to speed up X11-Forwarding with ssh"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by vinterkind on 2011-10-07
Hei,

I would like to speed up the X-Forwarding through my SSH-Tunnel.
I've brought up a ssh gateway machine to which I connect for the tunnel.
then I can access the machines behind the gateway via tunnel.

the X-Forwarding via ssh -X is horrible ...

any experiences anyone ?

hilsen

---

### Post by haqking on 2011-10-07
> **vinterkind said:**
> Hei,

I would like to speed up the X-Forwarding through my SSH-Tunnel.
I've brought up a ssh gateway machine to which I connect for the tunnel.
then I can access the machines behind the gateway via tunnel.

the X-Forwarding via ssh -X is horrible ...

any experiences anyone ?

hilsen

X forwarding is slow.

you could try

ssh -X -C -c

where -C is compression and -c changes the cipher.

if it works you could edit your ssh_config so you dont need to type it everytime

try just the -C first, man ssh for more information

---

### Post by GrandTheft on 2011-10-17
try 

   ssh -XC4c arcfour,blowfish-cbc 

have fun

---

