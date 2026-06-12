---
title: "ubuntu 8.10 and eeepc 1000he wireless problem"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by powerman15 on 2009-08-10
Hi guys, 

This is really becoming annoying, firstly i installed ubuntu netbook remix and was unable to get my wireless to connect (at home) yet it connected to my university network :S

i didn't like the netbook remix, so now ive gone for the stable desktop ubuntu 8.10 with the eeepc kernel from array.org

I read through 10 or more forums about the problem, and fiddled with all sorts of settings.

i installed the RT2860STA driver and uninstalled network manager.. and that didnt work, or though doing a ```
iwlist scan
``` came up with results, of finding my home network, but trying a ```
iwconfig ra0 essid "....."
``` found error for wireless request "set essid"

so i've just done a clean format, and now have 8.10 with eeepc kernel

I know the wireless device is Ralink Device 0781..


i'm out of ideas...?

Cheers

---

### Post by The Toxic Mite on 2009-08-10
Hmm, I know you said you know what device it is, but it might be a bit unclear to some people.

Can you go to Applications > Accessories > Terminal and do the following commands please?

```

sudo lshw -c network
iwconfig
ifconfig

```

Once you're done, post the outputs of these commands.

Thanks :)

---

### Post by powerman15 on 2009-08-10
yeah no worries, heres the outputs
lshw -c network
>   *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:26:18:1b:0e:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.0.7 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:25:d3:14:dd:55
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:2b:da:65:fe:fb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


iwconfig
> lo        no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.437 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-72 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pan0      no wireless extensions.


ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:26:18:1b:0e:6b  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe1b:e6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:945 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1246441 (1.2 MB)  TX bytes:153730 (153.7 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15132 (15.1 KB)  TX bytes:15132 (15.1 KB)

ra0       Link encap:Ethernet  HWaddr 00:25:d3:14:dd:55  
          inet6 addr: fe80::225:d3ff:fe14:dd55/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270782 (270.7 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 


Thanks :)

---

