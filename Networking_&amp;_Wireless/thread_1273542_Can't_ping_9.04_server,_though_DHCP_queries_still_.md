---
title: "Can't ping 9.04 server, though DHCP queries still work"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by crashsystems on 2009-09-23
Recently I set up a new server running Ubuntu 9.04 server addition. However, I am having some very strange networking issues with the system. I have no clue what is causing these issues, so I'll provide as much details as possible, in hopes someone can point me in the right direction.

Here are the details on the network hardware setup: Ethernet is coming from a cable modem into eth0 on the server, which acts as a gateway and caching proxy (Squid). eth1,eth2,eth3 are plugged into ports 22,23,24 on an HP ProCurve 1800-24G switch. Those three ports are set up for [*mode 4 link aggregation*]("https://wiki.ubuntu.com/LinkAggregation") to form bond0, and the switch has been configured for this as well. The server's LAN IP address (bond0) is 192.168.0.1. There are two Linksys wireless routers, plugged into the switch at ports 1 and 2, IP addresses 192.168.0.2 and 192.168.0.3.

The server is running 9.04 server. It is configured to act as a gateway, DHCP server and transparent Squid proxy. It will be running some other apps once it is working, but this is the extent of it's configuration so far.

Here is a list of the server's hardware:
[LIST]
[*][NZXT Beta Series CS-NT-BETA-B Black Steel / Plastic ATX Mid Tower Computer Case - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811146055")
[*][SUPERMICRO MBD-C2SBC-Q-O LGA 775 Intel Q35 ATX Intel Motherboard - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182151")
[*][Antec earthwatts EA500 500W Continuous Power ATX12V v2.0 SLI Certified CrossFire Ready 80 PLUS Certified Active PFC Power Supply - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007")
[*][Intel Core 2 Quad Q8200 2.33GHz 4MB L2 Cache LGA 775 95W Quad-Core Processor - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115055")
[*][OCZ Flex EX 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Ehanced Bandwidth Desktop Memory Model OCZ2FXE800EB4GK - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227400")
[*][Intel EXPI9402PT 10/ 100/ 1000Mbps PCI-Express PRO/1000 PT Dual Port Server Adapter 2 x RJ45 - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106014")
[*][Western Digital Caviar Green WD10EADS 1TB 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317")
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317)
[*][Intel X25-E Extreme SSDSA2SH032G1 2.5" 32GB SATA II SLC Internal Solid state disk (SSD) - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820167013")
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820167013](http://www.newegg.com/Product/Product.aspx?Item=N82E16820167013)
[*][iStarUSA DIY-RP-HDD2.5 2.5" to 3.5" Hard Drive Mounting Bracket - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816215157")
[/LIST]

The server can ping any server on the Internet, and can ping the first wireless router at 192.168.0.2, but not the second. When I plug my laptop into the switch, the server assigns it an IP via DHCP. The laptop can then ping the first wireless router, but not the second. The laptop cannot ping the server, and nether can the server ping the laptop. When the laptop tries to ping the outside world, or load a webpage, NAT is not working.

I'm supplying the configuration details for the old, working server for comparison, because as far as software goes, the configuration is almost identical. The old server was running 8.04, while the new server is running 9.04. To download /etc for both old and new servers, [*click here*]("http://drop.io/ar7w8io") to download them. From that location you can also download tcpdumps ran on both the server and my laptop, as I did pings and DHCP queries. You can also find the /etc/network/interfaces file from the new server in the attachments below, as well as a dump of the iptables rules from both the old and the new servers.

If someone could look at this and tell me what they think, I would appreciate it. Also, if there is any more data I can gather that would be useful, please let me know.

---

### Post by crashsystems on 2009-09-26
The only variable I could think of between old working configs I've done and this new not working install was that the old installs were running 8.04 server, while the new one was running 9.04 server. With that in mind I installed 8.04, and configured it identically to what the previous install was running. Still no luck.

Anyone have any ideas?

---

### Post by Iowan on 2009-09-27
The link for "mode 4 link aggregation" is broken (missing the initial "h"). Did you use this on the original 8.04 install? Is **route** set up properly on server? (you mentioned that it was the same as previous, working system). Are you pinging by name or IP address?

---

### Post by crashsystems on 2009-09-27
Oops. Yes, this setup is identical to working setups I've done before with 8.04. Of course, I put 8.04 on the server yesterday, so release number is not the issue. I am pinging by IP address. I've not checked out the routing table yet. Do you have any recommendations/links for when I do so later today, specifically how to spot routing table problems and fix them?

---

### Post by crashsystems on 2009-09-28
I just checked out the routing table for the server:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
75.148.79.36    *               255.255.255.252 U     0      0        0 eth0
192.168.0.0     *               255.255.0.0     U     0      0        0 bond0
default         75-148-79-38-Ja 0.0.0.0         UG    100    0        0 eth0

```
This is exactly the same routing table that appears in the old, functional server, except this one of course has a bond0 interface instead of eth1.

---

### Post by Iowan on 2009-09-29
I shoulda mentioned - **route -n** will give numeric results. Is the default gateway supposed to be eth0?

---

### Post by crashsystems on 2009-09-29
Yes, the default gateway is supposed to be on eth0 (the port connected to the cable modem).

Here is the routing table, with the -n parameter:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
75.148.79.36    0.0.0.0         255.255.255.252 U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 bond0
0.0.0.0         75.148.79.38    0.0.0.0         UG    100    0        0 eth0
```

---

