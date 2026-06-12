---
title: "Nat from bonding NICs?"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by fela on 2011-07-31
Hi

I'm thinking of a possible configuration of a proposed network in my friend's flats, which includes bonding two ADSL connections for a faster speed.

Two ADSL2+ modems will plug into a dual teaming ethernet card in a Linux server. The rest of the network will plug into another NIC in the server. The server will run DHCP to the network and act as a router with NAT.

The thing I'm wondering about is first of all, how to set up the dual teaming NIC with Linux. Then of course, how to use IPTables to create a NAT firewall from the two teamed / bonded connections to the third (internal) NIC.

Maybe this diagram will show what I want more clearly: [http://sixteennet.co.uk/malnetwork.jpg](http://sixteennet.co.uk/malnetwork.jpg) :P

(click here if that link didn't work: [http://imageshack.us/f/34/malnetwork.jpg](http://imageshack.us/f/34/malnetwork.jpg) )

Thanks alot :D

---

### Post by fela on 2011-07-31
Never mind, I think I've figured it out.

---

