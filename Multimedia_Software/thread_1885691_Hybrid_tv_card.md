---
title: "Hybrid tv card"
date: 2011-11-23
forum: Multimedia Software
---

### Post by anthony2010 on 2011-11-23
Hi all. 

Ive searched the forums but have found nothing that can help.

I have an Avermedia tv card that utilises the Philips SAA7231 chipset. 
i d an older philips chipset on an older card that worked but I sold the machine.

Does anyone know how I can get this set up? Ive tried installing various libraries, running various commands but nothing seems to work. Im no techno guy but I think this is a pci e card.

Anyway, heres the output of lspci and some of the commands Ive tried:

anthony@anthony-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: ASRock Incorporation Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
02:00.0 Multimedia controller: Philips Semiconductors SAA7231 (rev 8a)
03:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:06.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus
anthony@anthony-desktop:~$ sudo modprobe | grep SAA7231
[sudo] password for anthony: 
Usage: modprobe [-v] [-V] [-C config-file] [-d <dirname> ] [-n] [-i] [-q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
anthony@anthony-desktop:~$ set up my ******* tv card you pile of ****
anthony@anthony-desktop:~$ 

Im not one for quitting but I need help on this one.

Thanks in advance guys.

Anthony.

---

### Post by BicyclerBoy on 2011-11-23
Check the output of dmesg for firmware loading etc..

dmesg | grep firmware
dmesg | grep SAA

You need to install the linux firmware package (possibly non-free firmware as well) .

To see if the driver is loaded look in dmesg or ..
lsmod | grep saa
(maybe SAA)

---

### Post by wolfen69 on 2011-11-23
Try
```
sudo apt-get install linux-firmware-nonfree
```
reboot

Most of the firmware in this package is for television tuner cards. However,
non-free firmware for other classes of devices are provided as well.

---

### Post by anthony2010 on 2011-11-26
> **BicyclerBoy said:**
> Check the output of dmesg for firmware loading etc..

dmesg | grep firmware
dmesg | grep SAA

You need to install the linux firmware package (possibly non-free firmware as well) .

To see if the driver is loaded look in dmesg or ..
lsmod | grep saa
(maybe SAA)

Thanks guys.

I installed the non free firmware - infact ?I insalled every sort of firmware in synaptic! Then I followed the commands.

Sadly, no tv card recognition. Its there in lspci but I just cant seem to get ubuntu to run it.(Yet)

Any other suggestions or ideas?

Thanks in advance!

Ant

---

### Post by wolfen69 on 2011-11-26
What tv apps have you tried?

---

### Post by BicyclerBoy on 2011-11-26
Can you post the relevant parts of dmesg output ?
Your post #4 did not include anything ..

look for:
- firmware
- registering 
- mpeg2
- dvb
etc

---

### Post by arisp on 2011-11-27
I looks like saa7231 is unsupported.
[http://www.jusst.de/hg/saa7231/summary](http://www.jusst.de/hg/saa7231/summary)
[https://www.linux.com/forums/multimedia/installing-and-using-a-saa7231-tv-card/9625#p9625](https://www.linux.com/forums/multimedia/installing-and-using-a-saa7231-tv-card/9625#p9625)

---

