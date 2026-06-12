---
title: "two desktop in a single installed ubuntu"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by ubunssk on 2011-04-23
Hi,
 Can I have two ubuntu desktop in a single installed ubuntu9.10 such that two desktop has different ipaddress?

Thanks

---

### Post by Paddy Landau on 2011-04-23
Are you telling me that you want one of the two desktops to simulate being a completely different computer on the network?

I believe this is not possible. The router assigns an IP address to the physical network controller in your computer.

Perhaps there is some clever trick you can use if you have the right router; but to the outside world, they would both have the same IP address (provided by your ISP) anyway.

---

### Post by ubunssk on 2011-04-23
okay. Thanks for your reply.

but is there a way of connecting another system through internet protocol by knowing another system ip address?
VPN would do huh?

---

### Post by Paddy Landau on 2011-04-24
Are you talking about using a proxy?

I'm no expert on Internet access, sorry, but if it's a proxy, go to System > Preferences > Network Proxy.

If it's VPN, I'm sorry I don't know.

---

### Post by ubunssk on 2011-06-30
Hey,
using virtualizers can assign two ip addres.Virtually booted os can be assigned with differnt ip address. dont know whether am i right?

---

### Post by Paddy Landau on 2011-07-01
> **ubunssk said:**
> using virtualizers can assign two ip addres.Virtually booted os can be assigned with differnt ip address. dont know whether am i right?
It depends which IP address you're referring to.

If you mean the *external* IP address that your ISP provides, then no.

But if you mean the *internal* LAN IP address that your router provides, then yes.

In Virtual Box, go to Settings > Network > Adapter 1 > Enable Network Adapter > Attached to *Bridged Adapter*. If you need to know the assigned MAC address, press Advanced.

(Please mark the thread as solved if this has answered your question.)

---

