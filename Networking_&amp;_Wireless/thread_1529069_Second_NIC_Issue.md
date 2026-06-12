---
title: "Second NIC Issue"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by GardenCity on 2010-07-11
Hi All,
I'm running Ubuntu 10.04 i386 desktop. Everything works fine, until I tried to add a second NIC. Eth0 works, but when I try to activate eth1, both eth0 and eth1 refuse to run.

Here are my NIC interrupts:
17:   7    19    9     1384 IO-APIC-faste01   eth1
     ....
29:   31  12830 30     24   PCI-MSI-edge      eth0

Here are my interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet static
address 192.168.0.111
netmask 255.255.255.0
gateway 192.168.0.1

I've spent a lot of time searching the Internet, but can't find what's wrong. Can anyone help a novice?

thanks in advance for any tips.

---

### Post by jMon54 on 2010-07-19
Try using a different subnet on the 2nd nic.

---

### Post by Iowan on 2010-07-19
I presume only one NIC will connect to Internet. You should remove the gateway definition from the other one.
(In addition to putting them in different subnets... ;))

If you're trying to do connection sharing, [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page that might be useful.

---

### Post by pricetech on 2010-07-19
Remove the default gateway on one or the other NIC.

---

### Post by yakupm on 2010-12-23
I had a similar situation - 2 nics on a server, eth0 for normal traffic, eth1 for ntop only with all traffic mirrored to it.  I needed eth1 to have an IP on the network so ntop would correctly see local and remote traffic.   With a /24 subnet mask for eth1, it would always appear at the top of the list when I ran route.  Deleting that route would temp fix the problem but the route using eth1 would reappear after reboot.   My solution was to assign eth1 a /32 subnet mask.  route now only shows eth0.  Here's my /etc/network/interfaces showing the /32 mask.

[COLOR=Navy]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 10.175.10.1
        netmask 255.255.255.0
        gateway 10.175.10.254
#ntop mirror port
auto eth1
iface eth1 inet static
        address 10.175.10.2
        [COLOR=Green]netmask 255.255.255.255[/COLOR]

[/COLOR]

---

### Post by yakupm on 2010-12-23
Update:
Everything worked except that ntop was seeing all traffic as remote.  So I changed the netmask (see earlier post) for eth1 to 255.255.254.0.

---

