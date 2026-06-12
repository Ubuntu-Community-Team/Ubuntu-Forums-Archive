---
title: "Wired network ok but wireless not working"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by shodan_uk on 2009-02-22
Hi all,

First of all, can I just say I'm very new to Ubuntu and Linux in general. I've had a fair amount of experience with wireless networks on windows though.

Up until today, I had both wired and wireless networks working fine in Ubuntu on my Toshiba laptop. Then today, I bought a new router and am now having trouble with the wireless on my laptop. To clarify: the wired network is fine and the router is fine as my girls Windows Vista based laptop connects just fine.

I can't seem to get Ubuntu to see any wireless networks although there are several available (I can see them via my GF's laptop). 

I used to be able to select the wireless network from a list in the NetworkManager applet on the panel at the top of the screen although now, the words "Wireless Networks" are greyed and out and there is a message that read "device is unmanaged".

NB. I am in terrible fiddler and it's very likely that I've turned something off, uninstalled a vital package or installed a something that's causing an issue and the new router may be a total red herring!

I don't really know what the following commands mean but I've seen their output asked for in similar threads in here so am going to post them in the hope that they'll be useful to someone:

"sudo iwlist scanning"
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

```

"iwconfig"
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

"ifconfig"
```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:87:df:11  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe87:df11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4458974 (4.4 MB)  TX bytes:399910 (399.9 KB)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

```

"sudo lshw -C network"
```
     
description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:87:df:11
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.6 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:69:3e:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:2f:09:ab:43:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Apologies if any of that is unnecessary - just hoping it'll improve my chances of getting a solution!

Thanks in advance.

Cheers,
Terry

---

### Post by Joe2Shoe on 2009-02-22
If you changed nothing on the Ubuntu end, the problem is with the router.
Enter the wireless router's setup program and turn on B/G and N (if available).
Possibly the router is not set on Auto to broadcast in B/G/N.
Did you apply the same SSID (network name) and password to the new wireless router in the Setup Program as you did in the old one?
If you mistyped anything, that will cause the problem.

1. Reboot the wireless router; unplug it for 5 minutes, then plug it back up.
2. Reboot the laptop.

Good luck.

---

### Post by x1101 on 2009-02-22
from the look of your output it seems like your wireless card has just been disabled.

if you see this 
wlan0     IEEE 802.11bg  ESSID:""  
from running iwconfig

but don't see the interface (wlan0) listed when running ifconfig, the next thing you should do is run *sudo ifconfig wlan0 up*
this will bring your network interface *wlan0* online.

---

### Post by shodan_uk on 2009-02-24
Thanks for replying, guys.

I switched the laptop on the next day and all was working again... very odd because I know I rebooted several times when it wasn't working.

I'll keep an eye on it and see what happens.

Thanks again for taking the time to reply!

Cheers,
Terry

---

