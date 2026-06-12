---
title: "Internet stops when LAN switch is switched ON"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by aarav2306 on 2010-07-29
hi 
My PC is connected to an modem (DHCP) with IP 192.168.1.21 on eth0
Internet works perfectly
I have installed an additional LAN card and configured it as eth1 with IP of 192.168.0.1
When I connect this LAN card to a LAN switch which in turn is connected to 6 other PCs, the internet stops working.
As soon as I switch OFF the LAN switch, I am able to access internet.
The IP addresses of the other PCs are configured as 192.168.0.2 etc. with gateway as 192.168.0.1 and DNS same as the DNS on the external interface.
I can ping 192.168.0.1 from the LAN but neither LAN nor the main PC can access net.
I was planning to Masquerade and NAT the other computers without using squid

My setup is as follows
ISP - Modem(192.168.1.1) - Ubuntu desktop 9.04(external interface eth0  192.168.1.21 & internal interface eth1 192.168.0.1) - switch - LAN  (comprising of Ubtuntu 9.04, 9.10, 10.4 & XP machines with IP  192.168.0.2 - 8 and gateway of 192.168.0.1) 
I did NAT as per [https://help.ubuntu.com/community/In...nectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")
This worked perfectly well 1 day
Next day onwards whenever the LAN switch is "ON" the main Ubuntu wudnt  get internet and the internet connection would work only when the LAN  switch is turned "OFF". Even if all the PCs in LAN were to be switched  off, the main Ubuntu would behave similarly i.e. internet would work  only when switch isn't connected to it or switched off.

Regards
Aarav

---

### Post by Ocxic on 2010-07-29
your routing tables is getting changed, so that your default gateway is being set incorrectly.(i think)

post the output of "sudo route" after you connect that other card, and your net connection dies.

---

### Post by aarav2306 on 2010-07-30
Hi
The output for sudo route after I switch "ON" the LAN switch is
Kernel IP routing table
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth2
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         aarav-desktop. 0.0.0.0         UG    0      0        0 eth0
regards
Aarav

---

### Post by Iowan on 2010-07-30
Either there's a typo somewhere, or what you *think* is eth1 is showing up as eth2. Dunno if this messes up your NAT configuration...

---

