---
title: "Jaunty network issue"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by pauled on 2009-07-06
Hi,

I have recently upgraded to Jaunty and ever since have been suffering network problems, Intrepid was fine. This occurs when a file is opened by a windows pc using the samba share. The network seems to stop, active ssh connections can be terminated if in use.

The only thing I have to go on is this snippet from /var/log/syslog which seems to echo what I am suffering. All the system seems to be doing to right itself is restart the network card. 

Network card is an Intel PRO/1000

Could anyone please point me in the right direction, has anything changed within the networking ?

Many thanks

Paul

Jul 10 10:55:19 mae kernel: [331966.000142] e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang
Jul 10 10:55:19 mae kernel: [331966.000145]   Tx Queue             <0>
Jul 10 10:55:19 mae kernel: [331966.000146]   TDH                  <9a>
Jul 10 10:55:19 mae kernel: [331966.000147]   TDT                  <a5>
Jul 10 10:55:19 mae kernel: [331966.000148]   next_to_use          <a5>
Jul 10 10:55:19 mae kernel: [331966.000149]   next_to_clean        <94>
Jul 10 10:55:19 mae kernel: [331966.000150] buffer_info[next_to_clean]
Jul 10 10:55:19 mae kernel: [331966.000151]   time_stamp           <4f12bb5>
Jul 10 10:55:19 mae kernel: [331966.000152]   next_to_watch        <9b>
Jul 10 10:55:19 mae kernel: [331966.000153]   jiffies              <4f13494>
Jul 10 10:55:19 mae kernel: [331966.000154]   next_to_watch.status <0>
Jul 10 10:55:20 mae NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Jul 10 10:55:22 mae NetworkManager: <info>  (eth0): carrier now ON (device state 1)
Jul 10 10:55:22 mae kernel: [331968.716374] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX

eth0 : 03:07.0
    Make/Model = Intel Corporation Device 341a
    Ethernet controller = Intel Corporation 82546EB Gigabit Ethernet Controller
    VenID:DevID = 8086:1010
    Driver name = e1000
    Driver version = 7.3.21-k3-NAPI
eth1 : 03:07.1
    Make/Model = Intel Corporation Device 341a
    Ethernet controller = Intel Corporation 82546EB Gigabit Ethernet Controller
    VenID:DevID = 8086:1010
    Driver name = e1000
    Driver version = 7.3.21-k3-NAPI

---

