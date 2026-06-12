---
title: "Upgrade to 11.04 loses network for Realtek 8168B"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by callenish on 2011-05-04
I should know better by now than to try to upgrade Ubuntu, but hope springs eternal...

Upgraded to 11.04 and on reboot my network suddenly stopped working. ifconfig showed no IP address associated with eth0. No network access was possible.

Reading the forums it seemed others had this problem and fixed it by adding eth0 to /etc/network/interfaces. I tried that and was finally able to get ifconfig to show me an inet line with my specified static IP address, but I still can't ping even my router.

Could this be related to this[1] bug? 

[1] [http://fossplanet.com/f10/%5Bbug-771857%5D-%5Bnew%5D-realtek-8168b-r8169-interface-not-workingfollowing-suspend-139001/](http://fossplanet.com/f10/%5Bbug-771857%5D-%5Bnew%5D-realtek-8168b-r8169-interface-not-workingfollowing-suspend-139001/)

My ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:81:48:ce  
          inet addr:192.168.145.14  Bcast:192.168.145.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2912 (2.9 KB)  TX bytes:2912 (2.9 KB)
```Output from lspci | grep ethernet:

```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```My list of drivers:

```
firewire-ohci
r8169
pata_jmicron
ahci
snd-hda-intel
nvidia-current
nouveau
nvidiafb
i2c-i801
iTCO_wdt
shpchp

```Any help appreciated.

---

