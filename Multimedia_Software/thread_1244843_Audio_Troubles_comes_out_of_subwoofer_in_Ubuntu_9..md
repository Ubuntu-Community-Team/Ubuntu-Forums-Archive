---
title: "Audio Troubles: comes out of subwoofer in Ubuntu 9.04"
date: 2009-08-19
forum: Multimedia Software
---

### Post by JFlou on 2009-08-19
I recently received a new laptop and run it in a triple boot environment of Ubuntu 9.04, Windows Vista Home Premium and Windows 7 RT Edition. I have recently found out that when i'm logged into my Ubuntu boot, when I play any audio files or anything that has sound, the sound only comes from the subwoofer and not from the four other speakers installed in the laptop. In contrast, on both my Windows Vista and 7 boots, the audio works fine without a hitch. I've updated the alsa audio drivers to 1.19 and have been searching for a solution for weeks with no luck.

Here are the specs of my machine according to lshw -short in terminal:

jflou@jflou-laptop:~$ sudo lshw -short
H/W path             Device      Class       Description
========================================================
                                 system      GT735
/0                               bus         MS-1721
/0/0                             memory      64KiB BIOS
/0/4                             processor   AMD Turion(tm) X2 Ultra Dual-Core M
/0/4/5                           memory      128KiB L1 cache
/0/4/6                           memory      1MiB L2 cache
/0/4/7                           memory      L3 cache
/0/25                            memory      4GiB System Memory
/0/25/0                          memory      2GiB DIMM Synchronous 333 MHz (3.0 
/0/25/1                          memory      2GiB DIMM Synchronous 333 MHz (3.0 
/0/1                             processor   
/0/1/0                           memory      128KiB L1 cache
/0/1/1                           memory      1MiB L2 cache
/0/100                           bridge      RS780 Host Bridge
/0/100/2                         bridge      RS780 PCI to PCI bridge (ext gfx po
/0/100/2/0                       display     Mobility Radeon HD 3850
/0/100/2/0.1                     multimedia  Radeon HD 3870 Audio device
/0/100/4                         bridge      RS780 PCI to PCI bridge (PCIE port 
/0/100/5                         bridge      RS780 PCI to PCI bridge (PCIE port 
/0/100/5/0           ra0         network     RT2860
/0/100/6                         bridge      RS780 PCI to PCI bridge (PCIE port 
/0/100/7                         bridge      RS780 PCI to PCI bridge (PCIE port 
/0/100/7/0           eth0        network     RTL8111/8168B PCI Express Gigabit E
/0/100/9                         bridge      RS780 PCI to PCI bridge (PCIE port 
/0/100/9/0                       bus         IEEE 1394 Host Controller
/0/100/9/0.1                     system      SD/MMC Host Controller
/0/100/9/0.2                     system      Standard SD Host Controller
/0/100/9/0.3                     system      MS Host Controller
/0/100/9/0.4                     system      xD Host Controller
/0/100/11            scsi0       storage     SB700/SB800 SATA Controller [AHCI m
/0/100/11/0.0.0      /dev/sda    disk        320GB FUJITSU MHZ2320B
/0/100/11/0.0.0/1    /dev/sda1   volume      24GiB Windows NTFS volume
/0/100/11/0.0.0/2    /dev/sda2   volume      43GiB Windows NTFS volume
/0/100/11/0.0.0/3    /dev/sda3   volume      206GiB Windows NTFS volume
/0/100/11/0.0.0/4    /dev/sda4   volume      15GiB Extended partition
/0/100/11/0.0.0/4/5  /dev/sda5   volume      15GiB Linux filesystem partition
/0/100/11/0.0.0/4/6  /dev/sda6   volume      721MiB Linux swap / Solaris partiti
/0/100/12                        bus         SB700/SB800 USB OHCI0 Controller
/0/100/12.1                      bus         SB700 USB OHCI1 Controller
/0/100/12.2                      bus         SB700/SB800 USB EHCI Controller
/0/100/13                        bus         SB700/SB800 USB OHCI0 Controller
/0/100/13.2                      bus         SB700/SB800 USB EHCI Controller
/0/100/14                        bus         SBx00 SMBus Controller
/0/100/14.1          scsi4       storage     SB700/SB800 IDE Controller
/0/100/14.1/0.0.0    /dev/cdrom  disk        DVD RW AD-7560S
/0/100/14.1/0.0.0/0  /dev/cdrom  disk        
/0/100/14.2                      multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                      bridge      SB700/SB800 LPC host controller
/0/100/14.4                      bridge      SBx00 PCI to PCI Bridge
/0/101                           bridge      Family 11h HyperTransport Configura
/0/102                           bridge      Family 11h Address Map
/0/103                           bridge      Family 11h DRAM Controller
/0/104                           bridge      Family 11h Miscellaneous Control
/0/105                           bridge      Family 11h Link Control
/1                   pan0        network     Ethernet interface

This may have already been solved elsewhere so I apologise in advance.

---

