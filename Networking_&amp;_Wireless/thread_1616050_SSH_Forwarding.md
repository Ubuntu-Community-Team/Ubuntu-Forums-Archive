---
title: "SSH Forwarding"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by eternity0022 on 2010-11-07
Hi everyone,

Im trying to run a kippo honeypot which listens on port 22 however Ubuntu 10.10 does not allow me to do so as a normal user, on the other hand kippo honeypot can not be run as root.
I am running the honeypot on a static public IP address, firewall disabled and no services listening on port 22.

is there any way to forward the incoming connections on port 22  to another port for example 2222(which kippo works on)?
I have also tried authbind, setcap with no luck.

any help is appreciated

---

### Post by hackertarget on 2011-02-10
> iptables -A PREROUTING -t nat -p tcp -d yourpublicipaddress --dport 22 -j REDIRECT --to-port 2222

Note that this will not work if you try connecting to port 22 locally to test.

Connect from another system that has access to 22 on your public IP.

---

