---
title: "Intel Corporation Centrino Advanced-N 6235 bluetooth"
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by ebe0 on 2012-07-13
I recently installed Intel Corporation Centrino Advanced-N 6235 (rev 24) on my Lenovo x220 tablet. The wireless is working fine, however bluetooth is not detected (intel 6235 comes with bluetooth 4.0). 
Has anyone had success with this or simillar card? and help is highly appriciated.

Configuration:

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 07)

$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Thanks in advance.

---

### Post by Kirk Schnable on 2012-07-13
Bluetooth adapters might not show up on lspci.  Can you give us "lsusb" as well?

Thanks,
Kirk

---

### Post by ebe0 on 2012-07-13
Bluetooth is integrated with Intel 6235 miniPCI card. 

Here is the output
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 004: ID 04f2:b217 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 056a:00e6 Wacom Co., Ltd

---

### Post by Kirk Schnable on 2012-07-13
It sounds like System76 sells a laptop with this chipset, so I find it hard to believe it wouldn't be supported.

Which kernel version are you running?  I wonder if this is a case where your hardware would be supported in a later distro.

Kirk

---

### Post by ebe0 on 2012-07-13
Hi Kirk,

Ubuntu 12.04 kernel : 
> uname -a
Linux ebe0 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I think the device is 8087:07DA (which seems to be a USB device), however it is not being detected.

Have you had any success with an Intel centrino dual(wifi + bluetooth) miniPCI card? There doesn't seem to be much informaition regarding this. Much of the discussion surrounds wifi connnection.

Thanks for the support.

Ebe

---

### Post by Kirk Schnable on 2012-07-13
Shot in the dark here, but have you tried Function+F5 or whatever the "wireless hotkey" is on your machine?

I've seen an instance in Lenovo with Intel chipsets where the wireless hotkey actually turns the Bluetooth completely off, which might explain why it's not being detected.

I've seen some weird stuff too where if Windows is shut down with Bluetooth off, Ubuntu can't turn it back on. (on my dual booting laptop with an Intel chipset).

I'd hate to recommend reinstalling Windows just to see... but was Bluetooth ON when you last used Windows?  

I also have seen "wireless switch oddities" with some of our Lenovo IdeaPads at work.  When the wireless swiitch was turned off, it changed something in the BIOS (not in a user editable field) and the wireless could not be turned back on by the Ubuntu driver.  The somewhat annoying fix we found was pulling the CMOS battery.

You can decide which of my "workarounds" you want to look into trying.  Good luck...

Kirk

---

