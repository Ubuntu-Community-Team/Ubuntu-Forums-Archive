---
title: "/etc/resolve.conf in the wrong order"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by djshaw on 2009-10-31
Hey,

So, whenever I try to ping a peer on my network, I get a "ping: unknown host <host-name>". I know the host is alive and responding to pings because my windows box can ping it just fine.

When I look at my /etc/resolve.conf, I see:
> 
domain phub.net.cable.rogers.com
search phub.net.cable.rogers.com
nameserver 192.168.1.1
nameserver 64.71.255.198


I am assuming that 'nameserver 192.168.1.1' should be at the top of the list. From what I understand, I should not modify /etc/resolve.conf and modify /etc/dhcp3/dhclient.conf instead.

My dhclient.conf is (basically the default dhclient.conf):
> 
send host-name "chaos";
prepend domain-name-servers 192.168.1.1;
request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, domain-search, host-name, netbios-name-servers, netbios-scope, interface-mtu;



It looks as though "prepend domain-name servers 192.168.1.1;" isn't actually prepending to the list of domain nameserver.

Does anyone know what is going on here?

Thanks,
-Derek

---

### Post by Iowan on 2009-10-31
I was gonna ask if you restarted/rebooted after changing the file, but it occurred to me that 192.168.1.1 _IS_ at the top of the nameserver list. Does 192.168.1.1 run a DNS server? I disabled DHCP on my modem and installed **dnsmasq** on my server to tie DHCP and DNS together.  Short term, you could add address/name to */etc/hosts* but that doesn't work well for DHCP addresses.

---

### Post by djshaw on 2009-10-31
> **Iowan said:**
> I was gonna ask if you restarted/rebooted after changing the file, but it occurred to me that 192.168.1.1 _IS_ at the top of the nameserver list. Does 192.168.1.1 run a DNS server? I disabled DHCP on my modem and installed **dnsmasq** on my server to tie DHCP and DNS together.  Short term, you could add address/name to */etc/hosts* but that doesn't work well for DHCP addresses.

I restarted the service with 
> 
sudo /etc/init.d/networking restart


192.168.1.1 is a stock WRT54G (v2, if I remember correctly. Machines are routinely added and removed from the network. No address stays the same for long (most change every month or so).

---

### Post by mpokrywka on 2009-11-01
What is output of:

dig PEER_HOSTNAME

Specifically, which server is used? SERVER line, third from bottom.

---

