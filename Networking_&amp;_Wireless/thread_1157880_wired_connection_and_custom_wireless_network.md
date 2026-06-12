---
title: "wired connection and custom wireless network"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by thmonkey on 2009-05-13
Hello everyone,

i am trying to create a manual wireless network from my laptop's wireless interface, while my laptop is connected to a router through ethernet. The only way i got both interfaces to connect simultaneously was when i disabled the roaming mode of the wireless connection, and set up some settings myself, while providing no gateway for the wireless. however, that did not create a new wireless network.

is there any way to do that?

thanks in advance for your time!

---

### Post by Peter09 on 2009-05-13
I think you need to setup you wireless interface as ad-hoc with a static address with an IP schema different to your router.

---

### Post by thmonkey on 2009-05-13
> **Peter09 said:**
> I think you need to setup you wireless interface as ad-hoc with a static address with an IP schema different to your router.

thanks for your quick reply!

the steps i followed are the following:

1. configured the wireless interface to get static ip:

in file /etc/network/interfaces i added ,

```
iface {interface} inet static
wireless-essid {desired-essid}
address {static-ip}
netmask {mask}
gateway {gateway-ip}
auto {interface}
```

2. configured the wireless interface to operate in adhoc mode:

```
sudo ifdown {interface}
sudo iwconfig {interface} mode ad-hoc
sudo ifup {interface}
```

---

### Post by superprash2003 on 2009-05-13
so did it work?

---

### Post by thmonkey on 2009-05-13
> **superprash2003 said:**
> so did it work?

yeah you're right, forgot to mention it :roll:

worked like a charm ;)

---

