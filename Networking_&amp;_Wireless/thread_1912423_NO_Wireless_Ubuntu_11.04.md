---
title: "NO Wireless Ubuntu 11.04"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by shirbal on 2012-01-20
Hi all,

i just installed ubuntu 11.04 on my laptop
i installed it from windows by wubi
 
i can see any networks around me (routers) at all.

thanks for your help

shiran

---

### Post by ACMarina on 2012-01-20
Can you post the output of ifconfig?

---

### Post by shirbal on 2012-01-20
hi, not really beacuse i am using the forum from another comupter,
tell me what u want to check and i will write it (the output is long..)

THanks!!!

---

### Post by ACMarina on 2012-01-20
Does the wireless adapter show up when you type in ifconfig? Does it show up when you look in your network connection manager?

---

### Post by shirbal on 2012-01-20
no, and no... ):

---

### Post by ACMarina on 2012-01-20
How is the wireless device connected? PCI, USB, etc?

---

### Post by shirbal on 2012-01-20
its a built in wirless ( in my laptop) (i am sure if thats what u r asking)

---

### Post by ACMarina on 2012-01-20
alright, let's try "lspci" and see what you get.. 

What kind of laptop is it, by the way? Make/Model?

---

### Post by ajgreeny on 2012-01-20
See what ```
lspci
``` shows in terminal, or possibly better```
sudo lshw -C network
```

Both should show what wireless adapter you have and give a clue as to driver needs.

---

