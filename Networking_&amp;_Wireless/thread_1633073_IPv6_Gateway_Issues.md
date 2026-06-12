---
title: "IPv6 Gateway Issues"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by guiclaw on 2010-11-28
Hi,

I'm currently doing some experimentation with IPv6 for a University project but I've run into a couple of problems.

I've managed to successfully configure both a 6to4 tunnel, and a tunnel broker from sixxs on different machines with no problem - either of these configurations allow the machine this is configured upon access to sites such as ipv6.google.com and access into my University via IPv6 so I know that this aspect of things is working perfectly.

The problem arises when I try to share this out to the LAN behind this gateway machine. I've configured radvd, and client machines do indeed get an address from the /64 that I've been assigned from the broker, and I can ping6 between all machines both on the fe80: link local and the global 2a01: address.

I have IPv6 forwarding enabled via sysctl, and the default policy in ip6tables for all tables is set to allow.

When I do a traceroute6 on a client machine, it does hit the gateway but then seems to die. As the gateway machine can access the global IPv6, I believe it's something to do with the routing setup on the gateway, however I'm really not sure where the problem lies, as I assume that if the gateway can access outbound IPv6, then with forwarding enabled other machines should be able to route though?

I appreciate any help anyone can give on this issue! It seems to be rather puzzling as I've also followed multiple IPv6 gateway setup guides, including adding a 2000::/3 route to my tunnel device all to no avail!

This is on my main 10.04 testing machine, though I've got the same issues on 10.10 and on an old install of 9.04.

Thanks in advance!

---

