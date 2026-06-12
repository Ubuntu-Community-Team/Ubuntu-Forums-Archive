---
title: "wireless problem in eeepc t91mt"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by roda on 2011-03-16
hi you guys, i have an huge issue with my new ubuntu 10.10 and that is wireless problem. Here are details:
After finishing install ubuntu 10.10 my wireless works well. just after install poulsbo driver for intel gma 500, i couldn't access wifi anymore. I clicked on the network icon, it say: "wireless is disable". I press f2 when it startup to enable wireless in bios, but the led signal of wireless turn off when the ubuntu screen appear. I also installed latest linux-backports-modules-wireless. it doesn't work. I tried all the combination of keys to enable it and i found nothing. 

This is the result when i put the code "sudo lshw -C network"
```
 *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:10:9a:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:40 memory:fbfc0000-fbffffff ioport:e880(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:36:ed:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-27-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbef0000-fbefffff
```


With "rfkill list" i have

```
0: eeepc-wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: eeepc-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```



and, with "sudo iwconfig" i have:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
```


I tried everything i could. The final thing i can come up with is to come back to win7. Please help me with this issue as i want no tissue. Thanks alot

---

### Post by jtjs on 2011-03-17
From [http://ubuntuforums.org/showthread.php?t=1595220&highlight=rfkill&page=5](http://ubuntuforums.org/showthread.php?t=1595220&highlight=rfkill&page=5)

> **Ozone77 said:**
> My wireless worked at first but after something (kernel update?) it only works if I run 

sudo rfkill unblock all

If this works for you, edit /etc/rc.local and add "rfkill unblock all" for a permanent workaround.

---

### Post by roda on 2011-03-19
This is funny. First, the wireless's LED was off, i can see the wireless part in "network taskbar" (like, eth1). After the code 
> sudo rfkill unblock all
the LED came back again but eth1 is gone.
An issue came with an issue gone, the pain be still remain.
Anyway, that was a process. Because with code "sudo rfkill list" i have this

> 0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: eeepc-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


the strange thing is the difference between the result of "sudo iwconfig"
BEFORE:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

AFTER:
> lo        no wireless extensions.

eth0      no wireless extensions.


i started to think this had come back to the driver problem.
However, May i have any further information? because i have no idea what to do from here. I ll do some google search while waiting. Thank you.

---

