---
title: "Configuring external monitor"
date: 2012-08-14
forum: Multimedia Software
---

### Post by Almeida1 on 2012-08-14
I've got a laptop which uses an external monitor fine in Windows, however Ubuntu doesn't detect it. When I run lspci I get the following:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0ffc (rev a1)
02:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 05)
02:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)

The laptop is a Lenovo W530.

Thanks

---

### Post by KidCoding on 2012-08-14
I have the same problem with the same computer.

I installed bumblebee but It didn't solve the problem.

I also tried to install the brand new nvidia drivers 304.37 but this blocked the resolution to 640x480 and didn't correct the problem of the external monitor detection.

The GPU is a nvidia quadro K2000M.

Any idea?

KidCoding

---

### Post by bdk on 2012-08-15
Same here, W530. Looking to get the external monitor working, tried xorg-edger's Nvidia-current, that didn't help.

In the bios, you can select discrete video and then you get the option of selecting external ports as the display. When I selected the VGA port, I do get video on my monitor, GRUB shows up, I select Ubuntu, screen changes to the deep purple and then just stops.

The x86 mem-test works fine.

I've got dual screens work, with a switchable option by following [here]("http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/") and [here]("http://sagark.org/thinkdisp-about-installation/"). It works great, but I'm now looking to JUST get the external monitor working and not work as an extended desktop.

*-bdk*

---

### Post by stephanunc on 2013-02-14
Hey Guys.

I am having the same issue. I haven't been able to use the DVI ports on my docking station. Currently am using laptop monitor + monitor one plugged into VGA...ok. installed Nvidia driver from website and it didn't fix it...dropped resolution to 640. 
would like to use DVI ports on docking station...plz help!

Ubuntu 12.04 LTS
Lenovo T430 laptop
Nvidia-5400 Optimus Video card
-not sure why lspci shows both Intel and Nvidia

Docking station model 
Type 4338

lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0def (rev ff) (prog-if ff)

---

