---
title: "Static address prevents access to internet"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by Rhemat on 2012-06-12
I have a Virtual Machine acting as a MineCraft server, and I have been trying to specify a static address on it so that I won't have to worry about it changing.  However, every time I change it, it prevents any access to anything but the machine it is on.  I have done a network map, just to make sure that there was no IPv4 address conflict, but there is no conflict (I really only have 4 devices on that subnet).

Current devices on the network:

Desktop - 192.168.0.5 (via DHCP)
Server -  192.168.0.32 (static)

Addresses I've tried:

192.168.0.2  (Was previously assigned via DHCP)
192.168.0.6  (Was previously assigned via DHCP)
192.168.0.36
192.168.0.48
192.168.0.210

No matter what, when I assign a static address, it will not communicate with anything aside from the host machine it is on.  Is there anything I can do to fix this?

Thanks in advance.

---

### Post by Ashtechsmith on 2012-06-12
An Internet Protocol address (IP address) is a numerical label assigned to each device (e.g., computer, printer) participating in a computer network that uses the Internet Protocol for communication.An IP address serves two principal functions: host or network interface identification and location addressing. Its role has been characterized as follows: "A name indicates what we seek. An address indicates where it is. A route indicates how to get there."

---

### Post by Rhemat on 2012-06-12
I do understand what an IP address is, what function it serves, etc.

What I want to know, is why giving it any static address renders the VM unable to communicate with anything other than the host.

---

### Post by chili555 on 2012-06-12
What DNS nameserver did you give?

---

### Post by Rhemat on 2012-06-12
They don't have a DNS name server at this point, as I don't have a domain yet.

---

### Post by chili555 on 2012-06-12
> No matter what, when I assign a static address, it will not communicate with anything aside from the host machine it is on.And how are you trying to communicate? Can you ping the router? Can you:```
ping -c3 8.8.8.8
```Without a DNS nameserver, you will not be able to reach the internet by name. It needn't be your own domain.

---

### Post by Rhemat on 2012-06-12
I'm not sure what happened, but to get my facts straight, I followed the first (and so far best rated answer) from Bart De Vos at this URL:

[http://superuser.com/questions/357120/how-do-i-setup-a-virtualbox-server-with-a-static-ip](http://superuser.com/questions/357120/how-do-i-setup-a-virtualbox-server-with-a-static-ip)

I not only specified the address, and mask, but also network, gateway, and broadcast.  Now, the machine can communicate with the rest of my network.  I'm sorry I mis-typed the topic; getting it to access the internet was an issue, but not the one I was attempting to address.

Thanks anyway.

---

