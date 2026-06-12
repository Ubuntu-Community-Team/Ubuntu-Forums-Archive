---
title: "wireless adapter disabled, can't enable it"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by pop_ianosd on 2011-08-24
I've got this problem on my Amilo Li 1718, this is the output of sudo lshw -C network:
```

  *-network DISABLED      
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:fd:50:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:8f:2b:99
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.159 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:a000(size=256) memory:c0200000-c02000ff

```I have tried the solution at:
[http://ubuntuforums.org/showthread.php?t=1180170](http://ubuntuforums.org/showthread.php?t=1180170)   but it would freeze my terminal after the "make" command;
When I click the networking icon on the top bar, it says "wireless is disabled", even after I check "enable wireless";

---

### Post by praseodym on 2011-08-24
Hello,

for [COLOR="Red"]F[/COLOR]ujitsu [COLOR="Red"]S[/COLOR]iemens [COLOR="Red"]Am[/COLOR]ilo you can try a kernel module:

```
sudo modprobe -v fsam7400 radio=1
sudo rfkill unblock all
sudo service network-manager restart
```
Now test your wireless and check buttons, etc.

---

### Post by pop_ianosd on 2011-08-24
wohoooho, it really works, thank you very much!

---

### Post by rubenba on 2013-04-01
Thank you Praseodym! It worked for me too so my wireless adaptor found the router signal. However, it tries to connect and it doesn't connect (and ends up asking me the password again). I am sure the wifi is working as I can connect with my smartphone. Is there anything I can do? Any troubleshooting guide? 

Thanks

PS: Now I am using a wired connection, but only available until wednesday! :confused:

Ruben

---

### Post by xianbei on 2013-04-01
Hmm... you can try cycling the adaptor up and down

ifconfig wlan0 down
ifconfig wlan0 up

(you'll need the sudo)

---

