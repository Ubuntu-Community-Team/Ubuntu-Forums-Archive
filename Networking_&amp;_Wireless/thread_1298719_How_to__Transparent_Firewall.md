---
title: "How to : Transparent Firewall"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by supersabre_22 on 2009-10-23
I know alot of people are going to say "You should do it this way" "There's a better way" but I'm trying to teach myself a proof of concept.  

I know this "can" be done,  I just can't work out how.  

I need to understand how to structure IPTABLES to make  device completly transparent but still be able to do things such as firewall and proxy.  

         Router                                 Ubuntu                                    PC
  192.168.0.254               192.168.0.10      192.168.0.11            192.168.0.1
     -----------                           ----------------------                     ------------
| NIC_Router |---------------|  eth0     |          |  eth1  |-----------|  NIC_PC    |

The Gateway on the PC is 192.168.0.254

How on earth do I get this to work?

---

### Post by bapoumba on 2009-11-05
Moved to networking & Wireless.

---

