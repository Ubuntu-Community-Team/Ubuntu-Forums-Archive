---
title: "AMD64 + N300 USB adapter"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by cybpabeofm on 2012-04-10
I was running ubuntu 11.10 32 bit until I discovered that it didnt use all of my RAM (only 2 gigabytes were in use out of 8 gigabytes) so I switched to AMD64. I downloaded the Netgear N300 WNA3100 driver (both 64bit and 32bit) from: [http://dl.dropbox.com/u/32258336/ndis_bcmwl.zip](http://dl.dropbox.com/u/32258336/ndis_bcmwl.zip)

I installed these with NDISWRAPPER's GUI. Then linked the driver to my hardware through this command:
ndiswrapper -a 0846:9020 bcmwlhigh5

This is the output from ndiswrapper -l:
bcmwlhigh5: driver installed
     device (0846:9020) present

However when I run iwconfig I have this output:
lo:      no wireless extensions

eth0:    no wireless extensions


Does anyone know any way that I can have ubuntu successfully load this ndiswrapper driver?

---

### Post by idoitprone on 2012-04-10
> **cybpabeofm said:**
> I was running ubuntu 11.10 32 bit until I discovered that it didnt use all of my RAM (only 3 1/2 gigabytes were in use out of 8 gigabytes) so I switched to AMD64. I downloaded the Netgear N300 WNA3100 driver (both 64bit and 32bit) from: [http://dl.dropbox.com/u/32258336/ndis_bcmwl.zip](http://dl.dropbox.com/u/32258336/ndis_bcmwl.zip)

I installed these with NDISWRAPPER's GUI. Then linked the driver to my hardware through this command:
ndiswrapper -a 0846:9020 bcmwlhigh5

This is the output from ndiswrapper -l:
bcmwlhigh5: driver installed
     device (0846:9020) present

However when I run iwconfig I have this output:
lo:      no wireless extensions

eth0:    no wireless extensions


Does anyone know any way that I can have ubuntu successfully load this ndiswrapper driver?

we would rather have you tell us the details of the card so we can find the proper open source driver

```
lspci -nnk

```
is this a usb wireless dongle?

---

### Post by cybpabeofm on 2012-04-10
Yes it is a wireless USB dongle. I have previously had it working on Ubuntu 11.10 32bit with the help of chili555, however the driver he supplied me with was 32bit, I have been browsing for a 64bit driver, this is the closest ive gotten.
user@user-GA-990FXA-UD3:~$ lspci -nnk
00:00.0 Host bridge [0600]: ATI Technologies Inc RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
	Subsystem: Giga-byte Technology Device [1458:5000]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:09.0 PCI bridge [0604]: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:0a.0 PCI bridge [0604]: ATI Technologies Inc RD890 PCI to PCI bridge (external gfx1 port A) [1002:5a1d]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40)
	Subsystem: Giga-byte Technology GA-MA770-DS3rev2.0 Motherboard [1458:b002]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Giga-byte Technology Device [1458:5004]
	Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Giga-byte Technology Device [1458:5004]
	Kernel driver in use: ehci_hcd
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Giga-byte Technology Device [1458:5004]
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Giga-byte Technology Device [1458:5004]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
	Subsystem: Giga-byte Technology Device [1458:5002]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: Giga-byte Technology Device [1458:a132]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
	Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
	Subsystem: Giga-byte Technology Device [1458:5004]
	Kernel driver in use: ohci_hcd
00:15.0 PCI bridge [0604]: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:15.1 PCI bridge [0604]: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:15.2 PCI bridge [0604]: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:15.3 PCI bridge [0604]: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Giga-byte Technology Device [1458:5004]
	Kernel driver in use: ohci_hcd
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Giga-byte Technology Device [1458:5004]
	Kernel driver in use: ehci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 2 [1022:1602]
	Kernel modules: amd64_edac_mod
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 3 [1022:1603]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 4 [1022:1604]
	Kernel driver in use: fam15h_power
	Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2056]
	Kernel modules: nouveau, nvidiafb
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0bee] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2056]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 USB Controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
	Subsystem: Giga-byte Technology Device [1458:5007]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd
