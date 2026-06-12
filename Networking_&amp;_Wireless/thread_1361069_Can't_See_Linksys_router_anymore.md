---
title: "Can't See Linksys router anymore"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by rldasilva on 2009-12-21
Greetings,

I am at my parent's house for the holidays and for some reason I can't see their linksys wireless router. The funny thing is I know that I had this all working last time I visited them around Thanksgiving. 

My wireless at home works just fine. There we have a D-link router. Additionally my brother's Windows XP laptop is workign perfectly with the router. 

I've tried for a few hours trying to figure this out but honestly I don't know very much about this stuff. I read through some posted articles for a while but found nothing that was the same problem as mine. 

Thank you in advance!
rds

Below I have posted all the information from the commands listed in the guide on how to make a good post in the order the page lists: (where I knew enough about the output to cut it down to just the relevant details I have)

[PHP]
Output of lspci------------------------------------
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Output of lsusb------------------------------------
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:09b8 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Output of ifconfig------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:23:5a:2a:8b:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:348767526 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2176 (2.1 KB)  TX bytes:2176 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:86:a7:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-86-A7-9E-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Output of iwconfig------------------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Output of lsmod | grep"ath_pci"------------------------------
ath_pci               109168  0 
wlan                  234784  1 ath_pci
ath_hal               225904  1 ath_pci
id misc:0   Missed beacon:0

Output of dmesg | grep "ath_pci"--------------------------------
[   15.863629] ath_pci: 0.9.4

Output of sudo lshw -C network----------------------------------
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:86:a7:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg


Output of iwlist scan----------------------------------
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Output of lsb_release -d----------------------------------
Description:	Ubuntu 8.10

Output of uname -mr------------------------------------
2.6.27-11-generic x86_64


Output of sudo /etc/init.d/networking restart-------------------
* Reconfiguring network interfaces...                                       [ OK ][/PHP]

---

### Post by SlugSlug on 2009-12-21
plug a network cable in and look at routers wireless settings..

---

### Post by rldasilva on 2009-12-21
I just received an email from a friend of mine and suggested that I remove the battery and let it sit for a few minutes, then try again. This worked.

Thanks for your help!
rds

---

