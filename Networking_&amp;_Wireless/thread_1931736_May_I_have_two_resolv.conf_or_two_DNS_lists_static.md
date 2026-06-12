---
title: "May I have two resolv.conf or two DNS lists: static master and dhcp slave?"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by Artif on 2012-02-26
1) I do not have Network Manager at all. It was purged.
2) I have DHCP connection to Internet.
3) I need to organize my own DNS's address list in such a way that: primary and first address is static and my own, others are secondary and obtained via DHCP.

I want to use DNS+DHCP feature of KVM infrastructure ( [https://help.ubuntu.com/community/KVM/Networking#DNS_and_DHCP_Guests](https://help.ubuntu.com/community/KVM/Networking#DNS_and_DHCP_Guests) ) for name resolution of my virtual machines. It is possible if the first nameserver address in resolv.conf is address of host's libvirt interface. Dnsmasq - a part of out of the box KVM's infrastructure - will take care about all the other.

But my KVM host have DHCP configuration for external interface, which all ways overwrites &quot;resolv.conf&quot;. I do not want to change DHCP to static and do not want to use fully static DNS list.

Is there a way (may be any workaround) to create a cascade of DNS addresses lists? Smth. like primary static resolv.conf and secondary one obtained via DHCP?

---

### Post by Vishal Agarwal on 2012-02-26
Before searching the resolve.conf, the O/S always search the hosts first. you can put your own DNS list into the hosts file.
May be it can work for you !

---

### Post by Artif on 2012-02-26
> **Vishal Agarwal said:**
> you can put your own DNS list into the hosts file.

IP adresses of virtual machines are changing in my case.

As far as I know I can not put into &quot;/etc/hosts&quot; addresses of DN servers to be used for name resolution. The file can be filled only with static pairs of host/domain names and it's IP address.

---

