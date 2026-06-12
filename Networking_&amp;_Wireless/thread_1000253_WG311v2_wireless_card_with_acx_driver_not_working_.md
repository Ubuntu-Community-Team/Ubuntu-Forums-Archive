---
title: "WG311v2 wireless card with acx driver not working on 8.10"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by Existence on 2008-12-02
Hey everyone,
I'm fairly new to Linux in general, but I think I have a pretty good understanding of how things work. Now, I just installed Ubuntu Intrepid (8.10) and my wireless card, the Netgear WG311v2 doesn't seem to work.

I've spent about 3-4 days trying to fix it, but it just doesn't seem to connect. The card and driver gets recognized, but no networks can be found. I've tried disabling the Network Manager, I've tried using ndiswrapper, I've tried using the custom drivers located [HERE]("http://acx100.sourceforge.net/"), but nothing has worked.

If you need any more info, just ask.

Any help is appreciated,
Thanks.

---

### Post by Existence on 2008-12-03
Alright, here's a bit more info.

iwconfig wlan0
```
wlan0     IEEE 802.11b+/g+  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lshw
 ```
 *-network
             description: Wireless interface
             product: ACX 111 54Mbps Wireless Interface
             vendor: Texas Instruments
             physical id: 0
             bus info: pci@0000:01:00.0
             logical name: wlan0
             version: 00
             serial: 00:0f:b5:48:43:84
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
```
I'm gonna try to install wicd now, and some other stuff.

---

### Post by Existence on 2008-12-04
Hmm, im now conpletely at a loss. Is there anything else I can do? :/

---

