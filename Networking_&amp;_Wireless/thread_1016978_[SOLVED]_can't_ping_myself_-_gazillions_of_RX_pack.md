---
title: "[SOLVED] can't ping myself - gazillions of RX packets dropped"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by el_baby on 2008-12-20
Hi,

I have a really weird problem.

I set up a minimal intrepid server.

I did all the setup in my internal network with a fixed IP (192.168.83.7).

After setting it up, updating it and installing and configuring a [shoreline firewall]("http://www.shorewall.net"), I decided to move it to the outside network.

I stopped networking, modified /etc/network/interfaces, chose an unused public IP, and started networking again... but **nothing** works... not even pinging myself.

I even completely disabled the firewall to no avail.

Note that the same setup (with ANOTHER static IP) work perfectly.

The only thing I can see is that I see lots of dropped RX packets using ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:22:15:3f:f1:53  
          inet addr:200.69.209.60  Bcast:200.69.209.63  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1106 errors:0 dropped:3958411264 overruns:0 frame:0
          TX packets:697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142231 (142.2 KB)  TX bytes:67794 (67.7 KB)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6288 (6.2 KB)  TX bytes:6288 (6.2 KB)

```

But I also see these in the internal network... the other difference is that the internal network is 100BaseT FD switched and the external one is 10BaseT HD non-switched... I tried 2 different (old) hubs with the same result (I don't have another switch to test).

FWIW, the /etc/network/intefaces file for the internal network is
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
	address 192.168.83.7
	netmask 255.255.255.0
	gateway 192.168.83.254

```

and the one for the external network is
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
	address 200.69.209.60
	netmask 255.255.255.248
	gateway 200.69.209.62
	#network 200.69.209.56
	#broadcast 200.69.209.63
	#name Ethernet LAN card 0

```

I have a hardy server with the next address running beside this one without a single problem...

Any hints? I'm desperate!

---

### Post by jowilkin on 2008-12-20
Sounds like a firewall problem to me, I had similar problems and found a script that clears the iptables rules and it fixed my errors

> #!/bin/sh
# ung ung ung ung ung ung ung ung
# This program might significantly decrease your networksecurity
# Dieses Programm kann Ihre Netzwerksicherheit signifikant herabsetzen.
#
# zum NATten sind folgende Optionen zu überdenken:
# iptables -t nat -A POSTROUTING  -o ppp0 -s 192.168.156.0/24 -d 0/0 -j MASQUERADE

PATH=/sbin:/usr/sbin
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F
iptables -X
iptables -L


---

### Post by el_baby on 2008-12-20
No, it's not a firewall problem... I unplugged the uplink to internet and completely turned off the firewall and I still couldn't ping myself :-(

Thanx anyway.

---

### Post by el_baby on 2008-12-22
OK... it was a classical **[font=courier]USER=id10t[/font]** error...

I've been pinging 200.***68***.209.60 instead of 200.***69***.209.60 the whole time!!!!

Sorry about the wasted bw...

---

