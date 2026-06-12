---
title: "vaio and wlan problems"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by SonicDeathMonkey on 2009-06-04
I did not know if I was supposed to post this here or at "Hardware & Laptops" section. anyway.
I recently installed Ubuntu 9.04 in a Sony Vaio N31Z (before that I used Vista). Everything seemed fine, apart from the fact that it cannot seem to be able to find any wireless networks, not even mine when I put it a few right next to the router. The wlan light stays off. It's not my network's problem, there seemed to be no problems when i was using vista, I also tried another laptop and it had no problem finding and connecting to my network. When I use an ethernet cable connect to my modem/router everything is fine though. It's just the wireless thing that does not work.
I even activated the "Alternate Atheros madwifi driver" from System > Administration > Hardware Drivers but nothing changed.
I tried to look it up but I found nothing that could help me. I just hope it's not a fault of mine. I also hope that I won't have to get back to using Windows, I 've really enjoyed using Ubuntu so far.

---

### Post by t0mppa on 2009-06-04
Not to worry, it's likely just some configuration issue, not a hardware malfunction.

Just open up a terminal, run **lshw -C network** and post back with output.

---

### Post by SonicDeathMonkey on 2009-06-04
oh, thank you

this is what i got

> sonicdeathmonkey@sonicdeathmonkey-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:c7:3f:51
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:1f:cc:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:d3:82:75:67:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
sonicdeathmonkey@sonicdeathmonkey-laptop:~$ 
sonicdeathmonkey@sonicdeathmonkey-laptop:~$ 



---

### Post by t0mppa on 2009-06-04
Ok, the drivers get associated with the interface, but the interface is disabled. Are you sure you haven't just disabled it with a button on your laptop?

If you've already tried that out and it hasn't helped, try running **sudo ifconfig ath0 up**. Then run the lshw again and see if that DISABLED tag disappears.

---

### Post by SonicDeathMonkey on 2009-06-04
there is no "disabled" tag now but still no networks found, and still no wlan light on.

> sonicdeathmonkey@sonicdeathmonkey-laptop:~$ sudo ifconfig ath0 up
[sudo] password for sonicdeathmonkey: 
sonicdeathmonkey@sonicdeathmonkey-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:c7:3f:51
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:1f:cc:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:6f:5d:b7:59:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
sonicdeathmonkey@sonicdeathmonkey-laptop:~$ 



---

### Post by t0mppa on 2009-06-04
Ok. Then lets do some more troubleshooting. Here's some more commands to run from the terminal:

```
ifconfig
iwconfig
iwlist scan
```

---

### Post by SonicDeathMonkey on 2009-06-04
and this is what i got

> sonicdeathmonkey@sonicdeathmonkey-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:c7:3f:51  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fec7:3f51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6775 (6.7 KB)  TX bytes:8207 (8.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

sonicdeathmonkey@sonicdeathmonkey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

sonicdeathmonkey@sonicdeathmonkey-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

pan0      Interface doesn't support scanning.

sonicdeathmonkey@sonicdeathmonkey-laptop:~$ 



---

### Post by t0mppa on 2009-06-05
Hmm.. It doesn't show up on ifconfig, so it's still not quite operational. Let's see if the logs have something to tell us, so run **dmesg | grep ath** and check to see if the modules are properly loaded with **lsmod | grep ath**

---

