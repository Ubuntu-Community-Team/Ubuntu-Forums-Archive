---
title: "Dell 1537 Broadcom Netlink tm gigabit ethernet driver location"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by LfxqtmzGT4iK on 2011-01-21
I've been looking through my windows hard-drive for my Ethernet driver which I really need to locate so i don't have to use the Big 'ol' blue cable any more. Any suggestions to where I can find the INF file for this?

---

### Post by chili555 on 2011-01-21
I'm confused. The title of your thread implies you need a driver for your ethernet card. The text of your thread implies you need to detach and stop using the ethernet cable. I suspect you really want a wireless driver. As long as you have an ethernet connection, is there an option to activate additional drivers in System > Administration > Additional Drivers? Can you tell us more about your wireless card? Please open a terminal and run and post:```
lspci -nn
```

---

### Post by LfxqtmzGT4iK on 2011-01-21
jordan@jordan-Studio-1537:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
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
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3400 Series [1002:95c4]
01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
09:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)

Okay that's everything but i am looking for the inf of my wireless driver

---

### Post by racho on 2011-01-21
Plug it through the ethernet cable and go System->Administration->Additional Drivers, then choose whatever option it gives you. It should be working.
Broadcom WiFi drivers usually do not work out of the box in Ubuntu so you'll need the proprietary one.

---

### Post by chili555 on 2011-01-21
However, he has an Intel wireless device:> Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]It works with the driver *iwlagn* that is already built in to the kernel. If it's not working out of the box, something else is wrong. Please run and post:```
rfkill list all
dmesg | grep iwl
```

---

### Post by LfxqtmzGT4iK on 2011-01-22
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jordan@jordan-Studio-1537:~$ dmesg | grep iwl
[   10.137714] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.137716] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.137819] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.137855] iwlagn 0000:04:00.0: setting latency timer to 64
[   10.137916] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.179087] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.179218] iwlagn 0000:04:00.0: irq 47 for MSI/MSI-X
[   10.186212] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[   10.197873] phy0: Selected rate control algorithm 'iwl-agn-rs'

Okay that's everything. What now?

---

### Post by chili555 on 2011-01-22
> 0: dell-wifi: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]This implies one of two things. Either the hardware switch on your laptop is switched to turn the wireless off and needs to simply be moved back to 'On' or the module *dell-laptop* is not properly translating the key position to the kernel. *dell-laptop* is notoriously a bit tricky.

If you have carefully determined that the switch is on, open a terminal and let's remove the *dell-laptop* module:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
rfkill list all
```Is the wireless still hard blocked? Is the wireless now working? If that was the fix, let's blacklist the module so it doesn't reload on boot.```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Please post back so the searchers can learn from your experience.

---

### Post by LfxqtmzGT4iK on 2011-01-30
That just did the trick. My wireless is now working perfectly! Thanks for that!

---

### Post by jeshua90 on 2012-07-28
root@bt:~# lspci -nn 00:00.0 Host bridge [0600]: Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02) 00:01.0 ISA bridge [0601]: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] [8086:7000] 00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01) 00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef] 00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02) 00:04.0 System peripheral [0880]: InnoTek Systemberatung GmbH VirtualBox Guest Service [80ee:cafe] 00:05.0 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 01) 00:06.0 USB Controller [0c03]: Apple Computer Inc. KeyLargo/Intrepid USB [106b:003f] 00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08) 00:0d.0 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)

---

### Post by chili555 on 2012-07-28
> root@bt:~# lspci -nn 00:00.0 Host bridge [0600]: Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02) 00:01.0 ISA bridge [0601]: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] 
<snip>That doesn't tell us much. Are you trying to get wired ethernet going? Are you doing to do so in a virtual machine, by chance?

---

### Post by jeshua90 on 2012-07-28
yes!!

---

### Post by chili555 on 2012-07-28
> **jeshua90 said:**
> yes!![http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

