---
title: "Cannot see any networks with Atheros AR242X"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by antonym on 2008-12-27
Considering the number of threads about atheros wifi cards and ubuntu I was hesitant to start a new one.... but I've been working at this for two days now, trying every solution I could find, and I still CANNOT get my wireless card to see any networks. (I know they're there -- a different laptop sees them)

I have an Acer Aspire One, running Intrepid (2.6.27-9-generic). 

I've tried installing linux-backports-modules-intrepid, activating the ath5k driver, and blacklisting ath_pci and ath_hal.
I've tried installing the madwifi drivers using instructions found around these forums.
I've tried using ndiswrapper, also using instructions found in one of these threads.
I did a clean install and tried using the ath5k drivers again.
Regardless of what I do, the most I can get out of the network manager is what you see in the image attached. It never sees any networks. I've tried the wifi switch too, in case the card was somehow off... it doesn't seem to affect anything.

Does anyone have any ideas at all what I could try, or want to walk me through something in case I'm making some sort of stupid error somewhere? I'm getting desperate here :(


Thanks in advance!


Some code output, off the top of my head... if you need anything else just let me know.

```
 lshw -c network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:d5:81:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:16:b5:79
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:8c:33:40:94:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

``````
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:d5:81:63  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fed5:8163/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4256 errors:0 dropped:3471198406 overruns:0 frame:0
          TX packets:3162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4496597 (4.4 MB)  TX bytes:409784 (409.7 KB)
          Interrupt:219 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr 06:8c:33:40:94:1a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:16:b5:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-16-B5-79-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by antonym on 2008-12-27
update --   after installing a new kernel update from this morning (from .27-9 to .27-11), the wired internet has stopped working as well... it sees eth0 as being there, but cannot connect to it. (booting back into .27-9 makes ethernet work again, fortunately)

---

### Post by antonym on 2008-12-29
No one has any suggestions, about the wireless drivers or about the wired connection?

---

