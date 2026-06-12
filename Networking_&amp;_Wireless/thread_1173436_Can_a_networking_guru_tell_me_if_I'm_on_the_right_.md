---
title: "Can a networking guru tell me if I'm on the right track here?"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2009-05-29
Here is my problem.  I use a voip service (Voipo) which requires that I use a Linksys Pap2 device (they provide).  Unfortunately, the service seems to have issues with the Tomato firmware that i have on my router.  My network currently looks something like:


```
DSL Modem >> Wireless Router1 (Tomato) >> (Pap2 + PC + Printer)
                    |
                    |Wireless connection
                    |
             Wireless router2 >> HTPC/file server
```

So Wireless Router1 is the main router that handles DHCP and everything, while the second router is simply bridged to extend the network to the living room (and is largely irrelevant to this question).

The Voip service via the Linksys Pap2 often had issues provisioning because of an incompatibility with the Tomato firmware.  This is documented in the Voipo forums, but no solution has yet been found. 

My plan is to add an ethernet switch between the DSL modem and Router1 and attach the Pap 2 to it as below.

```
 DSL Modem >> Switch  >> Pap2
                     |>> Wireless Router1 (Tomato) >> (PC + Printer)
                            |
                            |Wireless connection
                            |
                      Wireless router2 >> HTPC/file server
```

Should that address the problem, by allowing the Pap2 to bypass the router?  Would that setup cause any security issues that I should be aware of?  

Thanks

JTS

---

### Post by superprash2003 on 2009-05-30
are you connecting a cable from the DSL modem to the LAN port of the router 1 or WAN port?? is the router 1 configured to pppoe mode?? or the DSL modem?

---

### Post by madverb on 2009-05-30
Does the modem have an IP address or is it just a bridge? You will need to be able to use the internal IP of the modem as the gateway for the Pap2. Otherwise you will still have yo use the Router's internal IP as the gateway and that defeats the purpose.

---

### Post by jimmy the saint on 2009-05-30
The router is connected to the WAN port on the router.  I don't didn't have to configure anything in any router I have used with the router, so I think it takes place in the modem.  The modem doesn't show up on my LAN though so it doesn't have an intrenal ip that I know of.  I didn't think about that.  

Would there be a way to (with the the switch or with something else) to have the pap2 access the dsl modem directly rather than going through the router?

---

### Post by madverb on 2009-05-30
What is the WAN IP of the router? If it is a private IP like 192.168.*.* or 10.*.*.* the modem will have an internal IP.

---

### Post by superprash2003 on 2009-05-31
in that case , the setup you mentioned will not work.. as your router is doing the authenticating part with your ISP ,so anything behind the router will not have internet access.
  Although you could make a modification. use your DSL modem to connect to the internet.. and setup DHCP server on that.. and let router 1 and router 2 behave like hubs.. then connect voip directly to the switch ( which is connected to dsl modem ) .DISABLE DHCP on router1 and router 2

---

