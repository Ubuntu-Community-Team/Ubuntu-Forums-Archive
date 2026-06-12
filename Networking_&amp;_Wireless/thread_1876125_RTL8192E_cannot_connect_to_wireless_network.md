---
title: "RTL8192E cannot connect to wireless network"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2011-11-05
I followed the instructions in this post to install the linux driver for the Realtek RTL8192E [http://ubuntuforums.org/showpost.php?p=10087294&postcount=81](http://ubuntuforums.org/showpost.php?p=10087294&postcount=81)

After rebooting, the wireless card is still not working with network-manager. The nm-applet shows no available wireless networks. I tried manually typing in the SSID and passphrase, but that also did not work.

I'm not sure whether it's necessary, but I have already installed linux-firmware and linux-firmware-nonfree.

I'm using  2.6.38-8-generic on Ubuntu 11.04.

There is no (visible) RF switch on the laptop, but there is a Function key with the wifi logo. I tried pressing it but it didn't seem to do anything. **rfkill list** gives no output.

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

``````
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8152]
    Flags: bus master, fast devsel, latency 0, IRQ 5
    I/O ports at c800 [size=256]
    Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number a1-52-c4-fe-ff-d2-24-00
    Kernel modules: r8192e_pci

```The available modules:
```
/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8192e
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8192u
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/r8192e_pci.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko

```I believe r8192e_pci is the "correct" linux driver that I downloaded and built myself, but I'm no 100% sure.

---

### Post by kurt18947 on 2011-11-05
I know enough to be dangerous :tongue: and someone who knows more will be along soon I hope.  In the meantime, if you question whether or not the adapter is powered up it might be worth doing "rfkill list" in a terminal.  If your device shows hard blocked, it may indeed switched off somehow.  The function key switches usually work in Linux but not always, it depends on the machine.

---

### Post by pdc on 2011-11-05
if you go to post #2 here

[http://ubuntuforums.org/showthread.php?t=1689148](http://ubuntuforums.org/showthread.php?t=1689148)

chili suggested furnishing the data from some commands

> lspci -nn

and 

> lsmod | grep 819

you can see that the concern in this thread was that two drivers could be loading, which could cause conflict..............

---

