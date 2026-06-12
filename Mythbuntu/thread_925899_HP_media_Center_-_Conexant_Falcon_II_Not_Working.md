---
title: "HP media Center - Conexant Falcon II Not Working"
date: 2008-09-21
forum: Mythbuntu
---

### Post by tenju on 2008-09-21
Anyone have any luck with getting this Device working

here is my lspci

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
05:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:04.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
05:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by superm1 on 2008-09-21
lspci -nn would be more useful as it provides the product and vendor IDs to see if it matches any drivers.

---

### Post by tenju on 2008-09-21
Excuse my newbness 

00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770]
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771]
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 [8086:27e0] (rev 01)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 [8086:27e2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge [8086:27b0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller [8086:27c1] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600 GT [10de:0402] (rev a1)
04:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a] (rev 01)
05:02.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)
05:04.0 RAID bus controller [0104]: VIA Technologies, Inc. VT6421 IDE RAID Controller [1106:3249] (rev 50)
05:05.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20]

---

### Post by tenju on 2008-09-21
Also here is what i got from grep of ivtv

[   42.294150] ivtv:  Start initialization, version 1.1.0
[   42.294246] ivtv0: Initializing card #0
[   42.294254] ivtv0: Unknown card: vendor/device: 4444/0016
[   42.294259] ivtv0:               subsystem vendor/device: 1043/0666
[   42.294262] ivtv0:               cx23416 based
[   42.294265] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   42.294268] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   42.294272] ivtv0: card you have to the ivtv-devel mailinglist ([www.ivtvdriver.org](www.ivtvdriver.org))
[   42.294276] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   42.422487] ivtv0: Invalid EEPROM
[   42.631041] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   42.635279] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   42.716337] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   42.818312] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   42.818350] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   42.818386] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   42.818417] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   42.818446] ivtv0: Registered device radio0 for encoder radio
[   42.818449] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   42.818609] ivtv:  End initialization
[   49.329782] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   49.527013] ivtv0: Encoder revision: 0x02060039
[   52.854797] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d
[   52.925460] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d
[   52.982335] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d

---

### Post by superm1 on 2008-09-21
> **tenju said:**
> Also here is what i got from grep of ivtv

[   42.294150] ivtv:  Start initialization, version 1.1.0
[   42.294246] ivtv0: Initializing card #0
[   42.294254] ivtv0: Unknown card: vendor/device: 4444/0016
[   42.294259] ivtv0:               subsystem vendor/device: 1043/0666
[   42.294262] ivtv0:               cx23416 based
[   42.294265] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   42.294268] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   42.294272] ivtv0: card you have to the ivtv-devel mailinglist ([www.ivtvdriver.org]("http://www.ivtvdriver.org"))
[   42.294276] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   42.422487] ivtv0: Invalid EEPROM
[   42.631041] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   42.635279] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   42.716337] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   42.818312] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   42.818350] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   42.818386] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   42.818417] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   42.818446] ivtv0: Registered device radio0 for encoder radio
[   42.818449] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   42.818609] ivtv:  End initialization
[   49.329782] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   49.527013] ivtv0: Encoder revision: 0x02060039
[   52.854797] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d
[   52.925460] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d
[   52.982335] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d
Follow exactly what it says in dmesg about ivtv.  Odds are your card will end up supported, but they will walk you through getting some tweaks into the driver.

---

