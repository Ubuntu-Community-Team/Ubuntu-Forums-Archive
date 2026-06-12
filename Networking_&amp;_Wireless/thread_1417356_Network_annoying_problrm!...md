---
title: "Network annoying problrm!.."
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by ravnen620 on 2010-02-27
Hi everybody..
I got a Acer Aspire 6930g..
I installed Ubuntu 9.1

When i tried to get connection to the internet it couldt find anything..
So how or where do i find a driver for it..

Its a: 

Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller

/ thanks!..
(im new)

---

### Post by chili555 on 2010-02-27
Please open Applications -> Accessories -> Terminal and do:```
lspci -nn | grep Ethernet
sudo modprobe atl1e
ifconfig
```Post the result. The second command is a bit confusing to read. In caps, it would be ATL1E, but enter it as above. Thanks.

---

### Post by ravnen620 on 2010-02-27
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by chili555 on 2010-02-27
Let's broaden the search:```
lspci -nn
dmesg | grep atl
```Thanks.

---

### Post by ravnen620 on 2010-02-27
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9600M GT] [10de:0649] (rev a1)
07:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
09:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller [1969:1026] (rev b0)

---

### Post by chili555 on 2010-02-27
This is supposed to work with the driver module *atl1e*. Although you have modprobed it, dmesg evidently says nothing about it. Let's see what dmesg has to say about the device in *any* respect:```
dmesg | grep 09:00
```This is quite curious...and annoying!

---

### Post by ravnen620 on 2010-02-27
[    1.157414] pci 0000:09:00.0: reg 10 64bit mmio: [0x000000-0x03ffff]
[    1.157424] pci 0000:09:00.0: reg 18 io port: [0x00-0x7f]
[    1.157499] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    1.157504] pci 0000:09:00.0: PME# disabled
[    1.196996] pnp 00:04: io resource (0x2e-0x2f) overlaps 0000:09:00.0 BAR 2 (0x0-0x7f), disabling
[    1.197000] pnp 00:04: io resource (0x61-0x61) overlaps 0000:09:00.0 BAR 2 (0x0-0x7f), disabling
[    1.197003] pnp 00:04: io resource (0x63-0x63) overlaps 0000:09:00.0 BAR 2 (0x0-0x7f), disabling
[    1.197006] pnp 00:04: io resource (0x65-0x65) overlaps 0000:09:00.0 BAR 2 (0x0-0x7f), disabling
[    1.197010] pnp 00:04: io resource (0x67-0x67) overlaps 0000:09:00.0 BAR 2 (0x0-0x7f), disabling
[    1.197013] pnp 00:04: io resource (0x68-0x6f) overlaps 0000:09:00.0 BAR 2 (0x0-0x7f), disabling
[    1.197016] pnp 00:04: io resource (0x70-0x70) overlaps 0000:09:00.0 BAR 2 (0x0-0x7f), disabling
[    3.445146] ATL1E 0000:09:00.0: enabling device (0000 -> 0003)
[    3.445156] ATL1E 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.445170] ATL1E 0000:09:00.0: setting latency timer to 64
[    3.564217] ATL1E 0000:09:00.0: MAC state machine cann't be idle since disabled for 10ms second
[    3.564252] ATL1E 0000:09:00.0: PCI INT A disabled
[    3.564266] ATL1E: probe of 0000:09:00.0 failed with error -5

---

### Post by chili555 on 2010-02-27
Ooooh! Nasty!

I'm googling...

---

### Post by chili555 on 2010-02-27
It looks like it's a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933)

Although the title of this bug refers to iwl5100, you will notice that the symptoms are the same and atl1xx is referred to. If you want to try the fix in post #79, it should be fairly easy. If it doesn't work, it's easy to remove.

---

### Post by ravnen620 on 2010-02-27
thanks a lot for it so fare. i will check it out ;D

---

### Post by ravnen620 on 2010-02-27
> **ravnen620 said:**
> thanks a lot for it so fare. i will check it out ;D

Where should i paste the patch file, if its that file, you mean i should get.. ?

---

### Post by chili555 on 2010-02-27
Oops! Post #79 says there is a revised kernel at the URL quoted; however, as you have seen, there is now, months later, merely a patch. A patch is rather complex and involves recompiling your kernel.

If you have the ability to download and install, even if it is with a USB key, I think you would be much better off to grab the latest linux-image, here and install it. [http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-19-generic](http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-19-generic)

Be sure to download either the i386 or x64 version, depending on your installed version. Find out with:```
uname -a
```If you had a 64-bit linux, you would see x86_64 instead of i686 and i386. 

After you download it, presumably to your desktop, do:```
cd Desktop
sudo dpkg -i *.deb
```The wildcard * will install all .deb files on your desktop; presumably, the only one you have is the one you want installed.

Reboot and give us a (hopefully) good report.

---

