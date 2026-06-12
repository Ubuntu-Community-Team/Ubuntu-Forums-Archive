---
title: "multihomed interfaces"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by br74649 on 2009-02-12
Hi All,

I am just getting to grips with ubuntu after years of solaris.  So please be patient with the newbie questions. 

I have a server with 2 nic's I have no firewall enabled as yet. 

my /etc/network/interfaces contains the following

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 eth1

iface eth0 inet static
        address 10.18.0.1
        netmask 255.0.0.0
        network 10.0.0.0
        broadcast 10.255.255.255
        gateway 10.1.0.5
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 172.17.0.2
        dns-search xxx.com

iface eth1 inet static
        address 172.22.0.127
        netmask 255.255.0.0
        network 172.22.0.0
        broadcast 172.22.255.255


the default gateway needs to be 10.1.0.5 as thats where all the traffic needs to go. (internet facing) 

now when i try to connect to the 172.22.0.127 it doesnt connect me, the packets are supposed to come in on eth1 and out on eth0 
a tcp dump does shows on eth1 mypc -> eth1, however on eth0 i see no packet leaving the system at all. 

ip route get 172.23.0.26 shows the default gateway being 10.1.0.5 which is correct. 

Is there a setting that is blocking return packets with a src address not being the interface that the packet is leaving from.

or am i missing something more fundemental. 

This behaviour works out of the box on the solaris boxes we are replacing with ubuntu.  

Thanks in advance for any light that can be shed on this

regards

Tony Mills

---

### Post by br74649 on 2009-02-12
Hi All,

Sorry have i posted in the wrong forum here?

---

### Post by jonobr on 2009-02-12
Salutations from a Solaris 8 SCNA.
I allowed that to expire and now, jsut get new jobs based on my charm and BS ability.

You are in the right forum.

You know you are routing between CLass A and B right?

Whilst serving as a bump to your post, heres a link which may help
which includes enabling a recommendation for enable IPv4 forwarding


Cheers

[http://ubuntuforums.org/showthread.php?t=39358&page=2]("http://ubuntuforums.org/showthread.php?t=39358&page=2")

---

### Post by br74649 on 2009-02-13
Hi there,

And thanks for the response, I am routing between class A & B its to do with how the balancers are setup, I have tried the ip_forwarding setting but it didnt make any difference, i should have put that in original post OOPs.... 

I am not trying to turn the machine into a router and if its anything like the ip_forwarding setting in solaris thats what that what it does. just when connections are made to the address on eth1 the response follows the default gateway on the eth0 interface

the server is internet facing so the default needs to be the internet. for testing purposes and the apache config (multiple ssl domains) we have address based virtual hosting.

so when i connect via the backend management interface it needs to follow the default. 

incoming...
my_pc -> default gw on pc lan -> eth1 on ubuntu server 

outgoing...
eth0 on ubuntu server -> default gw (load balancer) -> pc lan gateway

I hope this functionality is possible.

Best Regards

Tony

---

### Post by br74649 on 2009-02-13
Hi 

in addition

ip route get 172.23.0.26 

172.23.0.26 via 10.1.0.5 dev eth0  src 10.18.0.1
    cache  mtu 1500 advmss 1460 hoplimit 64

So the machine knows where it needs to go, but it just doesnt want to. 

Regards

Tony

---

### Post by br74649 on 2009-02-13
I have found the problem, 

so am updating the thread incase anyone else see's the issue

in /etc/sysctl.d there is a file called 10-network-security.conf

it contains this

# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

i changed that to a "0", rebooted and it now works as i need it to. 

it must have been dropping packets on the interface that didnt have src address of the interface it was leaving on.  

DOH....

Thanks for you help 

regards 

Tony

---

### Post by br74649 on 2009-02-13
is this a bug or just misleading. 

in /etc/sysctl.conf there is the following section

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

so i assume its turned off, however the /etc/sysctl.d/10-network-security.conf file has exactly the opposite in it, therefore the contradict each other. 

surely they should both be off or both be on. 

regards

Tony

---

