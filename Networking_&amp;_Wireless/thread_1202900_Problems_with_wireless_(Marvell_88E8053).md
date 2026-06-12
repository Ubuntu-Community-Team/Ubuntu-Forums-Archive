---
title: "Problems with wireless (Marvell 88E8053)"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by vbCrLf on 2009-07-02
Hello,
My wireless connection is really slow (always on low signal - 14%), sometimes disconnect (seems like when heavily used, but not sure), and I have to disable and re-enable networking to reconnect.
I had Ubuntu 8.10 32-bit before, and it began behaving like that until it completely stopped working (couldn't connect at all). Tried ndsiwrapper, barely worked - and after some time stopped working completely as well. Had to format Ubuntu...
I formatted and installed Ubuntu 9.04 64-bit (in which I'm writing this message in) and I saw I still I have the same problem.
I had another Linux disto installed - Zenwalk, and I had low signal in it as well.

lspci:
```
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)

```

iwconfig wlan0:
```
wlan0     IEEE 802.11bg  ESSID:"Lahav_Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:63:41:89:CC   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=14/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 20
       serial: 00:1a:92:9e:12:6e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 20
       serial: 00:1a:92:9e:05:23
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0f:74:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.10 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:43:c2:79:67:7a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Kernel version is 2.6.28-11-generic x86_64.
These problems makes Ubuntu pretty much unusable... :(

Thanks,
Ori.

---

### Post by vbCrLf on 2009-07-09
I've tried ndiswrapper but got the same results.

Ori.

---

### Post by RavanH on 2009-07-12
I have no idea about the chipset your card is using but it might be worth to try the solution I found for a similar problem with a RT2500 based card. Read it on [http://ubuntuforums.org/showthread.php?p=7605785](http://ubuntuforums.org/showthread.php?p=7605785) and let me know if it works for you :)

---

### Post by vbCrLf on 2009-07-13
Thank you Raven!
The signal is still low, but the connection seems to work faster, and did not disconnect at all. I hope it will continue to work well. Thanks! :)

Ori.

---

### Post by RavanH on 2009-07-20
> **vbCrLf said:**
> Thank you Raven!
The signal is still low, but the connection seems to work faster, and did not disconnect at all. I hope it will continue to work well. Thanks! :)

Ori.

Did you try with the option 'Use dBm to measure signal strength' under Preferences in the Wicd Manager? In my case, with that option checked, the signal strenght is indicated as higher than originally. 

Weird, but it helps :)

---

### Post by vbCrLf on 2009-07-20
> **RavanH said:**
> Did you try with the option 'Use dBm to measure signal strength' under Preferences in the Wicd Manager? In my case, with that option checked, the signal strenght is indicated as higher than originally. 

Weird, but it helps :)
It does make it green, although it seems it doesn't really change anything - except the icon ;)

---

### Post by RavanH on 2009-07-27
> **vbCrLf said:**
> It does make it green, although it seems it doesn't really change anything - except the icon ;)

Well, as long as you like green -- and do not loose connection to it all the time -- you're fine, right? :D

---

