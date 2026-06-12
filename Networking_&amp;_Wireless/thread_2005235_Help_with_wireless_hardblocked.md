---
title: "Help with wireless hardblocked"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2012-06-17
Hi  I have just swap my wireless card from intel pro, to Atheros AR928X Wireless Network Adapter.
I now cant get wireless to switch on (tried switch at front)
Rfkill list ```
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```lshw -C network
```
*-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan1
       version: 01
       serial: 0c:60:76:22:6d:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d8000000-d800ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:28:3e:a9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.42.43.11 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:4000(size=256) memory:da000000-da000fff memory:d4000000-d400ffff

```iwconfig
```
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```sudo ifconfig wlan1 up```
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

I can get other info if required

---

### Post by spiky001 on 2012-09-22
Bump still trying

---

### Post by Iowan on 2012-09-22
Moved to Networking & Wireless

---

### Post by jack454 on 2012-09-22
Try ```
rfkill unblock all
```

---

### Post by spiky001 on 2012-09-22
That returns  ```
rfkill list 0: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: yes
```

---

### Post by jack454 on 2012-09-22
Hard blocked normally means a physical switch is turned off. If there isn't a switch I'm not sure what then try ```
rfkill unblock 0
```

---

### Post by kimberlite on 2012-09-22
> **jack454 said:**
> Hard blocked normally means a physical switch is turned off.
+1 & Also check your BIOS for any wireless option...

---

### Post by spiky001 on 2012-09-22
Hi  Ok there are no settings in the bios I have checked, +1 on the physical switch not on. I have tried it both ways and using the fn+f8 key for wireless. I could really do with some more help here.

---

### Post by jack454 on 2012-09-22
Try
```
rfkill unblock 0
```
If that doesn't work do the switch and again try ```
rfkill unblock 0
```
If this doesn't work you will have to wait for someone with more knowledge than I have.

---

### Post by kimberlite on 2012-09-22
I found a similar thread [here]("http://ubuntuforums.org/showthread.php?t=1920757"). That problem was solved by switching on physically the card. 
Another thread [here ]("http://ubuntuforums.org/showthread.php?p=11484748#post11484748")came out with a different solution for a notebook. By the way is it a notebook or PC?

---

### Post by spiky001 on 2012-09-22
Thks tried that every different way still same result.

---

