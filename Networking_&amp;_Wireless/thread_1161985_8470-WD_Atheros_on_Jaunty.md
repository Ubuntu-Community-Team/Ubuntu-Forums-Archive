---
title: "8470-WD Atheros on Jaunty"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by spikoley on 2009-05-17
I am trying to get my Proxim 8470-WD Atheros wireless card to work on a Jaunty server.  The server does not have an internet connection, so I need to use a USB thumb drive to get the .debs on it.  What .debs do I need to use?  I tried madwifi-tools and it did not work.  Any ideas?  The last couple of version the card has been recognized as wlan0 instead of ath0.  That has confused me on what packages I need to get this working.

---

### Post by t0mppa on 2009-05-17
The ath5k, which comes by default on the non-server edition of Jaunty (might be the same with the server one) uses wifi0 for your wireless, where as the older (original) Madwifi, ath_pci, uses ath0. The newest ath5k versions should be superior to the ath_pci, so I'd recommend trying that first.

If you need more specified help, perform the following actions and post your results here to give the rest of us an idea of what's going on. To troubleshoot the current state of the interface, run 'lshw -C network' from the terminal and you'll find out which Atheros chip you card has as well as if it's associated with any driver at the moment. Also run 'lsmod | grep ath' to find out which Madwifi modules are currently loaded to kernel. And a third thing is to go through the blacklist*.conf files in /etc/modprobe.d/ to find out if any ath related modules are blacklisted (tagged as "don't run these" for the kernel).

---

### Post by spikoley on 2009-05-17
I still cannot get it working.  Below are the results from the requested commands.

lsmod | grep ath - returned no results.

blacklist-ath_pci.conf
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
```

lshw -C network
```
  *-network DISABLED
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:20:a6:51:84:b8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
```

dmesg | grep ath
```
[    5.334923] device-mapper: multipath: version 1.0.5 loaded
[    5.334976] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.347142] ath5k_pci 0000:02:00.0: enabling device (0000 -> 0002)
[   15.347225] ath5k_pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   15.347846] ath5k_pci 0000:02:00.0: registered as 'phy0'
[   15.596420] ath5k phy0: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
[   15.596489] ath5k phy0: RF5111 5GHz radio found (0x17)
[   15.596537] ath5k phy0: RF2111 2GHz radio found (0x23)
```

---

### Post by t0mppa on 2009-05-18
Well, to get the latest version of ath5k, you need to download and install the [compat-wireless]("http://linuxwireless.org/en/users/Download") package.

Lsmod didn't find anything with ath on it? Try just the plain lsmod, without the grep part, to see if there was a typo or something. That's a very odd result, since lshw claims that ath5k_pci is the driver associated with the device. If it's still not shown, you can try running 'modprobe ath5k_pci' to load up the module and check if that made a difference.

Also, are you sure your wireless device is turned on? The disabled message on lshw often means that the device is off. And sometimes it's a glitch fixed by a reboot.

---

### Post by motopsyko32 on 2009-07-11
i am having the same issue with a similar card.  the proxim 8480

here is my output:

administrator@laptop:~$ lsmod | grep ath
ath5k                 107008  0 
mac80211              217464  1 ath5k
led_class              12036  1 ath5k
cfg80211               38288  2 ath5k,mac80211

administrator@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:35:a6:ca
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.5.121 latency=32 module=ssb multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:20:a6:4c:3a:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:12:a1:5e:84:01
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
administrator@laptop:~$ dmesg | grep ath
[    2.597815] device-mapper: multipath: version 1.0.5 loaded
[    2.597820] device-mapper: multipath round-robin: version 1.0.0 loaded
[   17.514845] ath5k_pci 0000:03:00.0: enabling device (0000 -> 0002)
[   17.514865] ath5k_pci 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.515053] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   17.626182] ath5k phy0: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
[   17.626188] ath5k phy0: RF5111 5GHz radio found (0x17)
[   17.626192] ath5k phy0: RF2111 2GHz radio found (0x23)
[   80.154126] ath5k phy0: noise floor calibration timeout (2452MHz)
administrator@laptop:~$

---

### Post by t0mppa on 2009-07-12
> **motopsyko32 said:**
> i am having the same issue with a similar card.  the proxim 8480

Same issue being a server without an Internet connection and not knowing which .debs you need to update it?

From the output you listed, the wireless interface seems to be working fine though.

---

