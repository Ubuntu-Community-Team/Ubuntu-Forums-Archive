---
title: "Lost Packets with eth0"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by Timc940 on 2010-05-26
Hello All,

I currently have a desktop install 10.04 ( 2.6.32-22-generic #33-Ubuntu SMP ) AMD 64 and for some reason on this box I'm getting dropped packets with the Ethernet adapter. i have also replaced the Ethernet cable just to ha's to see what would happen. The adapter details are: 

          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:24:21:14:56:5c
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.
110 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: irq:28 memory:dfd7d000-dfd7dfff ioport:de00(size=8)


Below is a ping showing that there is a loss in packets..

PING any-fp.wa1.b.yahoo.com (69.147.125.65) 56(84) bytes of data.
64 bytes from ir1.fp.vip.re1.yahoo.com (69.147.125.65): icmp_seq=1 ttl=50 time=28.8 ms
64 bytes from ir1.fp.vip.re1.yahoo.com (69.147.125.65): icmp_seq=2 ttl=50 time=25.7 ms
64 bytes from ir1.fp.vip.re1.yahoo.com (69.147.125.65): icmp_seq=5 ttl=50 time=24.4 ms
64 bytes from ir1.fp.vip.re1.yahoo.com (69.147.125.65): icmp_seq=8 ttl=50 time=24.0 ms
64 bytes from ir1.fp.vip.re1.yahoo.com (69.147.125.65): icmp_seq=10 ttl=50 time=25.6 ms

--- any-fp.wa1.b.yahoo.com ping statistics ---
10 packets transmitted, 5 received, 50% packet loss, time 9030ms
rtt min/avg/max/mdev = 24.064/25.738/28.821/1.686 ms

Note also there is no packet loss when i ping from the router or other devices on the network. And i have disabled ipv6 and ifconfig is not showing any dropped packets

        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26985021 (26.9 MB)  TX bytes:4490318 (4.4 MB)
          Interrupt:28

Any assistance with this issue would be great !! It has been racking my brain for days now !!!!

---

