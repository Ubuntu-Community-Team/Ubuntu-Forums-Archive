---
title: "My Wireless Card Is Disabled."
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by harish kharel on 2013-04-17
harish@harish-ubuntu:~$ sudo lshw -C network[sudo] password for harish:   *-network UNCLAIMED            description: Network controller       product: AR9285 Wireless Network Adapter (PCI-Express)       vendor: Atheros Communications Inc.       physical id: 0       bus info: pci@0000:06:00.0       version: 01       width: 64 bits       clock: 33MHz       capabilities: pm msi pciexpress bus_master cap_list       configuration: latency=0       resources: memory:d9100000-d910ffff  *-network       description: Ethernet interface       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller       vendor: Realtek Semiconductor Co., Ltd.       physical id: 0       bus info: pci@0000:07:00.0       logical name: eth0       version: 02       serial: 88:ae:1d:2e:fb:b1       size: 100Mbit/s       capacity: 100Mbit/s       width: 64 bits       clock: 33MHz       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.10.71 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s       resources: irq:42 ioport:2000(size=256) memory:d5110000-d5110fff memory:d5100000-d510ffff memory:d5120000-d513ffffThe wireless card is mentioned as *-network UNCLAIMED. So I cannot use wireless. How to solve this issue

---

### Post by chili555 on 2013-04-17
Please try loading the correct driver:```
sudo modprobe ath9k
```Did that fix it? If so, let's get the driver to load automatically:```
sudo su
echo ath9k >> /etc/modules
exit
```If that didn't fix it, there must be some other reason it isn't working. Is the wireless switch set to enable wireless?```
rfkill list all
```Are there any informative messages in the logs?```
dmesg | grep ath
```

---

### Post by hammad506 on 2013-04-17
> **chili555 said:**
> Please try loading the correct driver:```
sudo modprobe ath9k
```Did that fix it? If so, let's get the driver to load automatically:```
sudo su
echo ath9k >> /etc/modules
exit
```If that didn't fix it, there must be some other reason it isn't working. Is the wireless switch set to enable wireless?```
rfkill list all
```Are there any informative messages in the logs?```
dmesg | grep ath
```

this is what i get
$ rfkill list all
Wireless LAN
    Soft blocked: no
    Hard blocked: yes
$ dmesg | grep ath
[   14.479331] type=1400 audit(1366220569.117:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=942 comm="apparmor_parser"
[   14.480091] type=1400 audit(1366220569.121:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=942 comm="apparmor_parser"

---

### Post by chili555 on 2013-04-17
> Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]That suggests that the switch or wireless key combination, something like Fn+F4, maybe, is switched to turn wireless off. Can you please find it and switch it on?

---

### Post by harish kharel on 2013-04-17
When I run the code sudo modprobe ath9k following error is displayed.WARNING: Error inserting ath9k_hw (/lib/modules/3.2.0-40-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Invalid argumentWARNING: Error inserting ath9k_common (/lib/modules/3.2.0-40-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Invalid argumentWARNING: Error inserting mac80211 (/lib/modules/3.2.0-40-generic/updates/net/mac80211/mac80211.ko): Invalid argumentFATAL: Error inserting ath9k (/lib/modules/3.2.0-40-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument

---

### Post by chili555 on 2013-04-18
> WARNING: Error inserting ath9k[COLOR="#FF0000"]_hw[/COLOR]What...??

Let's see:```
ls /etc/modprobe.d
```I suspect you have a malformed and not needed file here.

---

