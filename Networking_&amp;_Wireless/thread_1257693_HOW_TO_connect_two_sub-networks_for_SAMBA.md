---
title: "HOW_TO_connect two sub-networks for SAMBA?"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by demontager on 2009-09-04
[FONT=Arial]I need connect two subnetworks together in way that I can connect from Ubuntu to Windows and vice versa, main reason is files sharing, so I need SAMBA protocol[/FONT]
  [FONT=Arial] Configs[/FONT]
  [FONT=Arial]Ubuntu[/FONT]
  [FONT=&quot]IP 192.168.0.23[/FONT]
  [FONT=&quot]msk 255.255.255.0[/FONT]
  [FONT=&quot]gw 192.168.0.20 ([/FONT][FONT=Arial]router[/FONT][FONT=&quot], [/FONT][FONT=Arial]connected[/FONT][FONT=Arial]to[/FONT][FONT=&quot] 192.168.1.0 [/FONT][FONT=Arial]via[/FONT][FONT=&quot] WAN [/FONT][FONT=Arial]port[/FONT][FONT=&quot])[/FONT]
  
  [FONT=&quot]Windows[/FONT]
  
  [FONT=&quot]IP 192.168.1.26[/FONT]
  [FONT=&quot]msk 255.255.255.0[/FONT]
  [FONT=&quot]gw 192.168.1.1([/FONT][FONT=Arial]router-Internet gateway[/FONT][FONT=&quot])[/FONT]
  
  [FONT=Arial]And router configs, which connects two networks[/FONT][FONT=&quot] 192.168.0.0 [/FONT][FONT=Arial]with[/FONT][FONT=&quot] 192.168.1.0:[/FONT]
  [FONT=&quot]WAN:[/FONT]
  [FONT=&quot]IP 192.168.1.20[/FONT]
  [FONT=&quot]msk 255.255.255.0[/FONT]
  [FONT=&quot]gw 192.168.1.1[/FONT]
  [FONT=&quot]LAN:[/FONT]
  [FONT=&quot]192.168.0.20[/FONT]
  [FONT=&quot]msk 255.255.255.0[/FONT]
  
  [FONT=&quot]PS [/FONT][FONT=Arial]Ping [/FONT][FONT=Arial]from[/FONT][FONT=&quot] Windows [/FONT][FONT=Arial]to[/FONT][FONT=&quot] 192.168.0.23 [/FONT][FONT=Arial]doesn't pass[/FONT][FONT=&quot],[/FONT]
  [FONT=Arial]from[/FONT][FONT=&quot] Ubuntu [/FONT][FONT=Arial]to[/FONT][FONT=&quot] 192.168.1.26 [/FONT][FONT=Arial]does[/FONT][FONT=&quot], [/FONT][FONT=Arial]but can't see Windows shared folders.[/FONT]
  [FONT=Arial]PPS On router which connects two networks I made[/FONT][FONT=&quot] port forwarding and I can connect to Ubuntu shares,[/FONT]
  [FONT=&quot]but I need to enter router&#8217;s IP(192.168.0.20) not 192.168.0.23[/FONT]
  
  [FONT=&quot]ID Port           IP Address [/FONT]
  [FONT=&quot]3    137-139                             192.168.0.23 [/FONT]
  [FONT=&quot]4          445                                             192.168.0.23 
[/FONT]

---

### Post by fwre01 on 2009-09-04
Is there a reason you're using NAT on 192.168.0.20? If you can disable NAT (or technically its PAT) on 192.168.0.20 then you wouldnt need any port forwarding rules.

---

### Post by demontager on 2009-09-04
The reason is- I want to hide 192.168.0.0 network from unauthorized views, so I need split forwarding rules for SAMBA. Theoretical as understand I need change default SAMBA ports, 135-137, 445. And assign its as SAMBA for other IP. Is it possible on Ubuntu?

And if yes how can I connect to Ubuntu SAMBA in Windows explorer than? \\192.168.1.20:333 ?

P.S. 333-port just for example

---

