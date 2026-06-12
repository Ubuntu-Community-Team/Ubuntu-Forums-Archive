---
title: "wifi - Driver looks ok, device disabled (prism64)"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by ahaman on 2006-02-25
I have tried setting up my wireless card Accton wn4201b, but the card is disabled. Any ideas how to enable it?

lshw:
network:0 DISABLED
                description: Wireless interface
                product: Intersil ISL3890 [Prism GT/Prism Duette]
                vendor: Intersil Corporation
                physical id: 7
                bus info: pci@01:07.0
                logical name: eth2
                version: 01
                serial: 00:30:b4:00:00:00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=prism54 multicast=yes wireless=NOT READY!

---

### Post by arckeda on 2006-02-25
First of all configure your card then activate it, then at bash type:


sudo iwconfig wlan0 essid any ap any

---

### Post by ahaman on 2006-02-25
thanks for answer!
actually my card  is now seen as eth2 (i have 2 normal eth cards also).

sudo iwconfig eth2 essid any ap any

root@kjeller3:/home/anders# iwconfig
lo        no wireless extensions.

eth3      no wireless extensions.

eth0      no wireless extensions.

eth2      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: FF:FF:FF:FF:FF:FF
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

