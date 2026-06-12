---
title: "Realtek rtl8187b install problems"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by blues2use on 2010-11-22
Running 10.10 2.6.35-22 and using my Ethernet connection to post.

I'm trying to enable my Trendnet USB wireless network adapter. Functions fine with XP and 7 (bought it today).

lsusb shows:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
B**us 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ndiswrapper -l shows:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
net8187b : driver installed
	device (0BDA:8189) present

I thought that this adapter was supported out of the box directly but I may be wrong. 

Not sure what I need to do now and how to proceed to get this wireless adapter enabled.

**Any / all suggestions will be most appreciated.**

**_Thanks_**

---

### Post by blues2use on 2010-11-22
> **blues2use said:**
> Running 10.10 2.6.35-22 and using my Ethernet connection to post.

I'm trying to enable my Trendnet USB wireless network adapter. Functions fine with XP and 7 (bought it today).

lsusb shows:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
B**us 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ndiswrapper -l shows:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
net8187b : driver installed
	device (0BDA:8189) present

I thought that this adapter was supported out of the box directly but I may be wrong. 

Not sure what I need to do now and how to proceed to get this wireless adapter enabled.

**Any / all suggestions will be most appreciated.**

**_Thanks_**

**I removed ndis-everything and the source build for the rtl8187b drivers**...the adapter **_now has the green LED lit_** (which is nice since it didn't do that before) but I still cannot use it to connect wirelessly.

lsusb reports the same info:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I had already checked for Additional Drivers (none) before making the original post. ndiswrapper and source building the drivers from Realtek provided no help.

I have no idea what to do next to enable this adapter. :-(

**_Help will be very much appreciated_**

---

### Post by blues2use on 2010-11-23
> **blues2use said:**
> **I removed ndis-everything and the source build for the rtl8187b drivers**...the adapter **_now has the green LED lit_** (which is nice since it didn't do that before) but I still cannot use it to connect wirelessly.

lsusb reports the same info:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I had already checked for Additional Drivers (none) before making the original post. ndiswrapper and source building the drivers from Realtek provided no help.

I have no idea what to do next to enable this adapter. :-(

**_Help will be very much appreciated_**

Searched the internet some more and finally found a suggestion (not a fix):

**_So far, the -only- solution I have found is to boot to 2.6-32-21 generic._** 

My wireless network is immediately recognized and I can connect automatically which is what I expected to do with 2.6.35.22 generic. 

Apparently, there is a problem in the kernel. For now, I will just make 21 the default boot and wait for further info and/or developments. Hopefully, a new kernel update in the future will have this fix included.

---

