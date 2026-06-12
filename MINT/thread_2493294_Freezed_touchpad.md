---
title: "Freezed touchpad"
date: 2023-12-09
forum: MINT
---

### Post by alebalweb on 2023-12-09
Hi, for a few days now the touchpad on my laptop has been freezing without any warning or apparent reason...

It seems like a software problem because if I turn off, restart, or suspend the PC, as soon as I turn it back on, already on the login screen, the touchpad works perfectly...

What can I do to try to resolve it?


```
hostnamectl
 Static hostname: alebal-ssd
       Icon name: computer-laptop
         Chassis: laptop
      Machine ID: b0d275fb46fa48c6820be57edaa22cf5
         Boot ID: 6baf7930d19f4d97a5843c9729549a60
Operating System: Linux Mint 21.2                 
          Kernel: Linux 5.15.0-91-generic
    Architecture: x86-64
 Hardware Vendor: Dell Inc.
  Hardware Model: Inspiron 15 7000 Gaming




sudo lshw -short
[sudo] password for alebal:               
H/W path           Device          Class          Description
=============================================================
                                   system         Inspiron 15 7000 Gaming (0798)
/0                                 bus            065C71
/0/0                               memory         64KiB BIOS
/0/44                              memory         8GiB System Memory
/0/44/0                            memory         8GiB SODIMM DDR4 Synchronous 2400 MHz (0.4 ns)
/0/44/1                            memory         DIMM [empty]
/0/48                              memory         256KiB L1 cache
/0/49                              memory         1MiB L2 cache
/0/4a                              memory         6MiB L3 cache
/0/4b                              processor      Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
/0/100                             bridge         Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
/0/100/1                           bridge         6th-10th Gen Core Processor PCIe Controller (x16)
/0/100/1/0                         display        GP107M [GeForce GTX 1050 Ti Mobile]
/0/100/1/0.1       card1           multimedia     GP107GL High Definition Audio Controller
/0/100/1/0.1/0     input15         input          HDA NVidia HDMI/DP,pcm=3
/0/100/1/0.1/1     input16         input          HDA NVidia HDMI/DP,pcm=7
/0/100/1/0.1/2     input17         input          HDA NVidia HDMI/DP,pcm=8
/0/100/1/0.1/3     input18         input          HDA NVidia HDMI/DP,pcm=9
/0/100/2           /dev/fb0        display        HD Graphics 630
/0/100/4                           generic        Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
/0/100/14                          bus            100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller
/0/100/14/0        usb1            bus            xHCI Host Controller
/0/100/14/0/4                      communication  Bluetooth wireless interface
/0/100/14/0/c                      multimedia     Integrated Webcam
/0/100/14/1        usb2            bus            xHCI Host Controller
/0/100/14.2                        generic        100 Series/C230 Series Chipset Family Thermal Subsystem
/0/100/15                          generic        100 Series/C230 Series Chipset Family Serial IO I2C Controller #0
/0/100/15.1                        generic        100 Series/C230 Series Chipset Family Serial IO I2C Controller #1
/0/100/16                          communication  100 Series/C230 Series Chipset Family MEI Controller #1
/0/100/17          scsi1           storage        HM170/QM170 Chipset SATA Controller [AHCI Mode]
/0/100/17/0.0.0    /dev/sda        disk           1TB ST1000LX015-1U71
/0/100/17/0.0.0/1  /dev/sda1       volume         50MiB Windows NTFS volume
/0/100/17/0.0.0/2  /dev/sda2       volume         491GiB Windows NTFS volume
/0/100/17/0.0.0/3  /dev/sda3       volume         530MiB Windows NTFS volume
/0/100/17/0.0.0/4  /dev/sda4       volume         439GiB EXT4 volume
/0/100/1c                          bridge         100 Series/C230 Series Chipset Family PCI Express Root Port #5
/0/100/1c/0        enp2s0          network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1c.5                        bridge         100 Series/C230 Series Chipset Family PCI Express Root Port #6
/0/100/1c.5/0      wlp3s0          network        Wireless 3165
/0/100/1d                          bridge         100 Series/C230 Series Chipset Family PCI Express Root Port #9
/0/100/1d/0        /dev/nvme0      storage        KINGSTON RBUSNS8154P3256GJ1
/0/100/1d/0/0      hwmon3          disk           NVMe disk
/0/100/1d/0/2      /dev/ng0n1      disk           NVMe disk
/0/100/1d/0/1      /dev/nvme0n1    disk           256GB NVMe disk
/0/100/1d/0/1/1    /dev/nvme0n1p1  volume         511MiB Windows FAT volume
/0/100/1d/0/1/2    /dev/nvme0n1p2  volume         237GiB EXT4 volume
/0/100/1f                          bridge         HM175 Chipset LPC/eSPI Controller
/0/100/1f/0                        system         PnP device PNP0c02
/0/100/1f/1                        system         PnP device PNP0c02
/0/100/1f/2                        system         PnP device PNP0b00
/0/100/1f/3                        generic        PnP device INT3f0d
/0/100/1f/4                        input          PnP device PNP0303
/0/100/1f/5                        generic        PnP device DLL0767
/0/100/1f/6                        system         PnP device PNP0c02
/0/100/1f/7                        system         PnP device PNP0c02
/0/100/1f/8                        system         PnP device PNP0c02
/0/100/1f/9                        system         PnP device PNP0c02
/0/100/1f.2                        memory         Memory controller
/0/100/1f.3        card0           multimedia     CM238 HD Audio Controller
/0/100/1f.3/0      input23         input          HDA Intel PCH Headphone Mic
/0/100/1f.4                        bus            100 Series/C230 Series Chipset Family SMBus
/1                                 power          DELL 0GFJ675
/2                 input0          input          Lid Switch
/3                 input1          input          Power Button
/4                 input10         input          Video Bus
/5                 input11         input          Video Bus
/6                 input12         input          Intel HID events
/7                 input13         input          Intel HID 5 button array
/8                 input14         input          Integrated Webcam: Integrated W
/9                 input19         input          DLL0798:00 06CB:7E92 Mouse
/a                 input2          input          Sleep Button
/b                 input20         input          DLL0798:00 06CB:7E92 Touchpad
/c                 input22         input          Dell WMI hotkeys
/d                 input3          input          Power Button
/e                 input4          input          AT Translated Set 2 keyboard


```

---

