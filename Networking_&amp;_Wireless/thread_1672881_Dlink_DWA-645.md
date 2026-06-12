---
title: "Dlink DWA-645"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by dargaud on 2011-01-21
Hello all,
I just bought a D-Link DWA-645 PCMCIA card because after some search I had the impression that it worked out of the box with Ubuntu. No luck. By default it uses the ath9k driver but I don't see a wlan device.
After following the [instructions found here]("http://ubuntuforums.org/showthread.php?t=1484242") to install the madwifi driver, here's what I get:
```
[  109.419592] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[  110.027822] ath_pci 0000:06:00.0: PCI INT A disabled
[  138.784088] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[  138.784181] pci 0000:06:00.0: reg 10: [mem 0x00000000-0x0000ffff]
[  138.784357] pci 0000:06:00.0: BAR 0: assigned [mem 0x84000000-0x8400ffff]
[  138.784373] pci 0000:06:00.0: BAR 0: set to [mem 0x84000000-0x8400ffff] (PCI address [0x84000000-0x8400ffff]
[  138.785901] ath_pci 0000:06:00.0: enabling device (0000 -> 0002)
[  138.785925] ath_pci 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  139.354722] MadWifi: ath_attach: Switching rfkill capability off.
[  139.357136] wifi0: Atheros AR5418 chip found (MAC 13.10, PHY SChip 8.1, Radio 13.0)
[  139.359169] ath_pci: wifi0: Atheros 5416: mem=0x84000000, irq=17
```
```
$ lspci
06:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:42:37:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53147 (53.1 KB)  TX bytes:53147 (53.1 KB)
```
```
# lshw -c network
  *-network DISABLED
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 1c:af:f7:f6:4e:2b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 multicast=yes wireless=IEEE 802.11b
       resources: irq:17 memory:84000000-8400ffff
```

---

### Post by dargaud on 2011-01-21
I got it. I had to "ifconfig wlan2 up" and then in wicd, go in Preferences and change wlan1 to wlan2. That's all.

---

