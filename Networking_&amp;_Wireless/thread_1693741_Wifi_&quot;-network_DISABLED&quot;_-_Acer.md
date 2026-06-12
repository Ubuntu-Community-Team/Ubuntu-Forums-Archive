---
title: "Wifi: &quot;*-network DISABLED&quot; - Acer"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by vbSteve on 2011-02-23
Hi,


I can't get my wireless network to work. I've tried many things now, but I just can't enable it.

I have an Acer Aspire 7551 notebook with an on-board AR928X PCI-Express Wifi Adaptor.


Here's my check list:

- Wifi LED is OFF
- Key combination to enable hardware (Fn + F3): not working.
- Logical name:: wlan0
- Bus: pci@0000:06:00.0
- Command: lspci
```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```
- Command: dmesg |grep -e ath -e wlan
```
[    0.746442] device-mapper: multipath: version 1.1.1 loaded
[    0.746445] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.417509] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.417519] ath9k 0000:06:00.0: setting latency timer to 64
[    7.845898] ath: EEPROM regdomain: 0x65
[    7.845900] ath: EEPROM indicates we should expect a direct regpair map
[    7.845904] ath: Country alpha2 being used: 00
[    7.845905] ath: Regpair used: 0x65
[    7.915157] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    7.915675] Registered led device: ath9k-phy0::radio
[    7.915692] Registered led device: ath9k-phy0::assoc
[    7.915705] Registered led device: ath9k-phy0::tx
[    7.915719] Registered led device: ath9k-phy0::rx
```
- Command: lshw -C Network
```
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:bb:ee:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-25-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d030ffff
```

Release Info:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Any one has a solution for this?
Thanks.

---

### Post by vbSteve on 2011-02-23
** Solved.

Right clicked the network icon on the top bar, and it gave me an option to enable the wifi. It works now.

You have to be real careful though. The option to enable the wifi may be grayed out, If it is use FN+F3 once and right click the icon again. (Bug?)

---

### Post by robbiemacg on 2011-02-23
Hi [vbSteve]("http://ubuntuforums.org/member.php?u=1163912"),
You're clearly working hard to try to find a solution, and you seem to have a sense of where/how to look for the information that might help you diagnose this problem.
I have a couple of quick questions that might or might not help move things forward:

- You seem to be working with a new installation. Is the system/machine new to you? Have you run other distros on it previously?

- Have you updated or changed your BIOS recently?

- What kind of information does **iwconfig** yield? Anything in addition to the facts previously stated?

- Finally (and promise I'm not being a jerk) are there any physical switches embedded in your machine's case that might have been banged, pressed, or clicked inadvertently in transit recently?

Let's try to get this problem solved.

---

### Post by robbiemacg on 2011-02-23
Could always just be that I guess. Lol.
I'm glad you're up, chum!

---

### Post by vbSteve on 2011-02-23
Thanks, robbie :)

---

