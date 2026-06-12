---
title: "Cannot detect wireless networks on Dell D620"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by kn4hh on 2009-07-14
I am running Ubuntu 9.04 on a USB memory stick with my Dell D620 laptop.  Ubuntu detects the network hardware on the pc however it will not detect wireless networks present.  When I try to manually detect the wireless network, all the options are grey'd out.  I have networking and wireless checked.  I booted the D620 from the HD with Windows XP and the wireless network is immediately detected.

Any assistance would be greatly appreciated.

Bob Watson

---

### Post by superprash2003 on 2009-07-14
post output of 
1)lshw -C network
2)iwconfig

---

### Post by kn4hh on 2009-07-21
ubuntu@ubuntu:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:3a:6d:66
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5752-v3.19 ip=10.0.38.99 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:84:45:ad
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 4a:71:e3:61:09:7b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ubuntu@ubuntu:~$ 

wireless and wired network detected OK under XP.  Tried Fn + F2 to enable wireless. No response.

Bob

---

