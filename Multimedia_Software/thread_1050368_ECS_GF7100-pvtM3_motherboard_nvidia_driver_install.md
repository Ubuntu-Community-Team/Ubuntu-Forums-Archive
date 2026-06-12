---
title: "ECS GF7100-pvtM3 motherboard nvidia driver install problem"
date: 2009-01-25
forum: Multimedia Software
---

### Post by illusion123 on 2009-01-25
Hi, 

I built a new desktop using following hardware:
Processor: Intel E7300 core2duo
Motherboard: ECS GF7100pvtm3
               Chipsets:
               North Bridge 	NVIDIA GeForce 7100
               South Bridge 	nForce 630i
RAM: DDR2 4GB

Monitor: Envision H190L
[http://envisiondisplay.com/products.asp?EPage=products&SMenu=h190L](http://envisiondisplay.com/products.asp?EPage=products&SMenu=h190L)

I am facing resolution problem with ubuntu 8.0.4 (i386 version), which is stuck at 800x600. I have tried enabling restricted driver and also through envyNG but nothing helped. I tried downloading and installing nvidia 180 and 171 driver from nvidia website, but that failed. I am attaching the logs here. Can someone help me. Is it a bad hardware or problem with my motherboard? Thanks in advance.

---

### Post by illusion123 on 2009-01-25
looks like my attachment didn't go through last time. I am attaching it here. This is the error snippet from the log:

-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   38.161776] audit(1232913467.596:2): type=1503
   operation="inode_permission" requested_mask="a::" denied_mask="a::"
   name="/dev/tty" pid=4820 profile="/usr/sbin/cupsd" namespace="default"
   [   39.484155] Bluetooth: Core ver 2.11
   [   39.485178] NET: Registered protocol family 31
   [   39.485181] Bluetooth: HCI device and connection manager initialized
   [   39.485184] Bluetooth: HCI socket layer initialized
   [   39.497539] Bluetooth: L2CAP ver 2.9
   [   39.497542] Bluetooth: L2CAP socket layer initialized
   [   39.541119] Bluetooth: RFCOMM socket layer initialized
   [   39.541129] Bluetooth: RFCOMM TTY layer initialized
   [   39.541131] Bluetooth: RFCOMM ver 1.8
   [   42.486087] NET: Registered protocol family 17

  [  483.615359] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 23
   [  483.615363] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [SGRU] -> GSI 23
   (level, low) -> IRQ 16
   [  483.615367] NVRM: This PCI I/O region assigned to your NVIDIA device is
   invalid:
   [  483.615368] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0000:10.0)
   [  483.615369] NVRM: The system BIOS may have misconfigured your graphics
   card.
   [  483.615752] nvidia: probe of 0000:00:10.0 failed with error -1
   [  483.615843] NVRM: The NVIDIA probe routine failed for 1 device(s).
   [  483.615845] NVRM: None of the NVIDIA graphics adapters were initialized!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux


I looked at my bios setup, but only setting available is - Advanced Chipset / VGA Share Memory "Auto Detect"

Thanks

---

### Post by ConfusedNow on 2009-02-05
I've the same problem with Ubuntu 8.10 (and the same hardware too).
I also tried to build nvidia-xconfig from sources and download last 180.22 bin installer from NVIDIA homesite. It tries to build a module for my kernel but it fails due to a "different version of GCC", even if I use gcc 4.3.2 (the same of my kernel)...

I'm exhausted...

---

