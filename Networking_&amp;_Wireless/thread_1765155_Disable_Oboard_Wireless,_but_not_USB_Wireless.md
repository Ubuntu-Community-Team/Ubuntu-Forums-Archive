---
title: "Disable Oboard Wireless, but not USB Wireless"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by Lucradia on 2011-05-22
lshw -C network:
```
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:f0:6d:04:1b:20
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:40:32:e8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan1
       serial: 00:26:5a:6a:df:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 ip=192.168.0.103 link=yes multicast=yes wireless=IEEE 802.11bgn
```

I want to disable the first wireless adapter listed here, but not the last one. However, pressing the Wireless LAN disable button disables both the onboard and USB Wireless LAN. Disabling it via the BIOS has the same effect. The PCI Wireless adapter has horrid coverage in comparison to the USB, so I must use the USB one.

---

### Post by chili555 on 2011-05-22
> The PCI Wireless adapter has horrid coverage I wonder if we can fix it. Please post:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Lucradia on 2011-05-22
lsmod output from above:

```
rt2870sta             410104  0 
rt2860sta             494649  0 
rt2800usb              17907  0 
rt2800pci              18159  0 
rt2800lib              43824  2 rt2800usb,rt2800pci
crc_ccitt              12595  3 rt2870sta,rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  5 rt2800usb,rt2800pci,rt2800lib,rt2x00pci,rt2x00usb
mac80211              257001  4 rt2800lib,rt2x00pci,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
```

---

### Post by chili555 on 2011-05-22
Man, that is a pile-o-drivers for just one little wireless card! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines at the end:```
blacklist rt2800pci
blacklist rt2x00pci
```Proofread carefully, save and close gedit. Remove the USB device and reboot. How is the built-in working now?

---

### Post by Lucradia on 2011-05-22
Well, it detects the majority of networks now, but now it won't connect to my WPA2 Router.

---

### Post by josephmills on 2011-05-22
hi there I think that chili is off brewing some coffee have you tried to reset the router after blacklisting?

---

### Post by Lucradia on 2011-05-23
> **josephmills said:**
> hi there I think that chili is off brewing some coffee have you tried to reset the router after blacklisting?

Yes, and it still doesn't work. I put the SSID to Visible this time, and it still doesn't want to connect.

But even if that was the problem, I wouldn't be able to use my netbook at my library, as their network is hidden.

---

### Post by chili555 on 2011-05-23
Add rt2860sta to your blacklist file and the on-board will be disabled.

---

### Post by Lucradia on 2011-05-23
Thanks, but now the USB WLAN Device doesn't want to connect to my WPA2-Personal (AES Only) network.

---

### Post by Lucradia on 2011-05-23
I also just tried installing **wicd**, but it said "rename failed" so it won't start, ever.

---

### Post by jawilljr on 2011-05-23
> **Lucradia said:**
> I also just tried installing **wicd**, but it said "rename failed" so it won't start, ever.

I take it you are using Natty...if you are then you need to type this:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

The logoff and relogin.

BTW if you are going to use WICD, I hope you removed network-manager.

Jerry

---

### Post by Lucradia on 2011-05-23
> **jawilljr said:**
> BTW if you are going to use WICD, I hope you removed network-manager.

I did, right before installing wicd.

---

### Post by Lucradia on 2011-05-23
Thanks that worked, and I think I know why gnome / network manager was failing to connect.

See, my router only has "Pre-shared Key" and no passphrase setting, I'm guessing network-manager was assuming my pre-shared key was a passphrase, and wasn't connecting due to that.

wicd has fixed that issue now, since wicd allows me to change to preshared key and passphrase separate. Also, the router would auto-scan for channels that are used the least, and would change its channel, this may not have played well with gnome.

Internal wireless now works like a champ.

---

