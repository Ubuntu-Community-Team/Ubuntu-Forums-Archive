---
title: "Wireless Doesn't Work Toshiba Satellite M305D 4830"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by mgoblue on 2009-01-14
Hi, the wireless isn't working on my toshiba satellite M305D 4830.  I am using ubuntu 8.04 64 bit.  

From sudo lspci -v:

```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7128
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint IRQ 0
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f0501000 (32-bit, non-prefetchable) [size=4K]
	Memory at f0500000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [60] Power Management version 2

09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, slow devsel, latency 64, IRQ 20
	Memory at f0500800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a0] Power Management version 2

09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: slow devsel, IRQ 11
	Memory at f0502000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2

```

Help?

---

### Post by crazeepingu on 2009-01-14
Did you try using windows driver ? Use ndisgtk to use windows drivers for your wireless device.

---

### Post by mgoblue on 2009-01-14
> **crazeepingu said:**
> Did you try using windows driver ? Use ndisgtk to use windows drivers for your wireless device.


I don't have windows anymore, I assume I was supposed to look for the driver on my windows partition (which does not exist lol)?

---

### Post by mgoblue on 2009-02-07
Still can't get wireless to work.. :(

---

### Post by roypalacios on 2009-04-27
I have the same laptop, here is how I managed to get my wireless work:
```

# svn co http://svn.madwifi-project.org/madwifi/trunk madwifi
# wget https://dev.openwrt.org/export/12395/trunk/package/madwifi/ath_hal-20080528.tgz
# cd madwifi
# mv hal hal.old
# tar xvf ../ath_hal-20080528.tgz
# mv ath_hal-20080528 hal
# make install BINDIR=/usr/bin MANDIR=/usr/share/man
# depmod -ae
# modprobe ath_pci

```
After that you might need to restart.
Good luck!

---

