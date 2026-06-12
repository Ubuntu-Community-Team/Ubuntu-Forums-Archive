---
title: "WLAN Access: DLink DKT-110 wireless router + Broadcom BCM4312"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by kushana on 2009-05-18
Hi,

I am trying to access wlan from my notebook. I have jaunty running on HP 550 with Broadcom BCM4312 chipset.  The wireless router I am using is Dlink dkt-110. Initially
it worked out of box and I was able to access the network, however after I restarted
the wireless router  I have not been able to access it again. The desired network
does not even show up in the list of available wlans. Let me also add that I am relatively
new to Linux. 
Thanks in advance.

cheers

---

### Post by Michael.Godawski on 2009-05-18
hey kushana, 

perhaps you can give us some additional info so the issue at hand gets a little bit clearer.
Just open up the terminal and post the outputs of these commands:

```

iwconfig
ifconfig
sudo iwlist scan
sudo lshw -C network
```

---

### Post by kushana on 2009-05-18
Hi Michael,

Thanks for the reply.
Actually I scanned the forums for the workaround and tried those commands, nevertheless I am pasting the output.

```

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:202  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

``````

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:64:76:16:e2  
          inet addr:134.106.22.94  Bcast:134.106.22.95  Mask:255.255.255.224
          inet6 addr: fe80::222:64ff:fe76:16e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:41466302 (41.4 MB)  TX bytes:783462 (783.4 KB)
          Memory:e4600000-e4620000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:92:08:81  
          inet6 addr: fe80::221:ff:fe92:881/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

``````

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:24:8E:56:50
                    ESSID:"uniOLwlan"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-93 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:12:43:F9:2F:E0
                    ESSID:"uniOLwlan"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:5/5  Signal level:-43 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:0F:24:8E:45:60
                    ESSID:"uniOLwlan"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:0F:24:94:AE:40
                    ESSID:"uniOLwlan"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-55 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

``````

sudo lshw -C network

*-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:64:76:16:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-2 ip=134.106.22.94 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:92:08:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:0d:f7:fd:10:bc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

---

### Post by kushana on 2009-05-19
bump

---

