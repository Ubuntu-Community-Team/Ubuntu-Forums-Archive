---
title: "RTL 8168B Gigabit performance"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by ajaysjoshi on 2013-04-30
I am trying to test the throughput of the gigabit network on ubuntu 12.04LTS. I have a gigabyte motherboard with onboard RTL 8168B realtek NICs.

I used pktgen to generate packets. With this I am able to get only  throughput of 137 Mbps. 
[I]
Params: count 10000  min_pkt_size: 60  max_pkt_size: 60
     frags: 0  delay: 1600  clone_skb: 1000000  ifname: eth2
     flows: 0 flowlen: 0
     queue_map_min: 0  queue_map_max: 0
     dst_min: 192.168.3.5  dst_max: 192.168.3.5
        src_min: 192.168.3.2  src_max: 192.168.3.2
     src_mac: 00:1f:d0:27:ed:d4 dst_mac: e8:40:f2:0b:3a:d8
     udp_src_min: 9  udp_src_max: 9  udp_dst_min: 9  udp_dst_max: 9
     src_mac_count: 0  dst_mac_count: 0
     Flags: 
Current:
     pkts-sofar: 10000  errors: 0
     started: 8592308019us  stopped: 8592342740us idle: 181us
     seq_num: 10001  cur_dst_mac_offset: 0  cur_src_mac_offset: 0
     cur_saddr: 0x203a8c0  cur_daddr: 0x503a8c0
     cur_udp_dst: 9  cur_udp_src: 9
     cur_queue_map: 0
     flows: 0
Result: OK: 34720(c34539+d181) usec, 10000 (60byte,0frags)
  288012pps 138Mb/sec (138245760bps) errors: 0[/I]

I tried updating the driver the driver from the realtek website but it still gives the same performance. 

Any ideas about how the performance can be improved and as to why it is so sluggish ?

---

### Post by TheFu on 2013-04-30
I have a 10. 04 system with that card and routinely see 650+Mbps (74MB/s) transfers to/from it.
I would start by checking
* the other system involved with the tests
* the cabling - 5e or CAT 6? Swap out the cable to check. Look for interference. CAT6 is 20x overkill, BTW, but I use it for all server-to-server connections.
* the switch/router connecting the systems. Not all switches are created equal. Sometimes a switch will get slower before failing. Had a D-Link fail after 6 yrs of hard use in that way. 
* the bus architecture for your motherboard. If the GigE NIC is on the same bus as other data-hungry devices, that PCI bus could be the limiting factor.

As an example, some cheap switches sold for home use don't have a backplane that can support GigE full-duplex throughput. Definitely check the specifications on yours.

Lastly, I'd install ethtool to see all the real settings and perhaps tweak those.

Personally, I prefer to use Intel PRO/1000 GigE NICs for primary server connections. They are THE STANDARD. Every VM actually provides emulation of this hardware, that is how "standard" they are. Plus they are relatively cheap - $15-25.  I've had a few cheaper cards ($10-15) over the years and only saw 250-300Mbps throughput with those cards.  When I first started using GigE, that was enough difference that I didn't complain, but after dropping in a few PRO/1000 cards and seeing 650+Mbps, I've become completely addicted.

Good luck.

---

### Post by ajaysjoshi on 2013-05-03
Finally when I changed the packet size to 1500 bytes, I was able to get the Realtek running at around 987Mbps.. Still do not understand why.. 

Any ideas on this ?

---

### Post by TheFu on 2013-05-03
Sounds like something else in your network is not GigE ready or compliant.  
Any packet less than 9000 bytes (called a jumbo packet) should work, right?

I don't use jumbo packets on my network because some of the devices on the LAN are not GigE and when those systems communicate directly (not though a router or a smart, managed, switch), it can be bad.

---

