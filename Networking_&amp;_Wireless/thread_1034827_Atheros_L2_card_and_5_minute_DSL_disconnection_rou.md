---
title: "Atheros L2 card and 5 minute DSL disconnection routine"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by deepclutch on 2009-01-09
[SIZE=3][FONT=Tahoma]Hello Guys ,
I got a Asus P5GC-MX/1333 945GC chipset based motherboard with Atheros L2 onboard pci lan card available.Here is the detailed lspci o/p:
[/FONT][/SIZE]```
[B]02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device 8233
    Flags: bus master, fast devsel, latency 0, IRQ 2300
    Memory at ddec0000 (64-bit, non-prefetchable) [size=256K]
    Expansion ROM at ddea0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [58] Express Endpoint, MSI 00
    Kernel driver in use: atl2
    Kernel modules: atl2[/B]
```--
[SIZE=3][FONT=Tahoma]Now ,My Problem:
I got broadband type pppoe via telephone lines of dataone ISP ,India.
I usually use bridge mode(dialer from Linux) to connect.
With Atheros L2 card ,I suspect DSL Link Light disconnects and reconnects exactly at 5 minutes intervals.also ,sometimes "pppoe-discovery" command shows no core server port address(via telephone exchange port).
The telephone exchange fellows already checked for any line noise,ports problem etc and resolved a slight line noise problem.
Still ,I counted in stopwatch that *exactly* at 5 minutes DSL link in Router(GLB-802C D-link made) disconnects and reconnects.Router also checked by D-link service centre here for problems and nothing observed.
I blamed ISP for all these problems until my friend's PC was connected on my house via dataone ISP and no such 5 minutes DSL link Light down/disconnection problem observed.He got a Realtek 8369 onboard ethernet card.

Is there anything can be done to resolve my problem with atheros  L2 card?:( ,should I need to spend another 200Rupees(5$) for another cheap realtek pci card ?
Please help and Thanks.
[/FONT][/SIZE]

---

### Post by manadi on 2009-01-09
Didnt quite get your problem.......how do you suggest that L2 card is causing the connection reset?

---

### Post by deepclutch on 2009-01-09
I guess so.just bought a cheap Realtek 8139cp/too driver type pci lan card and I am NOT experiencing any disconnections!
There is some poll mechanism in the driver(I guess) which makes the 5 minute disconnection of Router/CPE's DSL Link Light(ie ,dsl connection itself!) for Atheros L2 driver.
--
So ,Please Atheros L2 users ,please verify.
1)with my laptop and this router +broadband connection ,I was not experiencing any disconnection.
2)with this Realtek card installed ,yet to see a disconnection!
Please developers for Atheros L2 ,any inputs?

---

### Post by manadi on 2009-01-09
are you dual booting between windows and ubuntu?
If so plz shutdown the system for 10-15 minutes and boot into ubuntu.
Why? I am searching for the link and post it soon.Not sure just try it.

Here it is

[http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04541.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04541.html)

maybe u can contact chris(driver developer).

---

### Post by deepclutch on 2009-01-09
^with latest modules ,that problem was solved ,I think.

---

