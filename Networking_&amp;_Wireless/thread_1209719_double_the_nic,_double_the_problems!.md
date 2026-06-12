---
title: "double the nic, double the problems!"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by stuckdoingwork on 2009-07-10
Let me introduce you to a problem which has been driving me crazy for the past few months.  

I have two computers with three ethernet connections, two subnets, and two wall ports between them.

My university runs VLANS based on *static* ip's tied to the MAC address.  My desktop (running Jaunty) has a built-in ethernet card on the public vlan (eth0 on 18.93.*.*/255.255.0.0) and an add-on card on the private VLAN (18.4.16.*/255.255.255.0).  My laptop is also on the private vlan.  Needless to say, I need to access other computers on both vlan, and in particular I need access to my desktop from home, which is only available on the public vlan (and the vpn service, unfortunately, is on a completely separate network!).

Because I only have two wall ports, I plug the public vlan into one and have a Linksys switch (not a router) which hosts both my private desktop card and my laptop.  My university officially does not support the use of switches or routers, and if I plug the public card and either the private card or my laptop in, only one vlan will work at a time.  This makes sense to me as I believe my university either detects traffic to multiple vlans routed through the same physical plug and blocks one, or perhaps there's something in their gateways/switches that can't work like this anyways.

If I simply use NetworkManager to manage both cards on my desktop, it gets confused and only one seems to be active at once (ie I will only be able to ping computers on one subnet).  I believe this is due to multiple 0.0.0.0 routes that get added to the routing table.

If I disable NetworkManager and configure the cards manually, everything works - sort of.  For reference, here is my /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 18.93.my.ip
netmask 255.0.0.0
gateway 18.41.0.1
up route del default
up route add default gw 18.41.0.1 eth0
down route del default gw 18.41.0.1 eth0
dns-nameserver 18.70.0.160 18.71.0.151

auto eth1
iface eth1 inet static
address 18.4.16.ip
netmask 255.255.255.0
gateway 18.4.16.1
dns-nameserver 18.70.0.160 18.71.0.151

auto eth1:0
iface eth1:0 inet static
name Ethernet alias LAN card
address 192.168.0.4
netmask 255.255.255.0
gateway 0.0.0.0

I set up my routing tables as above to make all traffic except that on my private subnet run through the builtin card on my public lan (I don't fully understand the vlan setup here, as the private network does have access to the internet and some other computers on my network, but cannot be pinged/sshed etc from outside).

I also added the alias to my private card in hopes that everything from my laptop which targets it directly will go through my switch, but not all the way through the gateway, in hopes that this will 1) improve latency and 2) prevent my gateway/university from knowing about the switch and possibly blocking one of the IP addresses, which has been my suspicion, because:

Everything on the public lan works fine.  But, during periods of high transfer between my laptop and desktop (particularly when I run Unison and Synergy, both over ssh - I haven't tried anything similar with other protocols), my desktop will stop responding on the private lan.  It will no longer be able to ping the gateway, nor can either computer ping the other, even on the local address.  I don't believe my laptop ever loses it's connection to the gateway.  I sometimes can bring it back up right away with /etc/init.d/networking restart or /etc/init.d/networking force-reload, but often I have to wait several minutes before this works, if not restart the computer.  When I'm transferring several hundreds of megabytes continuously, I will get approximately 30 seconds of up time before the session terminates, making file transfers extremely painful.

I have no issues running the same transfers over the public vlan when my laptop is at home (though obviously it's slower!).  I also have no problems when I directly plug my laptop into the private card on my desktop, so I doubt it's a card issue.  I haven't tried unplugging the public connection on my desktop and having both computers directly plugged into the wall in awhile, because I need both connections, but I don't recall having the same issues.

So:  any ideas what my problem could be?  Is there a chance this is caused by a faulty switch, or is it more likely that the gateway itself is terminating my access?  Are there any fancy tricks like bridging my two desktop cards that might resolve this (keep in mind all MAC addresses have to be linked to their assigned static IPs)?  

One potentially complicating fact that I do not understand is the subnet on my public card.  My help desk says it should be 255.255.0.0, but as above, I have it set to 255.0.0.0 - it does not connect at all with the settings they told me to use.  I believe this is because I have moved the computer from the office it was originally assigned to and I believe it is now connected to a physically different set of switches and cannot contact it's gateway via the assigned subnet.  However, I don't really understand how this works.

Thanks, hopefully some gurus here will be able to shed some light!

-Scott

---

