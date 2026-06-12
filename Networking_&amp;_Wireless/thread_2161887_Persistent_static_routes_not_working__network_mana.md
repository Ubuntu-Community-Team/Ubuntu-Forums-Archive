---
title: "Persistent static routes not working / network manager not working"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by Seventh7 on 2013-07-12
Hi all,

I have three 12.04 virtual machines, and I'm having the same issue with all of them. They are brand new base installs with nothing on them other than vmware tools. I have two problems that I'm hoping someone can shed some light on.

The first is that I cannot edit network connections using the GUI, nor does the network come up at all, unless I run a 'service network-manager restart' from the console. Once I restart it, I can edit connections normally. Without running that command, if I bring up the network connections editor in system settings, I can see both network cards but every option is greyed out and I cannot edit it.

The second problem is that I can't seem to get persistent static routes to survive a reboot. In /etc/network/interfaces I have the following (without my actual net IP addresses):

[B][I]auto lo
iface lo inet loopback

up route add -net 1.2.3.4 net mask 255.255.255.0 gw 2.3.4.5 dev eth1[/I][/B]

After some RTFM and Google, I believe that's the right way to add a persistent route, however it's not reappearing on reboot, and a route-n shows my destination route for the 1.2.3.4 network to be just 0.0.0.0. If I run that last command alone from a terminal, eg:

[B][I]route add -net 1.2.3.4 net mask 255.255.255.0 gw 2.3.4.5 dev eth1
[/I][/B]
The route appears in the routing table and my network works the way it should. Since both of my problems have to do with the network, I can only assume that the problem is related, but I honestly have no idea what the problem could be. Any insight would really be appreciated. Thanks!

---

### Post by praseodym on 2013-07-13
Hi,

change "managed=false" to "managed=true" in the file /etc/NetworkManager/NetworkManager.conf, otherwise the networkmanager can not handle the manual config in the "interfaces"

---

### Post by Seventh7 on 2013-07-15
Thanks for the reply! :)

I made the change to NetworkManager.conf and rebooted, and now I can actually edit the NICs in the GUI (huzzah!). The route that I'm trying to add at startup isn't staying persistent however. My /etc/network/interfaces looks like so (minus the eth0 config):

[I]# Interface eth1
iface eth1 inet static
address 192.168.1.33
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
up route add -net 172.16.10.0 mask 255.255.255.0 gw 192.168.1.254 dev eth1
[/I]
It's that last route that I'm trying to add, so that my default route to the 172.16.x.x network is via .254 eth1's primary network, via eth1. After a reboot, a 'route -n' doesn't show it, and I get a destination net unreachable of I try to ping some_address on 172.16..x.x. If I add the route manually, it works just fine. 

Thanks again for the help!

---

### Post by praseodym on 2013-07-15
Did you add "auto eth1" in the file at the end?

---

### Post by Seventh7 on 2013-07-15
I've tried adding that right after the #description, and at the very end of the file, but no luck. I'm sure I'm just missing something painfully obvious but I can't quite figure out what it is.

Edit: I stand corrected - adding it to the end worked, I apparently just had to spell it correctly (*whistle*). Thank you very much, that was it! :)

Much appreciated!

---

