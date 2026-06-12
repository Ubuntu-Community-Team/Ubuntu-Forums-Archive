---
title: "Troubles getting Ralink RT2860 Wireless Working after upgrading to 11.10"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by camlee on 2012-11-12
I'm having trouble getting my wireless (WiFi) working after upgrading from Ubuntu 11.04. By working, I mean able to connect to my home WiFi network (2.4GHz, 802.11 g, encrypted - but I don't think any of this is the issue). It started as soon as I reached 11.10, and I've since upgraded all the way to 12.10 and am still having issues. I'm using an LG R580 laptop and believe that my wireless hardware is RT2860.

Here's a rough history:

When I first installed Ubuntu, many years ago, the wireless wasn't working then. If my memory serves, I could see networks and try to connect, but I would repeatedly be re-prompted for a password. I did some searching and found instructions somewhere to make it work. I'm pretty sure that these are the instructions that I followed back then: [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)
Things worked perfectly after this for several years. In this time, I've used Ubuntu lots and couldn't live without it (although I dual boot Windows 7).

Within the last week, I got a message saying that 11.04 had reached end of life, so I upgraded to 11.10. Then the wireless stopped working again. Different symptoms this time though. Firstly, I couldn't see an icon in the status tray for networking. I had to go to System Settings then Network to get to the Network Manager. Then, I could see the networks in Network Manager, but when I click connect, nothing happens. In fact, it said disconnected before and after I clicked.

I started looking around for a solution again. Eventually, I re-found the original instructions that I had followed and noticed that they said after a kernel upgrade, they would have to be re-followed. So I followed them again. This didn't solve anything though, so I started trying other things. From this point onwards, I can't remember exactly what happened. I tried a combination of:
- upgrading again (eventually ending at 12.10)
- blacklisting as per here: [http://ubuntuforums.org/showthread.php?t=1617290](http://ubuntuforums.org/showthread.php?t=1617290)
and other stuff
- Editing other files
- All sorts of commands
I've noticed several things:
- at some point my wireless device has changed from wlan0 to ra0
- my wireless card seems to have changed from RT2860 to RT2790. I've seen this come up elsewhere: [http://askubuntu.com/questions/125607/ralink-rt2790-or-maybe-a-rt2860-detected-as-two-different-chipsets-cant-con](http://askubuntu.com/questions/125607/ralink-rt2790-or-maybe-a-rt2860-detected-as-two-different-chipsets-cant-con)
- Once, in the log-in screen after restarting, I was prompted for a password for my WiFi network (it knew which one to connect to). No matter how many times I entered it, it would ask again. Just like my problem after originally installing Ubuntu.
I've also had other troubles:
- In Network Manager, I couldn't see the wireless section, to even go and try to connect to a WiFi network. I fixed this by doing: ```
rfkill unblock all
```

Right now, I'm stuck again at not being able to see the wireless section in Network Manager. And ```
rfkill unblock all
``` isn't doing anything. I believe I have the Ralink driver installed as described in the first link above.

Here's some useful (hopefully) output. Let me know if there is anything else that I should post:

```
lspci | grep link
02:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:ed:ca:08  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:feed:ca08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5236415 (5.2 MB)  TX bytes:2011958 (2.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139986 (139.9 KB)  TX bytes:139986 (139.9 KB)

ra0       Link encap:Ethernet  HWaddr 00:17:c4:98:35:90  
          inet6 addr: fe80::217:c4ff:fe98:3590/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

```

```
sudo lshw -C network
  *-network               
       description: Network controller
       product: RT2790 Wireless 802.11n 1T/2R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rt2860 latency=0
       resources: irq:16 memory:d8100000-d810ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 00:23:8b:ed:ca:08
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:45 ioport:1000(size=256) memory:d5004000-d5004fff memory:d5000000-d5003fff memory:d5010000-d501ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:17:c4:98:35:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 multicast=yes wireless=Ralink STA

```

Any help would be much appreciated. At this point, the next thing I'm thinking about trying is to install 12.10 from scratch, and then try to install the Ralink driver as in the first link above again.

Thanks

---

