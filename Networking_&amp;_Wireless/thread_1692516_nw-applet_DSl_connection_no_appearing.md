---
title: "nw-applet DSl connection no appearing"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by 372912 on 2011-02-21
I configure my pppoe DSL connection in Network manager applet, but I do not get an option to connect to it. It simply does not appear. It is there configured in options, but there is no way to activate it.

Wireless works fine - it connects.

But then I have to use pon dsl-provider to connect to my dsl provider(which works aftere configuring with pppoeconf). And I would like to use network manager instead. Especially since when after establishing connection with wireless, and the pon dsl provider, after I establish vpn connection to my workplace with network manager, internet simply stops working.

When I kill it afterwards with sudo pkill ppp, and restart pon dsl-provider it works again, but VPN nop. I think it would work if I could also establish pppoe connection with network manager. But I cannot.

Thank you for your help.

---

