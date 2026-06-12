---
title: "Setup Ubuntu machine as Wirless Bridge"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by Morphine. on 2011-09-09
So I've been using a router (DD WRT) to bridge a couple of computers (all connected to the bridge by Ethernet) wireless to my main router.
That had been working a dream until the router burnt out, and wireless has become extremely slow. 

So i had an idea, one of the computers connected to that bridge (Macbook running Ubuntu) has a wireless NIC that i don't use.

So basically i thought i would be able to use that wireless NIC to forward the wireless connection to this group of computers (original wireless bridge would just act as switch)

Now I've been reading up on a couple of methods, none of which have worked for me. 
What is the best way to go about doing this?

*I understand that the wireless hardware on macbook's are quite limited in their uses on linux due to driver restrictions, but i can definitely connect to my router though it.*

-Thanks

---

### Post by HermanAB on 2011-09-09
Howdy,

Not all WiFi adaptors can work as access points.

---

### Post by Morphine. on 2011-09-09
Yeah i see that my particular adapter cannot work in Master mode.

However in this instance i do not want the adapter to behave as an access point.
I want it to connect directly to my main router.
And some how directly forward that connection to the Ethernet port.

---

### Post by Morphine. on 2011-09-10
I found out how to bridge interfaces though /etc/network/interfaces
but it's still not quite working the way i would like.

**/etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid [SSID]
wpa-proto RSN 
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk    [Password]

auto br0
iface br0 inet static
address 192.168.0.250
netmask 255.255.255.0
network 192.168.0.
gateway 192.168.0.1
bridge_ports eth1 eth0

auto eth0
iface eth0 inet static
address 192.168.0.251
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.1

```The wireless connects and is accessible on the network as 192.168.0.250
However no DHCP is forwarded to Eth0.
If i directly connect another computer to the Ethernet port and i manually give it an IP, it cannot ping my main router (192.168.0.1)

All the things I've read deal with broadcasting network signals from Ethernet over wireless.. since i want to do the opposite I'm having trouble getting the config correct.

Any ideas?

---

