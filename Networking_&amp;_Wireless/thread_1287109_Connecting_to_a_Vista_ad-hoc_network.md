---
title: "Connecting to a Vista ad-hoc network"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by WindPower on 2009-10-09
Hi there,
I posted about this in this other thread[/url], but I am not using Karmic (yet) so I guess I should post here rather than in the Karmic testing forum. :)

Anyway, I'm trying to connect to an ad-hoc network created by another machine running Windows Vista. However, I can't see the network at all in the wireless network list. If I type in the connection info manually and try to connect anyway, nothing happens. I followed the instructions [in the wiki](https://help.ubuntu.com/community/WifiDocs/Adhoc), in [the thread I linked to](http://ubuntuforums.org/showthread.php?p=8079838), and on this [blog](http://haritkothari.wordpress.com/2007/12/11/ad-hoc-wireless-networking-with-ubuntu/), but none of them worked (all of these instructions are basically the same anyway, right?).
So here's what I did:
```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc
sudo iwconfig eth1 essid '<the Ad-hoc network's name>'
sudo ifconfig eth1 up
sudo dhclient eth1
```

The thing I did not do is to specify a WEP key, because the ad-hoc network doesn't have any protection. I also didn't specify a channel, because I don't know which channel it is on, and it's not visible in the wireless network list. I thought about using airodump-ng, but apparently it doesn't work on my wireless card:
```
$ sudo airmon-ng start eth1; sudo airodump-ng eth1


Found 6 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
3434    NetworkManager
3451    wpa_supplicant
3458    avahi-daemon
3459    avahi-daemon
4117    knetworkmanager
4309    dhclient
Process with PID 4309 (dhclient) is running on interface eth1


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode enabled)

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.
```


I am running Kubuntu 9.04 64-bit on a MacBook Pro 5,3, using knetworkmanager, and the restricted Broadcom wireless drivers.
```
$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)
```

---

