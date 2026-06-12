---
title: "Centrino drops packets"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by djoelsson on 2006-07-10
Hi,

I have a core due laptop with centrino built in wifi.  In windows, I get about 3Mbps of speed, but I only get 300kbps in dapper drake.  I don't have this problem when I use a PC wifi card. 

My ifconfig output:
eth1      Link encap:Ethernet  HWaddr 00:13:02:7F:3B:ED
          inet addr:192.168.1.160  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14073 errors:18 dropped:8362 overruns:0 frame:0
          TX packets:7306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1646314 (1.5 MiB)  TX bytes:855368 (835.3 KiB)
          Interrupt:185 Base address:0x6000 Memory:da000000-da000fff

My iwconfig output:

eth1      IEEE 802.11b  ESSID:"dansnetwork"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:06:25:9A:1F:7C
          Bit Rate:11 Mb/s   Tx-Power=14 dBm
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=73/100  Signal level=-61 dBm  Noise level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:22  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12592   Missed beacon:0

The PC card shows no dropped packets so I know that my router is not the problem.  Anyone have any ideas?  I have played with the RTS and Fragment thresholds, but I couldn't tell any differences.  The transmission power is at max.

Any help would be appreciated!

Thanks,
Dan

---

### Post by djoelsson on 2006-07-21
bumb...

I'm getting desperate.

Thanks,
Dan

---

