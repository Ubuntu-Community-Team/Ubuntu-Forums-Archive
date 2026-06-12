---
title: "Atheros nor madwifi work on compaq CQ60: Lucid"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by Bubnoff on 2010-12-11
On a fresh install, Lucid works perfectly. Week later, after updates, no WiFi. 

Specs:
Compaq Presario CQ60

lspci shows:
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

lshw -C network shows:
```
*-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:26:5e:4d:6f:c6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:92600000-9260ffff
```

As you can see, I followed the madwifi instructions, replacing the previously used ath5k driver with madwifi.

Light is now orange for WiFi, no networks.

here's the instructions I followed:
[http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)

Can anyone confirm if Maverick Meerkat support is better or worse. Not able to get a clear idea from Google.

Backports were installed beforehand. I also commented out the "blacklist ath_pci" in the file in /etc/modprobe.d. 

From dmesg | grep wifi:
```
[   17.816467] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[   17.820484] ath_pci: wifi0: Atheros 5424/2424: mem=0x92600000, irq=17


```

Here's some ifconfig after the madwifi installation:
```

ath0      Link encap:Ethernet  HWaddr 00:26:5e:4d:6f:c6  
          inet6 addr: fe80::226:5eff:fe4d:6fc6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wifi0     Link encap:UNSPEC  HWaddr 00-26-5E-4D-6F-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:26588 (26.5 KB)
          Interrupt:17 

```

Thanks for reading

Bubnoff

---

