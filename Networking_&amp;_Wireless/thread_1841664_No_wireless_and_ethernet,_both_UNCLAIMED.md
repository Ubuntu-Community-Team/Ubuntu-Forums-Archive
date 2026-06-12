---
title: "No wireless and ethernet, both UNCLAIMED"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by bolenjx on 2011-09-09
Laptop Info:
Ubuntu 10.04 LTS 64-bit dual boot w/ Windows 7 Pro 64-bit
Lenovo Thinkpad T520i 

Results from lspci:
```
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
03:00.0 Network Controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
```

lspci -nn:
```
00:19.0 Ethernet Controller [0200]: Intel Corporation Device [8086:1502] (rev 04)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
```

ifconfig:
only lo, no eth or wlan

iwconfig:
```
lo no wireless extensions.
```

lsmod | grep "wlan":
no results.

iwlist scan:
```
lo Interface doesn't support scanning.
```

sudo lshw -C network:
*-network UNCLAIMED (intel)
*-network UNCLAIMED (realtek)

Basically, I did a fresh install of both Windows 7 and Ubuntu once I got the laptop. Windows 7 is working perfectly but unfortunately, can't say the same for Ubuntu. I've also tried resolving the UNCLAIMED problems by following this guide: [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper) but there's no way to install ndisgtk since BOTH ethernet and wireless are broken. Also tried that thing with the CDROM but software sources just keep telling me that it can't mount the CD although I'm 100% sure it's mounted as mount told me so.

Appreciate any help on this.

---

### Post by bolenjx on 2011-09-10
Ok, after trying out everything possible under the moon last night, I just wiped my Ubuntu and installed 11.04 instead. 

Wireless works BUT very unstable. Every few minutes, sometimes seconds, the connection would just drop and I have to reconnect to make it work. Connection itself is also slow and very random.

lshw -C network:
```
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:da:b4:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-11-generic firmware=N/A ip=192.168.1.75 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:5000(size=256) memory:f2500000-f2503fff
```

lspci:
```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

rfkill list:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by nm_geo on 2011-09-10
Welcome to the forum.

First you really need to 

```
sudo apt-get update && sudo apt-get upgrade
```

That one may take some time to get your Natty up to date.

Let's try a few more diagnostic commands..

```
lsmod
```

That one tells us the loaded drivers and modules 

```
modinfo e100e | grep 1502

```

That one is looking for the driver that should work with your ethernet.

---

### Post by Pariah819 on 2011-09-10
I would suggest that you follow the driver installation provided by [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") in the post below...

[http://ubuntuforums.org/showpost.php?p=11102146&postcount=6](http://ubuntuforums.org/showpost.php?p=11102146&postcount=6)

---

