---
title: "Network suddenly loss"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by ling-g on 2006-06-06
I installed Breezy about three weeks ago. The network works perfectly at the beginning. Then, last week I have a crash on my Windows (dualboot), and I was asked to reset
my BIOS to default. And since then, my network does not work anymore on Breezy, though it works on Windows.

I tried to figure out what was the problem but unsuccessful. In fact, this is my first time installing Linux on a machine (mine is Thinkpad Z60t) and I really have no idea how to do all those configurations, setups, troubleshooting, etc. So, I really hope that someone could help me to solve this problem. 

These are some of the outputs of some commands (type, not cut & paste):

lspci:
0000:02:00.0 Ethernet Controller: Broadcom Corporation: Unknown device 167d

dmesg | grep eth:
eth0: Togon [partno(BCM95751M)] rev 4101 PHY (5750) ] (PCIX: 100MHz:32-bit) 10/100/1000BaseT Ethernet 00:16:36:18:ae:d7
eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOca[[1]
eth0: dma_rwctrl[76180000]
tg3: tg3_reset_hw timed out for eth0, firmware will not restart magic=4b657654

ifconfig eth0:
eth0    Link encap:Ethernet   HWaddr  00:16:36:18:AE:D7
           BROADCAST MULTICAST  MTU:1500   Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carriers:0
          collisions:0 txqueuelem:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupts:16

Anyone can figure out what is the problem and how to solve it ? Could it be a hardware failure ?

---

### Post by Iowan on 2006-06-06
Not sure, but I wonder if the PnP BIOS setting got re-activated, and needs to  be turned off.

---

### Post by ling-g on 2006-06-06
How to check whether it is PnP BIOS ? I don't see anything stated as PnP in my BIOS.

These messages came out when I do "dhclient eth0".

sit0: unknown hardware address type 776
Listening on LPF/eth0/<MAC address>
Sending on LPF/etho/<MAC address>
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down

---

