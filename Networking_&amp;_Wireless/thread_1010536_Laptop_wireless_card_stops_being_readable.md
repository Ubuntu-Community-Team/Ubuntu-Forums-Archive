---
title: "Laptop wireless card stops being readable"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Fretsejaz on 2008-12-13
I purchase a dell studio laptop with an intergrated wireless card just recently. Right after getting it I installed ubuntu 8.04 (32-bit distribution from the official website) and after a while, got it all up and running and everything was fine and dandy with the wireless card. Then, out of the blue, I can't connect, I go to the system->adminstration->network    tool and lo and behold I no longer have a wireless connection option. I went through the trouble shooting guide and I can't find my wireless card under the list of devices.

Here is the list:
Falseuser@falsecomputername:~$ sudo lshw -businfo
Bus info          Device      Class       Description
=====================================================
                              system      Studio 1735
                              bus         0H268K
                              memory      64KiB BIOS
cpu@0                         processor   Intel(R) Core(TM)2 Duo CPU     T5800  
                              memory      32KiB L1 cache
                              memory      2MiB L2 cache
                              processor   Logical CPU
                              processor   Logical CPU
                              memory      4GiB System Memory
                              memory      2GiB DIMM DDR Synchronous 667 MHz (1.5
                              memory      2GiB DIMM DDR Synchronous 667 MHz (1.5
pci@0000:00:00.0              bridge      Mobile PM965/GM965/GL960 Memory Contro
pci@0000:00:02.0              display     Mobile GM965/GL960 Integrated Graphics
pci@0000:00:02.1              display     Mobile GM965/GL960 Integrated Graphics
pci@0000:00:1a.0              bus         82801H (ICH8 Family) USB UHCI Controll
pci@0000:00:1a.1              bus         82801H (ICH8 Family) USB UHCI Controll
pci@0000:00:1a.7              bus         82801H (ICH8 Family) USB2 EHCI Control
pci@0000:00:1b.0              multimedia  82801H (ICH8 Family) HD Audio Controll
pci@0000:00:1c.0              bridge      82801H (ICH8 Family) PCI Express Port 
pci@0000:00:1c.1              bridge      82801H (ICH8 Family) PCI Express Port 
pci@0000:0c:00.0              network     BCM4310 USB Controller
pci@0000:00:1c.3              bridge      82801H (ICH8 Family) PCI Express Port 
pci@0000:00:1c.5              bridge      82801H (ICH8 Family) PCI Express Port 
pci@0000:09:00.0  eth0        network     NetLink BCM5784M Gigabit Ethernet PCIe
pci@0000:00:1d.0              bus         82801H (ICH8 Family) USB UHCI Controll
pci@0000:00:1d.1              bus         82801H (ICH8 Family) USB UHCI Controll
pci@0000:00:1d.2              bus         82801H (ICH8 Family) USB UHCI Controll
pci@0000:00:1d.7              bus         82801H (ICH8 Family) USB2 EHCI Control
pci@0000:00:1e.0              bridge      82801 Mobile PCI Bridge
pci@0000:03:01.0              bus         R5C832 IEEE 1394 Controller
pci@0000:03:01.1              system      R5C822 SD/SDIO/MMC/MS/MSPro Host Adapt
pci@0000:03:01.2              system      R5C592 Memory Stick Bus Host Adapter
pci@0000:03:01.3              system      xD-Picture Card Controller
pci@0000:03:01.4              generic     Illegal Vendor ID
pci@0000:00:1f.0              bridge      82801HEM (ICH8M) LPC Interface Control
pci@0000:00:1f.2  scsi0       storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI
scsi@0:0.0.0      /dev/sda    disk        320GB WDC WD3200BEVT-7
scsi@0:0.0.0,1    /dev/sda1   volume      78MiB Windows FAT volume
scsi@0:0.0.0,2    /dev/sda2   volume      10GiB Windows NTFS volume
scsi@0:0.0.0,3    /dev/sda3   volume      37GiB Windows NTFS volume
scsi@0:0.0.0,4    /dev/sda4   volume      250GiB Extended partition
                  /dev/sda5   volume      10GiB Linux swap / Solaris partition
                  /dev/sda6   volume      240GiB Linux filesystem partition
scsi@1:0.0.0      /dev/cdrom  disk        DVD+-RW TS-T633A
pci@0000:00:1f.3              bus         82801H (ICH8 Family) SMBus Controller
                              power       DELL KM9788A

I currently run the computer as a dual boot, a bit for vista (in case things go wrong) and most of it for ubuntu, Vista has no issues with the wireless card.

I can connect via a r45 cable to my DSL modem.

This is my first ask for help, so if I haven't included something, please feel free to tell me.

---

### Post by Fretsejaz on 2008-12-13
Well, I installed the new updates for the OS and it fixed the problem, sorry to bother.

---

