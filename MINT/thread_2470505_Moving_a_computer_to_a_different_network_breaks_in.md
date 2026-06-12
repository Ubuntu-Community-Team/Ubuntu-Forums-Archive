---
title: "Moving a computer to a different network breaks internet access"
date: 2022-01-01
forum: MINT
---

### Post by kevinthedrummer2 on 2022-01-01
When I move my computer from one network to another, then it can no longer reach the internet, neither numerically, nor by hostname. The computer can't even reach its own gateway IP address.

I'm trying to move from DSL to cable-modem. I have both networks in the home. Neither touch each other except for at the power outlet.

I start with a computer running Linux Mint 19.3 using DSL and on network 192.168.1.0/255.255.255.0 with IP address 192.168.1.12 and DNS hosts 205.171.3.65 & 205.171.2.65 with 8.8.8.8 and 8.8.4.4 added for good measure. Everything works in this configuration.

When I move the Ethernet cable of that computer to a router on the cable-modem network I have it retaining almost all of its network configuration, except that DNS host IP addresses 205.171.[23].65 are replaced by 75.75.75.75 & 75.75.76.76. In this configuration the computer can ping another computer with IP address 192.168.1.11. But, the computer can't even ping its own gateway: 192.168.1.1.

When I move the computer's Ethernet cable back to the DSL router, then all works again.

Before you suspect that the cable-modem network is all messed up let me describe what works. I have another computer, this one running Linux Mint 20.2, that's on the cable-modem network and everything works related to networking. I can ping the gateway. I can ping a host "in the wild" using it's IP address, and I can ping hosts using their network names, e.g. google.com. I can browse and SSH. This computer's network configuration is 192.168.1.0/255.255.255.0 with IP address 192.168.1.11 and DNS hosts 75.75.75.75 & 75.75.76.76 again with 8.8.8.8 and 8.8.4.4.

At this point one might think that there's something wrong with the computer I'm trying to move from DSL to cable-modem. I also have smart TVs on the DSL network, and moving a smart TV's Ethernet cable to the cable-modem network disables network connectivity for the smart TV. The error message there is that the TV can't get an IP address, which is being attempted via DHCP.

If it matters, the router for the DSL network is an Actiontec C1000A, and the router for the cable-modem network is a TP-Link Archer A6.

One person suggested that some part of the network equipment is mapping a router and/or network card MAC address to an IP address. Their suggestion was to power off all the equipment, wait, move the Ethernet cable, and power things on again. This did NOT work.

Thanks for any help at all.

---

### Post by howefield on 2022-01-01
Thread moved to the "*Mint*" forum.

---

### Post by kevinthedrummer2 on 2022-01-02
[COLOR=#232629][FONT=-apple-system]I fixed, or maybe worked around the problem. Anyway, the network in my home is working again. To accomplish this I replaced the TP-Link Archer A6 with a Netgear AC1750 WiFi router.

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]I don't know whether the TP-Link unit was broken or incapable. All I know is that I and that unit couldn't come up with a working network. I will say though, I've used it as an access point before, and that worked great. Yes, I remembered to change it back to router mode.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The Netgear router, its Nighthawk app, and I got along splendidly. It took me 1-1.5 hours working with 14 devices, comprising wired & WiFi, used by 4 people, ranging from wireless, entertainment devices, and servers, to get all that set up and tested. Everything works within the home.

[/FONT][/COLOR]

---

