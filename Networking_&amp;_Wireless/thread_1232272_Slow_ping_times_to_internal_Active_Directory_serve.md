---
title: "Slow ping times to internal Active Directory servers"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by nikolaidis on 2009-08-05
I just did a fresh install of Ubuntu 9.04 on my HP dc5800 desktop system. 
 
When I ping a server on my internal subnet by NETBIOS name, the name immediately resolves to the correct IP address, but it takes approximately 4 seconds before I get the first echo reply. Subsequent replies also take several seconds. 

For example, if I try to ping my domain controller by its NETBIOS name (e.g. "dc2"), it resolves immediately, but pings take 4 seconds before they respond. 

If I ping by its FQDN (e.g. "dc2.domain.local"), the name fails to resolve.

By contrast, if I ping a server's IP address directly (e.g. "192.168.100.29"), it responds immediately and sends and receives an echo request once per second. 

The machine specified in my examples is my DNS, which is provided by DHCP. 

When I ping any of my physical or virtual Linux or Windows servers, I get the odd, slow ping times. When I ping a NAS device, my router, or anything outside my network (Google, OpenDNS, etc.) I get responses as expected. 

I know the hardware (gigabit NICs and switches) is fine, as when I boot into Windows, everything works normally. Unfortunately this is keeping me from reliably accessing things on my LAN, and causing services like Likewise to fail authentication so I can't join the domain. 

Has anyone seen this behavior before? Any suggestions?

Thank you,

Peter

---

### Post by Technoviking on 2009-08-05
What does your /etc/hosts file look like. In the past disabling ipv6 has fixed the slow ping problem, but I don't think you can disable it anymore in Ubuntu 9.04+.

T-V

---

### Post by nikolaidis on 2009-08-05
Hey T/V!

My hosts file looks as expected, namely pointing to my domain (domain.local), search domain (also domain.local) and DNS server (192.168.100.29 - one of the machines I can't reliably ping by hostname but can just fine by IP address).

It doesn't really sound like an IP4 vs 6 issue to me, as I can ping by IP address just fine, but who knows? 

Thanks,

Peter

---

### Post by nikolaidis on 2009-08-05
Whoops! You asked about /etc/hosts and I replied with /etc/resolv.conf. Not the same! :)

My hosts file definitely has some IP6 cruft:

```
127.0.0.1	localhost
127.0.1.1	exemplar

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by nikolaidis on 2009-08-05
I just tried adding 

```
 ipv6.disable=1
```

to the end of my chosen kernel in /boot/grub/menu.lst 

As root, did a

```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```

and commented out all of the IP6 stuff in /etc/hosts.

No change. :(

Peter

---

### Post by stuart.ward on 2009-08-10
From what you were describing it sounds like the problem you are having is associated with DNS lookups. So if dig responds with an IP address quickly try dig -x <ip address of your server>

I suspect this is to do with nsswitch which tells resolve figure out where to look up names, if one of these sources is timeing out (4seconds) that match your symptoms.

Stuart

---

### Post by nikolaidis on 2009-08-10
Hi Stuart,

I agree it sounds like DNS, but I can't fathom why it's causing a timeout in between pings (as if it's doing a lookup between each). 

Both of my internal DNS servers are amongst the slow ping responders. When I do a dig -x <internal server IP> 
the response comes back almost immediately. Same story when I dig against the other internal DNS box. 

Another oddity is that my resolv.conf always puts one nameserver (192.168.100.29) in twice, not the two different ones that are assigned via DHCP, which could be related. 

Thanks,

Peter

---

### Post by nikolaidis on 2009-08-26
Looks like this is the bug found at 
[https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/94940)

I did the same fix, editing my /etc/nsswitch.conf file, and now my internal ping times are zippy.

---

