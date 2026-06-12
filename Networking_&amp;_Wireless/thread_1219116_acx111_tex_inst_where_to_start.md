---
title: "acx111 tex inst where to start??"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by ledoc on 2009-07-21
Hellooo :P
 
ok so this im relatively new to ubuntu, ive had a little bit of experience with knoppix in the past but very little at that.
 
Inevitably im stuck at the first hurdle, ive done a fair bit of swatting up on this problem and im a little confused about where to start and whether or not i do actually have a problem with the drivers for this particular wireless chipset. heres a few bits and bobs ive pulled out of the terminal.
 
02:06.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
Subsystem: Abocom Systems Inc Device ab90
Flags: bus master, medium devsel, latency 32, IRQ 22
Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]
Memory at fcfc0000 (32-bit, non-prefetchable) [size=128K]
Capabilities: <access denied>
Kernel driver in use: acx_pci
Kernel modules: acx
 
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wlan0 No scan results
pan0 Interface doesn't support scanning.
 
iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11b+/g+ Nickname:"acx v0.3.36"
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Bit Rate:54 Mb/s Tx-Power=15 dBm Sensitivity=1/3 
Retry min limit:7 RTS thr:off 
Power Management:off
Link Quality=36/100 Signal level=10/100 Noise level=0/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:4 Invalid misc:0 Missed beacon:0
pan0 no wireless extensions.
 
like i said im unsure wether i do have a driver issue at present? i suspect i do but also after that im unsure of which course of action to take.. be it having a go with ndiswrapper or changing the firmware on the card? or even getting a new card as ive already read that i may come into problems when trying to get this card working with wpa2 which is essential unfortunately.
 
any help would be greatly appreciated.

---

