---
title: "RT2500 can't connect to network"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by tupfzom on 2013-04-25
I've a RT2500 PCI card that used to work in Natty, but stopped to do so after an upgrade to Oneiric.  I thought that the upgrade might have broken something (there were other problems as well), so I did no more upgrades and now did a fresh Raring install, which shows the same problem as Oneiric.

The card works perfectly when booting to Windows.

dmesg outputs a lot of lines like this:

```
[ 3195.112536] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 3195.112536] Please file bug report to http://rt2x00.serialmonkey.com.

```

lshw says the following:

```
$ LANG=C sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2500 Wireless 802.11bg
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 01
       serial: 00:11:09:f8:d3:a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.8.0-19-generic firmware=N/A latency=32 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fdefc000-fdefdfff

```

Any advice on trouble shooting and fixing?

---

### Post by tupfzom on 2013-04-26
Some more info that might hopefully help in addressing the problem:

```
$ lsmod | grep rt2
rt2500pci              18467  0 
rt2x00pci              14151  1 rt2500pci
rt2x00lib              48522  2 rt2x00pci,rt2500pci
mac80211              526519  2 rt2x00lib,rt2x00pci
cfg80211              436177  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2500pci
```

And some more lines from dmesg:

```
[   18.360585] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.361175] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.365840] forcedeth 0000:00:08.0: irq 42 for MSI/MSI-X
[   18.365875] forcedeth 0000:00:08.0 rename2: MSI enabled
[   18.366091] forcedeth 0000:00:08.0 rename2: no link during initialization
[   18.366510] IPv6: ADDRCONF(NETDEV_UP): rename2: link is not ready
[   18.367201] IPv6: ADDRCONF(NETDEV_UP): rename2: link is not ready
[   18.370807] forcedeth 0000:00:09.0: irq 43 for MSI/MSI-X
[   18.370842] forcedeth 0000:00:09.0 eth1: MSI enabled
[   18.371058] forcedeth 0000:00:09.0 eth1: no link during initialization
[   18.371475] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.372377] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.622295] type=1400 audit(1366955440.364:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1057 comm="apparmor_parser"
[   18.622811] type=1400 audit(1366955440.364:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1057 comm="apparmor_parser"
[  305.308616] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  305.309265] wlan0: Selected IBSS BSSID be:6e:cd:25:16:a2 based on configured SSID
[  305.344810] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  336.096059] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  351.572583] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  351.612074] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[  351.612074] Please file bug report to http://rt2x00.serialmonkey.com.
[  352.687728] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[  352.687728] Please file bug report to http://rt2x00.serialmonkey.com.
[  356.040860] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[  356.040860] Please file bug report to http://rt2x00.serialmonkey.com.
```

The kernel version:
```
$ uname -r
3.8.0-19-generic
```

---

### Post by tupfzom on 2013-04-26
It seems that one more bit of info is essential to the problem:  I'm trying to use the card in ad-hoc mode (which used to work in Natty) because my main computer is sharing internet via Wifi.

---

### Post by tupfzom on 2013-04-28
Another potential possibility of solving the problem:  Make my main machine work as an AP, as the problem might indeed be ad-hoc mode.  The main machine has the following card:

```
Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

According to the [Community Wiki's MasterMode article]("https://help.ubuntu.com/community/WifiDocs/MasterMode#Intel_PRO.2BAC8-Wireless_.28ipwXXXX.29_series"), it should work, but a ```
iw phy phy0 info
``` does not list master mode, only the following:

```
	Supported interface modes:
		 * IBSS
		 * managed
		 * monitor
```

I have no idea whether master mode is not listed because of hardware or driver restrictions, though, and I have no idea whether it would be harder to get master mode working with this card or ad-hoc mode with the RT2500.  To be investigated...

---

