---
title: "slow after reboot?"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by thirdI on 2009-08-14
First-time Linux user. After installing 9.04 and the b43legacy driver, my wireless connection was great (avg.~200kb/s, as usual). However, when I installed updates through Update Manager and rebooted, there was a huge difference in the connection speed (avg.~15-20kb/s):confused:. I'm no good at interpreting the output from the terminal so if anyone can be of assisstance, here you go:
```

PCI
Belkin
F5D7000 
v7000
BCM4306





user@cpu:~$ lspci -v
01:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
    Subsystem: Belkin Device 7000
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at fe9fc000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

user@cpu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11bg

user@cpu:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:0  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe92:9b36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56582344 (56.5 MB)  TX bytes:3457916 (3.4 MB)

user@cpu:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"PN3V7"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=50/100  Signal level:-76 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Almost forgot...it's running on a Dell Dimension 2400 (she's been good to me for many years...)

---

### Post by thirdI on 2009-08-19
I was just installing the new updates and noticed that the download speed was around 115kb/s. After rebooting, I tried downloading a file using FireFox and the download speed dropped again. Can someone please give me just a slight idea on what's going on with my wireless connection?

---

