---
title: "resolvconf, network-manager et al."
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by Kleenux on 2012-08-17
Installed a brand new fresh 12.04 and network-manager is still cumbersome (and maybe still broken).

So as usual, I removed it ):P

Working with /etc/network/interfaces is reliable and not that inconvenient (works all the time).

Now, resolvconf ( 8 ) just overwrote my /etc/resolv.conf settings.
Well, it said it will, so I cannot really blame it.

But, come one, why the Ubuntu folks have to add a layer above /etc/resolv.conf? It was not simple enough?

Anyway, resolvconf is, also, removed.

Any comment / opinion?

---

### Post by chili555 on 2012-08-17
> But, come one, why the Ubuntu folks have to add a layer above /etc/resolv.conf? It was not simple enough?It was indeed simple enough and often slow. For the everyday user, Network Manager and the new method involving dnsmasq are good.

You can make your DNS settings persistent with a new line in /etc/network/interfaces like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="Red"]dns-nameservers 8.8.8.8 192.168.1.1[/COLOR]

```You can fine-tune the DNS nameservers you use with namebench, found in the Ubuntu repositories.

---

### Post by Kleenux on 2012-08-17
dns-nameservers in /etc/network/interfaces is actually what I've been using (after resolvconf was gone). 

This is good as it helps having the network configuration grouped together in one place.

---

### Post by jdthood on 2012-10-30
> **Kleenux said:**
> dns-nameservers in /etc/network/interfaces is actually what I've been using (after resolvconf was gone). 

This is good as it helps having the network configuration grouped together in one place.

Without the resolvconf package, "dns-nameservers" options in /etc/network/interfaces have no effect. It is resolvconf that implements the dns-* options. So if you want to use those options, you had better re-install resolvconf.

---

