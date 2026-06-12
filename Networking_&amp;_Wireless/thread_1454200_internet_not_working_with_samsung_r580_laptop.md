---
title: "internet not working with samsung r580 laptop"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by lydo on 2010-04-14
I just bought a samsung r580 laptop. this is the first time i've ever owned a laptop. I have owned a pc with ubuntu 8.04 installed on it and the internet worked trouble free. Now I have windows 7 and ubuntu 9.10 dual booted on my samsung r580. I used wubi to install and the internet works fine in windows but will not work in ubuntu. I have been trying to get this to work for about 5 hours now and stumped! I am not that computer savy so please dumbed down your responses for me. thanx

---

### Post by chili555 on 2010-04-14
Wired or wireless? Please open Applications > Accessories > Terminal and do:```
lspci -nn
```Please post the results.

---

### Post by lydo on 2010-04-15
I've tried wireless and with the ethernet cable plugged in but to no avail. I typed in the command you suggested and here are the results (I hope you can understand cause its a different language to me!):

00:00.0 Host bridge [0600]: Intel Corporation Arrandale DRAM Controller [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Arrandale PCI Express x16 Root Port [8086:0045] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a75] (rev a2)
02:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be3] (rev a1)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4381] (rev 11)
ff:00.0 Host bridge [0600]: Intel Corporation QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Device [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Device [8086:2d13] (rev 02)

thanx in advance for your help.

---

### Post by chili555 on 2010-04-15
I believe thei is a Realtek 8192E chipset. The most reliable way to get it going is with ndiswrapper and the Windows .inf and .sys files. Do you have the driver CD that came with the device? Please see attached.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by lydo on 2010-04-16
You are a hero! it totally worked! thank for your help.

---

### Post by ykerb on 2010-07-07
thank you both. It works!

---

### Post by msriram on 2010-09-08
hey, may i know how to use that file? I cannot install ndiswrapper on my laptop, cuz I dont have internet working...

---

