---
title: "Network card not Detected"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2009-02-05
I installed Ubuntu 8.10 about a week ago but under the Network Manager there was no devices listed. I didn't think much of it because i had the same thing happen to another computer of mine. But I could seem to get it to work on this system. So i decided to install 8.04 which my NIC had worked on before (I believe may have been 7.10 or whatever). Point being i know this card works under Linux. Well it doesnt work. If any one has any ideas let me know.

1) The network manager is detecting an old phone modem (but not my NIC)..... could that be it.

2) my card is TRENDnet TEG-PCITXR (version 2.0)

My lspci:
```
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:0e.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)

```

My ifconfig:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:752 (752.0 B)  TX bytes:752 (752.0 B)

```

---

### Post by ductiletoaster on 2009-02-05
So it seems that having the modem and the Ethernet card in at the same time kept Ubuntu from detecting my NIC card. Though i dont use the phone/fax modem i am goin to to try and see if i can now put that card in and see if i can connect both. I will post my results on this forum for any one interested.

To recap: i had two communication devices plugged into pci slots. the phone/fax modem in the first slot and the NIC in the second. Ubuntu was not detecting the NIC card but was installing the modem.

Well my NIC card is installed and connected. Overall the fix was to remove the Fax modem and only have the NIC card in the slot. Now im not a hardware expert but it could be that the PCI slot two went out.... Because i did move the NIC into another slot.

---

