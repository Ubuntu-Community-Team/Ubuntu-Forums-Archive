---
title: "Shorewall Configuration for PPPoE.. {Help Needed}"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by mkhurram92 on 2011-03-20
Hi all there,

i am using DSL for internet sharing on Ubuntu.
Now i want to configure shorewall on it. My setup is as follows

1. eth0 LAN
2. eth1 DSL(Internet)

After Sharing i get another connection ppp0.
eth1 is not detecting any IP. 
Now i want to configure Zones & Interfaces in Shorewall.
But Confused what i have to configure.
ppp0 or eth1 interface i have to define for policies and rules

Pls Guide


=========================
Thanks
Jazaib Hussain

---

### Post by Cheesehead on 2011-03-20
Did you install dnsmasq? Or some other DHCP/DNS solution?

Using a Linux box as a router requires a couple elements. At minimum it requires changing the kernel forwarding flag, installing and configuring dnsmasq, reconfiguring your LAN interface from client to gateway, and editing your firewall.

I did domething similar recently - you can see my solution at [http://kiwinc.itgo.com/ian/TechBlog.html]("http://kiwinc.itgo.com/ian/TechBlog.html"), look for the entry on March 5, 2011. It's buried a few hundred lines down by now...

I didn't use shorewall, but a quick look at my favorite search engine ('router shorewall') shows a few who did, and their solutions.

---

