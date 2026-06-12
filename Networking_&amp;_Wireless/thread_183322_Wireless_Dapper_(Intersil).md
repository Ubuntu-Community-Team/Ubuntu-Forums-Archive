---
title: "Wireless Dapper (Intersil)"
date: 2006-05-27
forum: Networking &amp; Wireless
---

### Post by akaSlack on 2006-05-27
Hey I`ve just installed Dapper and have a SMC wireless card that don`t want to start :( 

output of lspci: 
0000:02:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

output of iwconfig
eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

output of lshw
 *-network:0 DISABLED
                description: Wireless interface
                product: Intersil ISL3890 [Prism GT/Prism Duette]
                vendor: Intersil Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth1
                version: 01
                serial: 00:30:b4:00:00:00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=prism54 multicast=yes wireless=NOT READY!
                resources: iomemory:f2000000-f2001fff irq:217


Any solution? :confused:

---

