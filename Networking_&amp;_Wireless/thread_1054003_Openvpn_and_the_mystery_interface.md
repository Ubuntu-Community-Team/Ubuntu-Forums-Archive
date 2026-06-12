---
title: "Openvpn and the mystery interface"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by iwfur25 on 2009-01-29
I've got an odd issue... it seems OpenVPN created an interface that won't go away. I know OpenVPN normally creates an interface when it is connected and removes it when disconnected. Well, it created tap0 the first time I connected. Now tap0 is always there even after a reboot, with an address and everything.

Here it is, soon after booting the system (I left out the eth and lo interfaces). OpenVPN has not been started:

tap0      Link encap:Ethernet  HWaddr b6:d7:15:64:ce:ad  
          inet addr:192.168.217.201  Bcast:192.168.217.255  Mask:255.255.255.0
          inet6 addr: fe80::b4d7:15ff:fe64:cead/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:42537 (42.5 KB)  TX bytes:468 (468.0 B)

OpenVPN still works, but now whenever I connect it creates and uses tap1. It also removes tap1 when disconnected. Notice that tap1 shows the same IP address as tap0.

tap0      Link encap:Ethernet  HWaddr b6:d7:15:64:ce:ad  
          inet addr:192.168.217.201  Bcast:192.168.217.255  Mask:255.255.255.0
          inet6 addr: fe80::b4d7:15ff:fe64:cead/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:123227 (123.2 KB)  TX bytes:468 (468.0 B)

tap1      Link encap:Ethernet  HWaddr 62:cf:0d:84:55:58  
          inet addr:192.168.217.201  Bcast:192.168.217.255  Mask:255.255.255.0
          inet6 addr: fe80::60cf:dff:fe84:5558/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:238 (238.0 B)

The IP address is a correct one, handed out by the DHCP server on my home LAN. The VPN tunnel itself also works... I am able to access the PCs at home from wherever. This tells me the VPN server and client software are both working correctly.

The only problem is a tap0 that refuses to go away. I can remove it with 'ifconfig tap0 down' but it reappears when the machine is rebooted.

Here is the client config file:

client
dev tap

proto tcp-client

remote xxxxxxxxxxxxxxxxxxxx
ca /home/chuck/openvpn-config/ca.crt

cert /home/chuck/openvpn-config/client1.crt

key /home/chuck/openvpn-config/client1.key

ns-cert-type server

tls-client

persist-key

persist-tun

keepalive 30 120

cipher AES-256-CBC

comp-lzo

If I change the above to specifically use tap0 (dev tap0) OpenVPN claims "/dev/tap0: No such file or directory".
The command 'openvpn --rmtun --dev tap0' also claims no such file or directory. I know OpenVPN created tap0 at one point, but it can't see it to remove it.

Bonus: this has happened on 2 machines. I have gopenvpn installed to provide a gui frontend for the vpn. I thought this might somehow be a problem, but the mystery tap0 shows up on every boot whether gopenvpn is started automatically or not. Besides, gopenvpn is just a gui... it does not start the vpn until I tell it to.

So, after that wall of text, does anyone have a clue as to what might be going on?

---

### Post by iwfur25 on 2009-02-02
OK, I fail. I just bothered to check all running processes... OpenVPN is right there, running and connected right after boot. I have no idea how or why it is set to start at boot, but it is. I swear it didn't do this out of the box the last time I was playing with it on Linux. I certainly didn't tell it to start at boot either.

FYI, all I did was set up Ubuntu, installed OpenVPN with the package manager, and installed gopenvpn by hand.

---

