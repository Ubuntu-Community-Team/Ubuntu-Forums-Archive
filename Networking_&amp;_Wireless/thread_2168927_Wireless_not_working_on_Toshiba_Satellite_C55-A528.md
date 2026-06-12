---
title: "Wireless not working on Toshiba Satellite C55-A5281"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by jasonodoom on 2013-08-19
I just installed Ubuntu on my Toshiba Satellite C55-A5281 and the wireless isn't working. I checked to see if there were any drivers that need installing, but there were none. How can this be fixed?

---

### Post by carl4926 on 2013-08-19
Post for us the result of

```
lspci -nnk
```

---

### Post by jasonodoom on 2013-08-19
Here's the output:

jason@Matrix:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0156] (rev 09)
	Subsystem: Toshiba America Info Systems Device [1179:fa20]
	Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: mei
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 7 Series Chipset Family LPC Controller [8086:1e5e] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: alx
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181]

---

### Post by carl4926 on 2013-08-19
Do me a favour and also post

```
lspci -n
```

---

### Post by jasonodoom on 2013-08-19
I've just installed updates via ethernet and it won't boot: 'An erro occured while mounting /boot.'

---

### Post by carl4926 on 2013-08-19
Your device
```
[COLOR=#000000]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)[/COLOR]
[COLOR=#000000]Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181][/COLOR]
```

Isn't listed as working that I can see.

But you have other problems it seems..

---

### Post by jasonodoom on 2013-08-19
Alright, I had to skip mounting. Now the touchpad doesn't even work.

---

### Post by jasonodoom on 2013-08-19
Then this device cannot run ubuntu?

---

### Post by jasonodoom on 2013-08-19
Here's the output:

ubuntu@ubuntu:~$ lspci -n
00:00.0 0600: 8086:0154 (rev 09)
00:02.0 0300: 8086:0156 (rev 09)
00:14.0 0c03: 8086:1e31 (rev 04)
00:16.0 0780: 8086:1e3a (rev 04)
00:1a.0 0c03: 8086:1e2d (rev 04)
00:1b.0 0403: 8086:1e20 (rev 04)
00:1c.0 0604: 8086:1e10 (rev c4)
00:1c.1 0604: 8086:1e12 (rev c4)
00:1d.0 0c03: 8086:1e26 (rev 04)
00:1f.0 0601: 8086:1e5e (rev 04)
00:1f.2 0106: 8086:1e03 (rev 04)
00:1f.3 0c05: 8086:1e22 (rev 04)
01:00.0 0200: 1969:1090 (rev 10)
02:00.0 0280: 10ec:8179 (rev 01)

---

### Post by carl4926 on 2013-08-19
> **jasonodoom said:**
> Here's the output:

ubuntu@ubuntu:~$ lspci -n
00:00.0 0600: 8086:0154 (rev 09)
00:02.0 0300: 8086:0156 (rev 09)
00:14.0 0c03: 8086:1e31 (rev 04)
00:16.0 0780: 8086:1e3a (rev 04)
00:1a.0 0c03: 8086:1e2d (rev 04)
00:1b.0 0403: 8086:1e20 (rev 04)
00:1c.0 0604: 8086:1e10 (rev c4)
00:1c.1 0604: 8086:1e12 (rev c4)
00:1d.0 0c03: 8086:1e26 (rev 04)
00:1f.0 0601: 8086:1e5e (rev 04)
00:1f.2 0106: 8086:1e03 (rev 04)
00:1f.3 0c05: 8086:1e22 (rev 04)
01:00.0 0200: 1969:1090 (rev 10)
02:00.0 0280: 10ec:8179 (rev 01)

You can check the output here
[http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)

---

### Post by carl4926 on 2013-08-20
> **jasonodoom said:**
> Then this device cannot run ubuntu?
Your machine will probably run ubuntu
The wireless device might have issues.... wait for others to reply

---

### Post by red_starfox2 on 2013-08-27
Hello, besides trying out a other distro, I had a idea seeing your PCs hardware...maybe a PCIe mini extension card that comes with linux drivers?

---

