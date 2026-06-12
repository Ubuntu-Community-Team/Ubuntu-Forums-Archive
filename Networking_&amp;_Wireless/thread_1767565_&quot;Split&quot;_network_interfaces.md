---
title: "&quot;Split&quot; network interfaces?"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by Wolf9466 on 2011-05-25
Can you "split" a network interface in Ubuntu, similar to how airmon-ng lets you use your wireless card in managed and monitor mode, by making another interface out of the same hardware? I know it'd be slower, but I'd still like to do it.

---

### Post by Wolf9466 on 2011-05-26
Bump.

---

### Post by SeijiSensei on 2011-05-26
I don't really understand what you're looking to do, but Linux supports virtualizing interfaces by simply adding ":[0123...]" to the end of the designation.  For instance, if you have a wired connection on eth0, you can designate an eth0:0 (or eth0:1, eth0:2, etc.) and use ifconfig to assign it a separate address.  Usually this address has to be in the same subnet as the physical adapter, but if you have good routing skills you can probably make it talk to a different default gateway on a different subnet.  

I doubt that you can kick the virtual adapter into promiscuous mode while leaving the physical adapter alone if that's what you're trying to do, though.

Virtualized interfaces are no slower than their physical cousins.

---

### Post by Wolf9466 on 2011-05-26
> **SeijiSensei said:**
> I don't really understand what you're looking to do, but Linux supports virtualizing interfaces by simply adding ":[0123...]" to the end of the designation.  For instance, if you have a wired connection on eth0, you can designate an eth0:0 (or eth0:1, eth0:2, etc.) and use ifconfig to assign it a separate address.  Usually this address has to be in the same subnet as the physical adapter, but if you have good routing skills you can probably make it talk to a different default gateway on a different subnet.  

I doubt that you can kick the virtual adapter into promiscuous mode while leaving the physical adapter alone if that's what you're trying to do, though.

Virtualized interfaces are no slower than their physical cousins.

That's exactly what I want to do, how exactly do I do it? And I'd figure if I'm using both at the same time, it'd be a bit slower.

---

### Post by SeijiSensei on 2011-05-27
Just use ifconfig to attach an address to a virtual interface like eth0:0.  I suspect you can add a stanza to /etc/sysconfig/interfaces, though I've only ever created virtual interfaces using ifconfig.  I usually just put the command in /etc/rc.local like this:

```
/sbin/ifconfig eth0:0 10.1.1.1 netmask 255.255.255.0 broadcast 255.255.255.0
```

The address, mask, and broadcast address will obviously depend on the network to which the virtual interface is expected to connnect.

As for speed, any modern computer has a CPU that can run rings around network speeds, so processing packets is a very low-load activity.

---

