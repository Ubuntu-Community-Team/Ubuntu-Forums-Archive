---
title: "Can ssh into server with IP but not with host name"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by archknight on 2010-05-11
I have tried searching around on the Internet for this but I wasn't very successful in finding answers. I got a computer running Lucid Lynx with a ssh server running on it. When I try to ssh into it, I get a message saying that it cannot find the host. I run "hostname" in a terminal and it matches what I believe to be the host name. However, if I type in the IP address instead of a host name, SSH works exactly as expected. There aren't any firewalls between the Ubuntu server and the connecting PC (unless Ubuntu has a firewall on it that I don't know about). When I try pinging the host name, it also fails to find it but the IP address works. So, what can I do to make the host name work?

---

### Post by Iowan on 2010-05-11
The quick/dirty method is to make a hostname/IP entry in */etc/hosts*.

---

### Post by archknight on 2010-05-12
I am not sure what you mean. At the moment, the host name is already in the /etc/hosts file. I don't see how that helps other computers recognize the server though. This is what I see in my hosts file:



127.0.0.1       localhost
127.0.1.1       host_name_of_my_choosing

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by archknight on 2010-05-12
I appreciate any help someone can give me with this issue. What are some possible solutions to this problem?

---

### Post by Iowan on 2010-05-12
Sorry, I should have mentioned that the entry goes on the client machine.

---

### Post by archknight on 2010-05-12
Thanks but that doesn't really help. I could have just as easily created an alias that did that. There are a large number of client computers that I don't have access to as well as personal computers that need to be able to connect to this system. There should be a way of making this work. Or else, what is the point of a host name if can't be used by other computers, but instead must be attached to an IP address?

---

### Post by Iowan on 2010-05-12
Hence the "quick/dirty". 
Another option is to have a local nameserver. I have DNSMasq for a DHCP/DNS server on my network. DHCP clients can be accessed by hostname. I issue static leases to some of the other servers, so they're in there, too. Static addresses (like the router) are tracked because they have been entered in the DHCP/DNS server's "hosts" file.

Some routers have that built in - but the clients must use the "send host-name" option in */etc/dhcp3/dhclient.conf*.

---

### Post by CharlesA on 2010-05-12
> **Iowan said:**
> Hence the "quick/dirty". 
Another option is to have a local nameserver. I have DNSMasq for a DHCP/DNS server on my network. DHCP clients can be accessed by hostname. I issue static leases to some of the other servers, so they're in there, too. Static addresses (like the router) are tracked because they have been entered in the DHCP/DNS server's "hosts" file.

Iowan hit it on the head.

Sounds like you have no name resolution on the network.

---

### Post by archknight on 2010-05-18
So uh... thanks for attempting to help. I located a linux guru and asked him about it. Apparently, the problem is that you can't just connect by the hostname. I had to use hostname.local instead. With that, it worked and the problem is resolved. I figured I should post a solution for those who are interested.

---

### Post by kevdog on 2010-05-18
Iowan

Although this guy posted a solution, I'm not convinced this is the only way.  Modification of the /etc/hosts file or local dhcp server (such as modification of the file on the opendns router/dhcp server works for me).  Seems like you know more about this stuff than me however.

---

### Post by CharlesA on 2010-05-18
> **archknight said:**
> So uh... thanks for attempting to help. I located a linux guru and asked him about it. Apparently, the problem is that you can't just connect by the hostname. I had to use hostname.local instead. With that, it worked and the problem is resolved. I figured I should post a solution for those who are interested.

I can connect just fine by using the hostname (and not by using the FQDN). I however have my DHCP server set up so that it gives the correct DNS domain name for each machine.

My server is named thor.lcl and my dns domain name is .lcl on all machines, as given out my the DHCP server. I can connect just using "thor"

---

