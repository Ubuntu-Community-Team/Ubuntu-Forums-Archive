---
title: "iptables: how to specify an alternate IP for NAT?"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by jansssens on 2010-11-20
[FONT=Courier New]Greeting, [/FONT]

[FONT=Courier New]Basically, I want to configure a linux firewall doing NAT behind a DSL modem.[/FONT]

[FONT=Courier New]**_Bridging setup:_**[/FONT]
[FONT=Courier New]-- (A).[modem] -- A.[NAT box].B -- C.[PC][/FONT]
[FONT=Courier New]A = public IP[/FONT]
[FONT=Courier New]B = 10.0.0.1[/FONT]
[FONT=Courier New]C = 10.0.0.2[/FONT]

[FONT=Courier New]See drawing above. Ideally, I would configure the modem as a bridge and the firewall as a NAT box with a public IP, which is pretty straightforward for me. Unfortunately, my modem is too braindead to support bridging and I'm stuck to it because of telephony (my ISP doesn't disclose the SIP parameters)[/FONT]

[FONT=Courier New][FONT=Courier New][FONT=Courier New]**_IP forwarding setup:_**[/FONT]
[/FONT][FONT=Courier New]-- A.[modem].B -- C.[NAT box].X -- Y.[PC][/FONT]

[FONT=Courier New]A = public IP[/FONT]
[FONT=Courier New][FONT=Courier New]B = 10.0.0.1[/FONT]
[FONT=Courier New]C = 10.0.0.2[/FONT]
[/FONT][FONT=Courier New]X = 192.168.0.1[/FONT]
[FONT=Courier New]Y = 192.168.0.2[/FONT] 
 
See drawing above. Now, my modem does support IP forwarding as next best option (they incorrectly call it DMZ host), where it forwards everything to one specific IP (C) and vice versa, at least bypassing the (buggy) port translation cruft and NAT helpers of the modem. The damn thing has memory leaks in the NAT table for example, causing crashes. 
 
Now my question is: how do I tell iptables to use C for NAT but the conntrack helpers (like conntrack_ftp) should use address A. I think this is a quite common and at least useful setup. [/FONT]

---

### Post by jansssens on 2010-12-01
*kick*
Please ask if something is unclear in my question. Is my proposed setup possible at all?

---

