---
title: "How can I test my gigabit network throughput speed?"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by sofakng on 2009-08-12
I'm connecting from Ubuntu 9.04 to my Windows Home Server using SMB/CIFS and I'd like to run some tests.

How can I test my network throughput on my setup?

I'd also like to compare my onboard NIC's speed to an Intel 1000 GT (PCI).  My only concern is that the onboard NIC is likely connected to PCIe whereas the Intel card is only PCI.

---

### Post by LowSky on 2009-08-12
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting)

---

### Post by jonobr on 2009-08-12
Hello

You can also use iperf which is a command line utility that allows you to set one side up as a client or server, and the other side as the opposite.

You can define the amount of traffic you want to test with and transport type.
Ie udp or tcp.
It will give information on jitter, packet loss, throughput and so on

There is also a java based program called jperf which is the same program with a nice gui interface.

If you would like more info on setup of it, let me know and I can put up some info on configuration

---

