---
title: "NIC bridging"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by kr651129 on 2009-01-06
Hi All,
  Ubuntu Server 8.10 Server
  Pentium 4 32-Bit 2.5GHz
  2GB RAM
  100 GB HDD
  2 Generic NICs

I was wondering how you could take two NIC's bridge them, make one handle the incoming traffic and the other handle the outgoing traffic.  I have fiber to the prem and from that I have a cat6 going into a Linksys wireless router, and I have my server on port one.  I would like the cat6 to go to the server on card 1, then output on card 2, then take the output and put that into the router, this way I can monitor network traffic.  Ideas, questions, comments?  Maybe there is a better better way of doing this, thanks for your help!

---

### Post by puppywhacker on 2009-01-06
I don't fully understand your setup, but eitherway you have a few choice

1 ethernet bridging with brctl like this
[http://tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO-3.html](http://tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO-3.html)

2 NAT with iptables and masquerading

3 setting up routing tables to decide which network interface you need.

---

### Post by kr651129 on 2009-01-06
> **puppywhacker said:**
> I don't fully understand your setup, but eitherway you have a few choice

1 ethernet bridging with brctl like this
[http://tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO-3.html](http://tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO-3.html)

2 NAT with iptables and masquerading

3 setting up routing tables to decide which network interface you need.

this is what I'm trying to do:
```

                      fiber line
                           |
                           |
                           |
                         cat6
                           |
                           |
                         (nic1)
                        -ubuntu-
                         (nic2)
                           |
                           |
                         router
                           |
                           |
                       |network|

```

---

### Post by puppywhacker on 2009-01-07
cool, so most likely you want to do masquarading using iptables. (and ip_forwarding)

The bridging option and the routing option would be for piping everything straight through. Guess that is not what you want.

---

