---
title: "Wifi hard blocked on Linux Mint 19.2"
date: 2020-01-29
forum: MINT
---

### Post by poncha2 on 2020-01-29
Hello. I have notebook HP with Linux Mint 19.2 kernel 4.15.0.74-generic. My wifi used to work, but now it is hard blocked. Wifi button are always on, don't depends on switch it. There aren't any settings about wireless in my bios.

```
$ sudo rfkill unblock all 
``` no effect
```

$  rfkill list0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
```

$ iwconfig
wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
tun0      no wireless extensions.
eno1      no wireless extensions.
lo        no wireless extensions.

```
```

$ sudo lshw -c network
  *-network DISABLED        
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlo1
       version: 00
       serial: 9c:2a:70:3a:e8:41
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.15.0-74-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:63510000-6351ffff
  *-network
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eno1
       version: 05
       serial: 38:ea:a7:e5:b9:a5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.89 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:3000(size=256) memory:63404000-63404fff memory:63400000-63403fff


```
```

$ dmesg | grep -e wlo1 -e rt2
[   85.490294] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   85.500397] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   85.644679] rt2800pci 0000:07:00.0 wlo1: renamed from wlan0
[   87.366040] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready

```

It's my work computer. Help me, please, restore it!

---

### Post by wildmanne39 on 2020-01-29
*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by poncha2 on 2020-01-29
when I try to switch on wifi by button, I get state of soft blocked
turn off - 
```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```
turn on - 
```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by poncha2 on 2020-01-29
> **wildmanne39 said:**
> *Thread moved to **MINT a more appropriate sub-forum**.*
I don't think so. I consider that problem isn't with my system. Probably firmware or drivers

---

### Post by CelticWarrior on 2020-01-30
> **poncha2 said:**
> I don't think so. I consider that problem isn't with my system. Probably firmware or drivers

If you're using Mint this is your one and only section.

Now please read and follow instructions at [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) so we can see the hardware, drivers, settings, etc. being used.

---