03:00.0 IDE interface [0101]: Marvell Technology Group Ltd. Device [1b4b:917a] (rev 11)
	Subsystem: Giga-byte Technology Device [1458:b000]
04:06.0 RAID bus controller [0104]: VIA Technologies, Inc. VT6421 IDE RAID Controller [1106:3249] (rev 50)
	Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller [1106:3249]
	Kernel driver in use: sata_via
	Kernel modules: sata_via
04:0e.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
	Subsystem: Giga-byte Technology GA-7VT600-1394 Motherboard [1458:1000]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
06:00.0 USB Controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
	Subsystem: Giga-byte Technology Device [1458:5007]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

Predictably the adapter isnt in here, do you know where I can get a driver for it? It is device 0846:9020

---

### Post by idoitprone on 2012-04-10
> **cybpabeofm said:**
> 
ndiswrapper -a 0846:9020 bcmwlhigh5

This is the output from ndiswrapper -l:
bcmwlhigh5: driver installed
**      device (0846:9020) present**

srry i didnt reply sooner but i fell ill.

ok here

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

this link show all the required steps, tat sucks no linux driver
btw, since this is a usb adapter you must use
```
lsusb
```the words in bold show the problem 
run this command
[SIZE=3]```
ndiswrapper -a 0846:9020 bcmwlhigh5
```check if config failed
```
 dmesg -c
```[/SIZE]

if failed, go to the link because. it will too difficult for me to explain something I do never needed to use

---

### Post by chili555 on 2012-04-11
> I was running ubuntu 11.10 32 bit until I discovered that it didnt use all of my RAM (only 2 gigabytes were in use out of 8 gigabytes) so I switched to AMD64. You could have installed a pae linux-image as i did:> chili@LAPTOP60:~$ uname -r
3.0.0-17-generic-[COLOR="Red"]pae[/COLOR]
chili@LAPTOP60:~$ arch
i686
chili@LAPTOP60:~$ cat /proc/meminfo
MemTotal:        [COLOR="Red"]3914860 kB[/COLOR]
MemFree:         1507120 kB
Buffers:          264932 kB
Cached:          1545556 kB
<snip>
If the fix above doesn't help, you might try these attached. You'd need to remove bcmwlhigh5 and install bcmn43xx64.inf.

---

### Post by cybpabeofm on 2012-04-11
> **idoitprone said:**
> srry i didnt reply sooner but i fell ill.

ok here

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

this link show all the required steps, tat sucks no linux driver
btw, since this is a usb adapter you must use
```
lsusb
```the words in bold show the problem 
run this command
[SIZE=3]```
ndiswrapper -a 0846:9020 bcmwlhigh5
```check if config failed
```
 dmesg -c
```[/SIZE]

if failed, go to the link because. it will too difficult for me to explain something I do never needed to use


The driver install from the wiki didnt fail:


[  193.861823] Disabling lock debugging due to kernel taint
[  193.877437] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  193.918084] usbcore: registered new interface driver ndiswrapper
As you can see it didnt fail to load the driver so I dont really understand what went wrong then again I'm still a freshmen when it comes to wireless drivers on ubuntu 64 bit


however iwconfig doesnt show that the wireless adapter is present.

lsusb command output:
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

The following error occurred when I attempted to install the driver that chili555 gave me:

user@user-GA-990FXA-UD3:~/Desktop/BCM$ sudo ndiswrapper -i bcmn43xx64.inf
[sudo] password for user: 
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
couldn't find install section "BCM43XXN32" -
installation may be incomplete
user@user-GA-990FXA-UD3:~/Desktop/BCM$

---

### Post by cybpabeofm on 2012-04-11
Nevermind, I am going to scrap this idea, move to 12.04 32 bit, install the 32 bit WNA3100 drivers through ndiswrapper 1.57 and then use the different kernel like chili555 suggested.

---

### Post by idoitprone on 2012-04-12
> **cybpabeofm said:**
> Nevermind, I am going to scrap this idea, move to 12.04 32 bit, install the 32 bit WNA3100 drivers through ndiswrapper 1.57 and then use the different kernel like chili555 suggested.

you dont use iwconfig to see if it exist

use ```
ifconfig -a
```

you should check because it might have suceeded and you have internet

---

