---
title: "No wired (eth0) under networking manager applet (10.04)"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by QwertyTSecond on 2012-03-28
I use an ethernet cable whilst in accommodation, which works fine most of the time.
However, having come back to my parent's for easter, I find that I have no connection options under the network manager applet. Slightly confusing, as I haven't changed anything, either hardware or software. Ethernet is an integrated port on my motherboard (MSI P67A GD53 B3).

lspci
06:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI express Gigabit Ethernet Controller (rev06)

sudo dhclient

Sistening on LPF/eth0/8c:89:a5:32:7b:02
Sending on LPF/eth0/8c:89:a5:32:7b:02
Sending Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received
No working leases in persistent database - sleeping

As a final note, auto eth0 in network settings is set to automatic DHCP.

Many thanks in advance.

---

### Post by praseodym on 2012-03-28
If you change the router, remove any connections in "wired" and "DSL", and reboot.

---

### Post by QwertyTSecond on 2012-03-28
Okay, tried it, but same results. It doesn't generate any new connections either.
No connections appear under the network manager applet if I make them.
I also tried adding a static IP connection in etc/network/interfaces. This had the effect of making the network applet vanish.
Having restored the original etc/network/interfaces file, the only line is a loopback setting, shouldn't there be a static/dhcp setting as well?

---

### Post by Iowan on 2012-03-28
> **QwertyTSecond said:**
> 
Having restored the original etc/network/interfaces file, the only line is a loopback setting, shouldn't there be a static/dhcp setting as well?That sounds like my */etc/network/interfaces* file... Network Manager maintains it's own details (don't remember where, at the moment).

**ifconfig -a** should show details for interfaces - active or not... but I suspect it'll just show no IP address for eth0

---

### Post by QwertyTSecond on 2012-03-29
ifconfig -a  shows lo and eth0
lo appears fine, but you're right about eth0; no IP address, although the MAC address is there.
Is there any way to check if my ethernet port is functional, make sure it didn't burn out or suffer some other mishap? It's really odd it works fine on one router but not the other.
It might be worth noting that I was at my parent's over Christmas, and it worked then without a hitch.

Also, after you mentioned network manager, I browsed to /etc/NetworkManager/system-connections and found a file called auto eth0. Ubuntu doesn't recognise it's file type, and I can't open it with any text editor, it instead tells me I don't have the necessary permissions. Chmod doesn't change this.

---

### Post by QwertyTSecond on 2012-04-01
Okay, never mind, I was just being phenomenally retarded. I continuity checked the ethernet cable and one wire's broken in it. Replacing it with the one from my other computer solved the problem. Now I get to buy another one, oh joy...

---

