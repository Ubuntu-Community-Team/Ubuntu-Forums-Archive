---
title: "Network Setup"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by tomzie on 2013-03-05
I have just installed Ubuntu Server 12.04 on my old PC (Intel Celeron 2.40GHz, 40GB HD). During the installation, the network configuration failed. It was saying that I might not have DHCP Protocol capability. Now I wanted to setup my network at the command prompt now. Here is the information I get. Please help. Thanks.

$ ifconfig -a | grep eth
eth0     Link encap:Ethernet  HWaddr 00:01:29:25:4b:fc

$ lshw -class network
*-network DISABLED
        description: Ethernet Interface
        product: VT6102 [Rhine-II]
        vendor: VIA Technologies, Inc.
        logical name: eth0
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbits/s
        resources: irq:11 ioport:ec00(size=256) memory:ec101000-ec1010ff

---

### Post by prodigy_ on 2013-03-05
If you don't have DHCP, you can setup static configuration in **/etc/network/interfaces** file:
[https://help.ubuntu.com/10.04/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/10.04/serverguide/network-configuration.html#ip-addressing)
[http://manpages.ubuntu.com/manpages/lucid/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/interfaces.5.html)

---

### Post by oldos2er on 2013-03-05
Moved to Networking & Wireless.

---

### Post by cortman on 2013-03-05
[This page]("https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic") may be of help as well.

---

### Post by tomzie on 2013-03-05
Thanks all for the reply.

I added the lines below and restarted my computer. I am currently updating now.

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