### Post by alexandrum77 on 2012-01-20
Better, run lspci -nnk. This way we'll have the PCI ID and the driver/module that's currently in use by the kernel. Using the PCI ID you can search for existing bugs on launchpad.net or better use this ([http://www.google.com/cse/home?cx=001461844748502826593:hh-ikmexth4](http://www.google.com/cse/home?cx=001461844748502826593:hh-ikmexth4)) The PCI ID is the one that uniquely identifies the hardware among others.
Example:
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

The PCI ID is "[10ec:8168]"

---

### Post by shirbal on 2012-01-20
[FONT=Liberation Serif, Times New Roman, serif]*-network               [/FONT] 
 

        [FONT=Liberation Serif, Times New Roman, serif]description: Network controller[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]product: BCM4312 802.11b/g LP-PHY[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]vendor: Broadcom Corporation[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]physical id: 0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]bus info: pci@0000:04:00.0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]version: 01[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]width: 64 bits[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]clock: 33MHz[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]capabilities: pm msi pciexpress bus_master cap_list[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]configuration: driver=b43-pci-bridge latency=0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]resources: irq:18 memory:f4700000-f4703fff[/FONT]
 

   [FONT=Liberation Serif, Times New Roman, serif]*-network[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]description: Ethernet interface[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]product: NetLink BCM5906M Fast Ethernet PCI Express[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]vendor: Broadcom Corporation[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]physical id: 0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]bus info: pci@0000:07:00.0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]logical name: eth0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]version: 02[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]serial: 00:1e:ec:9d:1c:81[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]capacity: 100Mbit/s[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]width: 64 bits[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]clock: 33MHz[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]resources: irq:48 memory:f4600000-f460ffff[/FONT]
 

   [FONT=Liberation Serif, Times New Roman, serif]*-network:0 DISABLED[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]description: Wireless interface[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]physical id: 1[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]logical name: wlan0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]serial: 00:23:4e:c0:4c:3e[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]capabilities: ethernet physical wireless[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg[/FONT]
 

   [FONT=Liberation Serif, Times New Roman, serif]*-network:1[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]description: Ethernet interface[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]physical id: 2[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]bus info: usb@2:2[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]logical name: eth1[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]serial: cc:08:e0:1c:34:c0[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]capabilities: ethernet physical[/FONT]
 

        [FONT=Liberation Serif, Times New Roman, serif]configuration: broadcast=yes driver=ipheth link=yes multicast=yes[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]shiranmaor@ubuntu:~$ [/FONT] 
 

 [FONT=Liberation Serif, Times New Roman, serif]shiranmaor@ubuntu:~$ [/FONT] 
 

 [FONT=Liberation Serif, Times New Roman, serif]shiranmaor@ubuntu:~$ [/FONT] 
 

 [FONT=Liberation Serif, Times New Roman, serif]shiranmaor@ubuntu:~$ lspci -nnk[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a00][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: agpgart-intel[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a02][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: i915[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: i915[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a02][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a09][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: uhci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a0a][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: uhci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a0b][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: uhci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a0c][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: ehci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a0d][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: HDA Intel[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: snd-hda-intel[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: pcieport[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: shpchp[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: pcieport[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: shpchp[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: pcieport[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: shpchp[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: pcieport[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: shpchp[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: pcieport[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: shpchp[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a14][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: uhci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a15][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: uhci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a16][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: uhci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a17][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: ehci_hcd[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a19][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: iTCO_wdt[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a1a][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: ahci[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: ahci[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3a1d][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: i2c-i801[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3d9b][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: sdhci-pci[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: sdhci-pci[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3d9a][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: sdhci-pci[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]02:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo Device [17aa:3d9c][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: jmb38x_ms[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: jmb38x_ms[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Broadcom Corporation Device [14e4:04b5][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: b43-pci-bridge[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: ssb[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Subsystem: Lenovo IdeaPad S10e [17aa:3a23][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel driver in use: tg3[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]	Kernel modules: tg3[/FONT]

---

### Post by shirbal on 2012-01-20
shorter one:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Lenovo Device [17aa:3a00]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Lenovo Device [17aa:3a02]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Lenovo Device [17aa:3a02]
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Lenovo Device [17aa:3a09]
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Lenovo Device [17aa:3a0a]
    Kernel driver in use: uhci_hcd
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Lenovo Device [17aa:3a0b]
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Lenovo Device [17aa:3a0c]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Lenovo Device [17aa:3a0d]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Lenovo Device [17aa:3a14]
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Lenovo Device [17aa:3a15]
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Lenovo Device [17aa:3a16]
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Lenovo Device [17aa:3a17]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Lenovo Device [17aa:3a19]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
    Subsystem: Lenovo Device [17aa:3a1a]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Lenovo Device [17aa:3a1d]
    Kernel modules: i2c-i801
02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
    Subsystem: Lenovo Device [17aa:3d9b]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
    Subsystem: Lenovo Device [17aa:3d9a]
    Kernel modules: sdhci-pci
02:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
    Subsystem: Lenovo Device [17aa:3d9c]
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
    Kernel driver in use: tg3
    Kernel modules: tg3

---

### Post by shirbal on 2012-01-20
now i am using the internet from my iphone so i can post any output u want

thanks i  advenced

---

### Post by ACMarina on 2012-01-20
The device is showing up in lspci but it doesn't show up (not even as disabled or something) in your network manager, is that correct?

---

### Post by shirbal on 2012-01-20
correct

---

### Post by shirbal on 2012-01-21
Help someone?!?!

---

### Post by wildmanne39 on 2012-01-21
Hi, please post the output of:
```
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
```
lsmod | grep b43
```
```
dmesg | egrep 'b43|firm|wlan|wpa'
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by shirbal on 2012-01-22
the first code:

shiranmaor@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      no wireless extensions.

bnep0     no wireless extensions.

shiranmaor@ubuntu:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
shiranmaor@ubuntu:~$ lsmod
Module                  Size  Used by
ipheth                 13238  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_codec_hdmi     27479  1 
binfmt_misc            13213  1 
rfcomm                 38125  8 
sco                    17779  2 
bnep                   17785  3 
l2cap                  48656  18 rfcomm,bnep
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  450944  3 
snd_seq_midi           13132  0 
b43                   296610  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 i915
mac80211              257001  1 b43
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18160  4 
jmb38x_ms              17364  0 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
videodev               75143  1 uvcvideo
cfg80211              156212  2 b43,mac80211
drm                   180037  4 i915,drm_kms_helper
joydev                 17322  0 
snd                    55295  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
memstick               15816  1 jmb38x_ms
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
tg3                   131476  0 
ahci                   21591  1 
libahci                25548  1 ahci
sdhci_pci              13623  0 

ssb                    45942  1 b43
sdhci                  22720  1 sdhci_pci
shiranmaor@ubuntu:~$ nm -tool
nm: 'a.out': No such file
shiranmaor@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth1      Interface doesn't support scanning.

bnep0     Interface doesn't support scanning.

---

### Post by shirbal on 2012-01-22
shiranmaor@ubuntu:~$ lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43
shiranmaor@ubuntu:~$

---

### Post by shirbal on 2012-01-22
the third:

shiranmaor@ubuntu:~$ dmesg | egrep 'b43|firm|wlan|wpa'
[    1.190988] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.191003] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[   17.520976] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   17.687801] Registered led device: b43-phy0::tx
[   17.687886] Registered led device: b43-phy0::rx
[   17.687966] Registered led device: b43-phy0::radio
[   18.240537] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   18.240589] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   18.240631] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2467.377066] b43-pci-bridge 0000:04:00.0: PCI INT A disabled
[ 2468.813830] b43-pci-bridge 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[ 2468.813891] b43-pci-bridge 0000:04:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf4700004)
[ 2468.813904] b43-pci-bridge 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2468.813921] b43-pci-bridge 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2468.816034] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2471.503221] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 2471.503227] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 2471.503231] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
shiranmaor@ubuntu:~$ 


thanks for your time

---

### Post by shirbal on 2012-01-22
never mind, i downloaded from the link above something i guess was missing.

thanks again for your time

---

### Post by wildmanne39 on 2012-01-22
Hi, yes the firmware was missing, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

