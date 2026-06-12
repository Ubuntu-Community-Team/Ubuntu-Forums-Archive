---
title: "Wireless detects but wont connect"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by Sojurner on 2011-01-02
My wireless card in my Acer Aspire 7551G shows wireless networks in range but wont connect to any of them. I am running an Atheros AR928x Wireless network card (windows reports it as a AR5b93). Also as a side note, whenever i turn on my computer, my wireless is disabled. However not connecting is my primary problem.

sud rfkill list
```
sojurner@Sojurner-Laptop:~$ sudo rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


sudo lsmod | grep ath
```
sojurner@Sojurner-Laptop:~$ sudo lsmod | grep ath
ath9k                  89076  0 
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
led_class               2633  2 ath9k,acer_wmi

```


gksudo gedit /var/lib/NetworkManager/NetworkManger.state

-The above returns everything as enabled


sudo lshw -C network
```
 *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:18:d7:bf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0200000-d020ffff

```


If anyone can help me figure out how to fix this problem, i would greatly appreciate it.

---

### Post by perspectoff on 2011-01-02
Are you using Network Manager?

If so, join the thousands of people with the same problem.

I had the same problem for months as well, then uninstalled Network Manager and installed Wicd instead...

---

### Post by PatchesTheCaveman on 2011-01-02
Hi Sojurner!  If you noticed the output from rfkill, your wireless card is soft-blocked.

Run this command to unblock it:
```
sudo rfkill unblock 0
```

---

### Post by Sojurner on 2011-01-02
Both issue resolved..  Thanks alot

---

