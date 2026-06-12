---
title: "Realtek r8168 oneric 11.10"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by blubricks on 2012-03-09
Dual Boot Win7/Kubuntu 11.10 HP Pavillion
Hey All. I've been working on this for two days now. The closest I have gotten to a solution has been to follow the instructions here.

[http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/]("http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/")

I apologize for simply linking I am new to Linux and have had nothing but problems, if not for my stubborn nature I would not be here.
Regardless, The instructions I linked to are missing a few steps as pointed out in the comments. I believe something along the lines of rmmod 8169 and update-initramfs -u. Again please forvive my newbish ways.

Now this has gotten me to the point of installing the new driver until I reboot. The last two commands in this fix under "8. Make it available for boot" have not worked for me. when I enter these I get the error

cryptsetup: WARNING: failed to detect canonical device of /host/ubuntu/disks/root.disk
cryptsetup: WARNING: could not determine root device from /etc/fstab
Warning: No support for locale: en_US.utf8

I have searched high and low for another solution and am at my wits end. I appreciate any help or direction you can offer.

---

### Post by blubricks on 2012-03-09
If this helps...


07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
        Subsystem: Hewlett-Packard Company Device 3387
        Flags: bus master, fast devsel, latency 0, IRQ 42
        I/O ports at 2000 [size=256]
        Memory at f0104000 (64-bit, prefetchable) [size=4K]
        Memory at f0100000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: r8168

---

