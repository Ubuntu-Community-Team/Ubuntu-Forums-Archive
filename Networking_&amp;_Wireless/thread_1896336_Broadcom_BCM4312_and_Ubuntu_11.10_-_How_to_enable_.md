---
title: "Broadcom BCM4312 and Ubuntu 11.10 - How to enable channel 13?"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by lbracher on 2011-12-16
Hi there!

I have installed Ubuntu 11.10 and I have BCM4312 here. Unfortunately the AP's wifi channel is 13. It works at Windows, but when I boot ubuntu, it goes from channel 1 to 11. 

I downloaded the latest STA driver at Broadcom's site, I compiled and installed exactly as README.txt file tells me to do, but I don't see yet the channel 13. Do you know how to proceed to activate this channel?

Thank you!

```

# lspci -v
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 47-51-e1-ff-ff-ce-00-1f
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

```

# dmesg | egrep '(wl|ssb)'

[   19.261824] wl: module license 'unspecified' taints kernel.
[   19.280376] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.280392] wl 0000:0b:00.0: setting latency timer to 64


```

---

### Post by praseodym on 2011-12-16
Hi,

which country do you live?

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE #DE for Germany, replace it
```
Check:
```
iwlist chan
dmesg | grep country
```

---

### Post by lbracher on 2011-12-16
Hi praseodym! Thanks for your help!

Now I live in Italy.

The command you told me shows this:

```

# iw reg get
nl80211 not found.


```

I googled about nl80211 and I couldn't figure out what I need to do.

iwlist chan shows me the same 11 channels.
dmesg | grep country shows me nothing.

Any ideas?

Lucas.

---

### Post by praseodym on 2011-12-16
Try the native driver b43. Uninstall the STA and download the needed firmware:

```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
sudo modprobe -rfv wl
cd [COLOR="Red"]Foldername-of-STA-driver/[/COLOR]
make clean
make
sudo make uninstall
sudo modprobe -v b43
```
Check:
```
iwlist chan
sudo iwlist scan
dmesg | egrep 'b43|country'
```

---

### Post by lbracher on 2011-12-17
Hi!

I think it worked, since now I can see 14 channels with iwlist chan.

Unfortunately there's no wifi network here at channel 14, so I need to get back home to tell you if it worked.

```

# dmesg | egrep '(b43|country)'
[ 6283.175983] cfg80211: Calling CRDA for country: 97


```

Thank you! I will mark this as solved as soon as I arrive at home and get everything tested.

Bye!

Lucas.

---

### Post by lbracher on 2011-12-17
It works! Thank you!

---

