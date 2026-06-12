---
title: "vpn"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by causeitsme on 2010-01-09
I'm totally lost here. 

I have an Ubuntu box at home running 9.10 32bit and a laptop running 9.10 64bit. The setup I have is -- DSL modem ---> Belkin router ----> ethernet to Desktop box and wireless to laptop.

 I want to be able to connect to the box at home with the laptop from whereever I am.

I've installed all of these on both computers. 

the PPTP plugin, network-manager-pptp (SPM).
the Cisco VPNC plugin, network-manager-vpnc (SPM).
the OpenVPN plugin, network-manager-openvpn (SPM).


This is ifconfig from the box at home:

eth0 * * *Link encap:Ethernet *HWaddr 00:18:f3:4c:8e:62 *
** * * * *inet addr:192.168.2.2 *Bcast:192.168.2.255 *Mask:255.255.255.0
** * * * *inet6 addr: fe80::218:f3ff:fe4c:8e62/64 Scope:Link
** * * * *UP BROADCAST RUNNING MULTICAST *MTU:1500 *Metric:1
** * * * *RX packets:2388 errors:0 dropped:0 overruns:0 frame:0
** * * * *TX packets:2588 errors:0 dropped:0 overruns:0 carrier:0
** * * * *collisions:0 txqueuelen:1000*
** * * * *RX bytes:1582786 (1.5 MB) *TX bytes:425344 (425.3 KB)
** * * * *Interrupt:23 Base address:0xc000*

lo * * * *Link encap:Local Loopback *
** * * * *inet addr:127.0.0.1 *Mask:255.0.0.0
** * * * *inet6 addr: ::1/128 Scope:Host
** * * * *UP LOOPBACK RUNNING *MTU:16436 *Metric:1
** * * * *RX packets:82 errors:0 dropped:0 overruns:0 frame:0
** * * * *TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
** * * * *collisions:0 txqueuelen:0*
** * * * *RX bytes:9358 (9.3 KB) *TX bytes:9358 (9.3 KB)


I can connect to the desktop box when I'm at home with the laptop by using Remote Desktop by clicking the link to 192.168.2.2 (or, as it's called in my Places - Kim's computer) and then entering the password.

However 192.168.2.2 is the ip the wireless router gives to the desktop box... I think.

When I try and add a vpn connection under Network Icon>Configure VPN I don't know what to do, I've tried researching this and nowhere can I find info on what to enter. 

First, I don't know which option to choose:

*Cisco Compatible VPN (vpnc)
*OpenVPN
*Point-to-Point Tunneling Protocol PPTP

Second, when I do chose either of those, the first box to enter data in is Gateway. But, that doesn't seem to me to be enough. I thought the gateway would be the router and then I'd need to enter the local ip of the machine I'm trying to connect to.

Can someone tell me what I'm missing here?

---

