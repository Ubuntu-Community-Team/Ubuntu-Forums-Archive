---
title: "atl1 dropping packets"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by trevelyon on 2009-05-18
Hello,

I have a server that has an atl1 gigabit adapter and I am having a problem with packets seemingly being dropped when they are above a specific MTU. Nothing is noted in the syslog or dmesg when the packets are dropped and the output of ip -s link shows no errors or dropped packets.  I sniffed the saga port using wireshark and can see the packets received at the interface.  The packets with 1490 or smaller size show up in tcpdump but the ones with 1491 + size do not.

Problem description:
traceroute -nUp 6000 saga 1490 - works
traceroute -nUp 6000 saga 1491 - doesn't work (no packets show up in tcpdump and no response sent back from saga at all)

Here is the relevant system information:
OS: Ubuntu Intrepid 8.10 x86_64 (I do not want to upgrade to Jaunty as an unsolved freeze bug in Jaunty)
NIC: Attansic L1 Gigabit Ethernet Adapter
Motherboard:Asus P5E-VM HDMI
Memory: 8GB

lspci for the nic:
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

uname -a:
Linux saga 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux

/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 69.196.159.234
	netmask 255.255.255.248
	broadcast 69.196.159.239
	gateway 69.196.159.233
	mtu 1486		#added to reduce fragmentation over PPPOE


I can provide wireshark packet captures if needed but as I said before it shows the packets arriving at the interface for all sizes but no response at all for packets over 1490 bytes.  Seems like the packets are silently discarded if the size is too big (nothing in syslog, dmesg or any of the counters to indicate packet drop).

Any help is appreciated and let me know if there is more info I can provide or if you have any suggestions.  Thanks,

---

### Post by trevelyon on 2009-05-19
This has been solved.  Removing the mtu 1486 from /etc/network/interfaces solved the issue.

---

