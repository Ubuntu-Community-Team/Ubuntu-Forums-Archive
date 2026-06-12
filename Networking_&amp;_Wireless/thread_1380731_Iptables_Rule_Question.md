---
title: "Iptables Rule Question"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by eatsubway on 2010-01-14
Hello...

I'd like to create an iptables rule which blocks all connection on port 21 and 22 that's not from a specific host.

Correct me if im wrong but the notation 111.222.0.0/32 indicates all ip addresses with the host 111.222 right? If so I'd like to block everything that's not 111.222.0.0/32 on port 21 and 22.

Please include the syntax for this rule and the location it is to be place in (im guessing host.deny). Thanks

---

### Post by carverj on 2010-01-14
Sorry, there cannot be a class A host with an IP address of 111.222.0.0
Do you mean something like 10.0.0.1/32?

Have a look at this howto. It is very good:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

---

### Post by eatsubway on 2010-01-14
It's actually a class B, I just used 111.222 as an example.

---

### Post by DGortze380 on 2010-01-14
a 32 bit CIDR specifies that every host is on a separate network (ie. the specific address).

111.333.0.0/32 includes the address 111.333.0.0
111.333.0.0/24 includes the addresses 111.333.0.0 - 111.333.0.255
111.333.0.0/16 includes the addresses 111.333.0.0 - 111.333.255.255
111.333.0.0/8 includes the addresses 111.0.0.0 - 111.255.255.255

You can also have VLSMs (Variable Length Subnet Masks)

You can also have classless addressing (so yes, for the purpose of iptables you can have a 'class A' with a 32 bit CIDR, or a 'class A' with a 16 bit CIDR etc...)

But that should get you started.

So the rule you posted actually specifies a network with 1 address.

If that's what you meant to do that's fine, but it's better to just specify a host then, not a network.

If you meant to specify a network, you'll need a CIDR other than 32.

---

