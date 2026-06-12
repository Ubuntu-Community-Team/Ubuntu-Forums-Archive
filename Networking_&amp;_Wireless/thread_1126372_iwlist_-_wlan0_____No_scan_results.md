---
title: "iwlist - wlan0     No scan results"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by vnccrl on 2009-04-15
Hi All,

I am a newbie in Linux, I am not able to get my new D-Link DWL-G510 wireless card to work. I'll try to report problem with as much information as possible, please ask if you need any other info.

```
lspci -v

[...]
00:0d.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Subsystem: D-Link System Inc Device 3c09
        Flags: bus master, slow devsel, latency 32, IRQ 17
        Memory at cfff0000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
        Kernel driver in use: rt61pci
        Kernel modules: rt61pci
[...]

------------------------------------------------------------------

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

-------------------------------------------------------------------

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=13 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

------------------------------------------------------------------

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

-------------------------------------------------------------------
```

I have to say I haven't installed any drivers, I have been told it was working out of the box, I suspect I don't need to install drivers because it has been recognized but why it is not detecting any wireless network? There are at least 2 here, 1 is mine and works fine with a Windows laptop.

Any help will be deeply apreciated.

---

### Post by vnccrl on 2009-04-15
Should I be looking at how to install drivers? Can someone point me to the right direction please?

---

### Post by kerry_s on 2009-04-15
```
sudo iwlist wlan0 scan
```
```
sudo iwconfig wlan0 essid any
```
```
sudo dhclient wlan0
```

but why do you need to do it manually, the card is detected, looks like it works, you should just be able to left click the network applet and select your preferred connection.

you might also need this one:
```
sudo ifconfig wlan0 up
```

---

### Post by vnccrl on 2009-04-16
Mistery solved, I leave solution for future reference. I notice that pci card wasn't plugging into the motherboard perfectly so I tried to remove it and insert it in a different slot. After that scan started working.

---

