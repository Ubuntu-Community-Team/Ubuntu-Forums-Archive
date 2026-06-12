---
title: "No Wireless BCM4313"
date: 2012-09-30
forum: Networking &amp; Wireless
---

### Post by spikoley on 2012-09-30
I am unable to get my BCM4313 active.  Enable Wireless is grayed out under the network icon.  Right now, I am using the directions from [this site]("http://www.broadcom.com/support/802.11/linux_sta.php").  Any suggestions would be greatly appreciated.

```
lspci | grep 43
Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

```
lshw -C network
*-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:06:9a:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:f0600000-f0603fff

```

```
lsmod | grep wl
wl                   2442848  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
```

```
lsmod | grep lib80211
lib80211_crypt_tkip    17275  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
```

```
lsmod  | grep "b43\|ssb\|bcma\|wl"
wl                   2442848  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
```

```
sudo iwlist eth1 scan
eth1      Failed to read scan data : Invalid argument
```

---

### Post by spikoley on 2012-09-30
Got it working with *rfkill unblock all*.

```
:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

:~$ rfkill unblock all

:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

