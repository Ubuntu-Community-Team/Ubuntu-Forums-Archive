---
title: "Squid Problems"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by CyberAxe on 2010-10-14
Currently my work network is setup thus..

For computers that are outside the ranges of 192.168.0.0/24 and 192.168.1.0/24 the DHCP Gives the local server IP 192.168.0.1 as the DNS Server which is running DNSMasq it also provides the OpenDNS servers as backup, 208.67.222.222 and 208.67.220.220 so that when DNSMasq doesn't resolve it loads through OpenDNS.

For the ranges of 192.168.0.0/24 and 192.168.1.0/24 it provides the DNSMasq Server plus the ISP DNS Servers so that there is no restricted access.

I am attempting to setup squid but i want to get squid working in tandem with this setup so computers will be able to access or not access based on their ip address.

The two problems i have is 1 Squid will only resolve DNSMasq hosts if DNSMasq doesnt resolve then it throws an error along the lines of "access denied by the DNS Server" but if i setup DNSMasq so that it uses the resolv.conf which is setup to use the OpenDNS servers then it will resolve and work

Squid doesnt seem to use the secondary servers in resolv.conf which is the same as the first paragraph just the dnsmasq then doesnt attempt the others if that fails.

The other problem is it will only resolv using one set of dns servers i want to make it so if 192.168.0.5 tries to use the proxy they can still access facebook.com for example while anyone from 192.168.2.x is given the opendns blocked page.

---

### Post by SeijiSensei on 2010-10-15
I don't know about DNSMasq, but the simplest method for controlling access via Squid is using [ACLs]("http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators").  You can permit or deny access by an enormous range of options including source IP, URL regexes, etc.

I'm just curious, but if this is a workplace network, why don't you run bind9 on a local server and handle all DNS issues internally?

---

### Post by CyberAxe on 2010-10-18
As when i initially setup the network i couldnt figure out bind9 hence why i setup dnsmasq, though i was planning on going back and learning bind9 at some point.

---

