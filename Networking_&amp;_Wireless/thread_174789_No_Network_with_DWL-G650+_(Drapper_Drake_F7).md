---
title: "No Network with DWL-G650+ (Drapper Drake F7)"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by sajin on 2006-05-12
Greetings, i just installed Ubuntu - Drapper Drake Flight 7 - and cannot get my wireless lan working. I tried many forum threads / FAQs since yesterday, but nothing helped ](*,) :???:  . PCMCIA-Card is D-Link DWL-G650+ with Texas 
Intruments chipset acx111. 

The card was found, and ubuntu associated the acx_pci driver apparently
lshw -class network : 

```
  *-network:0 DISABLED
      (...)
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       (...)
       resources: iomemory:d0000000-d0000fff irq:10
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 00
       serial: 00:11:95:6d:e6:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:d2020000-d2021fff iomemory:d2000000-d201ffff irq:10

```
/etc/network/interfaces
A poster suggested in a similar thread that inserting "map wlan0" might do 
the trick, so i did that - to no avail.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

map wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid FRITZ!Box SL WLAN
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX

auto wlan0

```

Searchin with lsmod for acx_pci (the driver according to lshw), there is no text returned. If i use normal lshw, there are just two acx lines. Is this the driver ? 

```
Module                  Size  Used by
acx                   101132  0 
pcmcia                 40508  0 
ipw2100                87732  0 
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
pci_hotplug            29236  1 shpchp
usbcore               129668  9 acx,snd_usb_audio,snd_usb_lib,em28xx,usbhid,usb_storage,ehci_hcd,uhci_hcd

```

iwconfig

```
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          (...)

wlan0     IEEE 802.11b+/g+  ESSID:"FRITZ!Box SL WLAN"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality:35/100  Signal level:9/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I really have no idea how to continue. iwlist wlan0 scan doesnt find any aps, 
but the router works in windows without problems. I cannot modify the router, and it has WEP 128 encryption. 

Thanx for your help, 
Sajin

---

### Post by SSamiK on 2006-05-28
I had the same exact problem, and solved it by following zanglang's method witch is described in [http://ubuntuforums.org/showthread.php?t=145836&highlight=acx]("http://ubuntuforums.org/showthread.php?t=145836&highlight=acx"), post #3.

---

