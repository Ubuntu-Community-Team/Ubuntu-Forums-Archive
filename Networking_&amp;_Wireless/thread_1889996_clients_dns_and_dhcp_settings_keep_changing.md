---
title: "clients dns and dhcp settings keep changing"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by Dan-Eil on 2011-12-02
[SIZE=2]I have SBS 2011 running DNS and DHCP. Clients are losing DHCP settings. The DNS and DHCP Server IP's are changing after a period of time or when user reboots. I cannot figure out why they are changing and causing users to lose Internet connection. When i run an ipconfig /release then /renew... IP's change back to my assigned. [/SIZE]
[SIZE=2]I made sure i turned off DHCP on my router and my wireless AP. I have verified all my DHCP server settings (On SBS 2011). User platforms are XP and win7. [/SIZE]
[SIZE=2]Any help would be appreciated. [/SIZE]
[SIZE=2]Thanks,[/SIZE]
[SIZE=2]Dan[/SIZE]

---

### Post by poolet on 2011-12-02
try to clear the dns catch also if your usiing NAT make sure that you have check the name servers if they authenticate with your NAT..... at the end may you need a network engineer to make do a ip summarize since I think your problem is on metric the dhcp has delay with a result to disconnect and break down the connection!!!!

---

