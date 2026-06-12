---
title: "Molasses for Wireless"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by MrDead on 2009-04-29
Ever since installing Ubuntu (I am currently running 9.04) I've had endless problems with my Internet connections: intermittent connection loss, slow download speeds, complete loss of connection, etc. For a while me and my Internet had a rocky, but stable, relationship; however, now my erstwhile partner has turned sour, and I am getting incredibly slow connection speeds compounded with an unstable connection. For instance: I have FiOS (I think it's rated at 10mbps) and I am only getting maximum speeds of 200 kbps, and normal speeds of 90-100 kbps; additionally my connection sometimes gets it in its head that it needs a rest so it shuts off for a little while and then needs some serious coaxing to get it up again. 
I am using a Ralink 148f:2870 USB wireless device with an RT2870 driver (not ndiswrapper). 

Here is my iwconfig output:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"6ECL2"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1F:90:EE:E1:28   
          Bit Rate=48 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=67/100  Signal level:-72 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here is my lshw -C Network output:
*-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:37:81:36
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:24:a2:dd:0d:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:18:e7:4a:48:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.6 multicast=yes wireless=RT2870 Wireless

Here is my ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:24:8c:37:81:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:847291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:847291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:214099311 (214.0 MB)  TX bytes:214099311 (214.0 MB)

ra0       Link encap:Ethernet  HWaddr 00:18:e7:4a:48:b6  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe4a:48b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30703058 (30.7 MB)  TX bytes:1916038 (1.9 MB

I hope any of this information can help, 

Thank You Very Much

---

### Post by MrDead on 2009-05-02
Bump, plus this also somehow restricts bittorrent download speeds and number of seeders. However it hardly effects bittorent upload speeds which easily reach around 300 kbps, which is comparable to what I had been getting.

---

