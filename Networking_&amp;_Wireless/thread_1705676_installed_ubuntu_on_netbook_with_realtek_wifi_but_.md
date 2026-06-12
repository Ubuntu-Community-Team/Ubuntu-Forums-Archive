---
title: "installed ubuntu on netbook with realtek wifi but wifi doesnt exist????"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by perlex on 2011-03-12
I have a realtek wlan card installed on my toshiba netbook 505 but when i do run iwconfig it just shows
 
lo
eth0

how can i enable my wireless to work?

---

### Post by bkratz on 2011-03-12
> **perlex said:**
> I have a realtek wlan card installed on my toshiba netbook 505 but when i do run iwconfig it just shows
 
lo
eth0

how can i enable my wireless to work?



You might want to post the terminal output of

```
lspci | grep Network
```

which should show what wireless card you have, if not look at lspci and visually determine it.

---

### Post by perlex on 2011-03-12
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

---

### Post by perlex on 2011-03-13
It says that i have realtek 8190 pci wireless card installed

---

### Post by perlex on 2011-03-13
Ok I typed into the terminal window;

sudo apt-get update; sudo apt-get install hwinfo grep; sudo lshw -C  network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl'; iwconfig; cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'; sudo hwinfo --netcard ; cat /var/lib/NetworkManager/NetworkManager.state; sudo lsmod




and here is my result:




ldconfig deferred processing now taking place
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:76:fd:72
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.10.5.222 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path               Device     Class       Description
=========================================================
                                  system      TOSHIBA NB505
/0                                bus         PBU00
/0/0                              memory      100KiB BIOS
/0/4                              processor   Intel(R) Atom(TM) CPU N455   @ 1.6
/0/4/5                            memory      32KiB L1 cache
/0/4/6                            memory      512KiB L2 cache
/0/4/1.1                          processor   Logical CPU
/0/4/1.2                          processor   Logical CPU
/0/c                              memory      1GiB System Memory
/0/c/0                            memory      1GiB SODIMM DDR2 Synchronous 667 M
/0/c/1                            memory      SODIMM DDR Synchronous 667 MHz (1.
/0/100                            bridge      N10 Family DMI Bridge
/0/100/2                          display     N10 Family Integrated Graphics Con
/0/100/2.1                        display     N10 Family Integrated Graphics Con
/0/100/1b                         multimedia  N10/ICH 7 Family High Definition A
/0/100/1c                         bridge      N10/ICH 7 Family PCI Express Port 
/0/100/1c.1                       bridge      N10/ICH 7 Family PCI Express Port 
/0/100/1c.1/0                     network     Realtek Semiconductor Co., Ltd.
/0/100/1c.2                       bridge      N10/ICH 7 Family PCI Express Port 
/0/100/1c.2/0          eth0       network     RTL8101E/RTL8102E PCI Express Fast
/0/100/1d                         bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.1                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.2                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.3                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.7                       bus         N10/ICH 7 Family USB2 EHCI Control
/0/100/1e                         bridge      82801 Mobile PCI Bridge
/0/100/1f                         bridge      NM10 Family LPC Controller
/0/100/1f.2            scsi0      storage     N10/ICH7 Family SATA AHCI Controll
/0/100/1f.2/0.0.0      /dev/sda   disk        250GB TOSHIBA MK2565GS
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      229GiB EXT4 volume
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      2997MiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5  volume      2997MiB Linux swap / Solaris parti
/0/100/1f.3                       bus         N10/ICH 7 Family SMBus Controller
/0/1                   scsi4      storage     
/0/1/0.0.0             /dev/sdb   disk        SCSI Disk
/1                                power       PA3395U
Linux hwnd-TOSHIBA-NB505 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux
[    0.000000] found SMP MP-table at [c00f7d50] f7d50
[    0.257885] ACPI: No dock devices found.
[    0.260925] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.260946] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.268100] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.278646] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.301656] HEST: Table is not found!
[    0.302752] usbcore: registered new interface driver usbfs
[    0.302803] usbcore: registered new interface driver hub
[    0.302879] usbcore: registered new device driver usb
[    0.308107] Switching to clocksource tsc
[    0.361244] pnp: PnP ACPI: found 8 devices
[    0.742206] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.742476] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.742734] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.743025] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.743282] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.743538] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[    0.743991] Switching to clocksource hpet
[    0.744652] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/PNP0C0D:00/input/input0
[    0.744729] ACPI: Lid Switch [LID0]
[    0.771251] ERST: Table is not found!
[    0.779268] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.799317] hub 1-0:1.0: USB hub found
[    0.800267] hub 2-0:1.0: USB hub found
[    0.800948] hub 3-0:1.0: USB hub found
[    0.801614] hub 4-0:1.0: USB hub found
[    0.802270] hub 5-0:1.0: USB hub found
[    0.824417] device-mapper: multipath: version 1.1.1 loaded
[    0.824429] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.830304] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.125394] isapnp: No Plug & Play device found
[    1.260064] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.531643] r8169 0000:09:00.0: eth0: RTL8101e at 0xf80ac000, 1c:75:08:76:fd:72, XID 00900000 IRQ 44
[    1.677079] scsi4 : usb-storage 1-4:1.0
[    1.677354] usbcore: registered new interface driver usb-storage
[    1.768069] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    2.172076] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.406968] usbcore: registered new interface driver hiddev
[    2.411058] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
[    2.411390] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    2.417504] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input5
[    2.418517] generic-usb 0003:046D:C52F.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    2.418597] usbcore: registered new interface driver usbhid
[    2.418604] usbhid: USB HID core driver
[   12.234560] lp: driver loaded but no devices found
[   12.843336] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   13.083044] uvcvideo: Found UVC 1.00 device CNF9055 (04f2:b1d6)
[   13.103555] input: CNF9055 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
[   13.105255] usbcore: registered new interface driver uvcvideo
[   13.262659] usbcore: registered new interface driver ndiswrapper
[   14.240831] r8169 0000:09:00.0: eth0: link down
[   14.241412] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.576271] Console: switching to colour frame buffer device 128x37
[  269.377446] r8169 0000:09:00.0: eth0: link up
[  269.378115] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  279.872057] eth0: no IPv6 routers present
lo        no wireless extensions.

eth0      no wireless extensions.

blacklist rtl8190
blacklist wl
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
options iwlagn 11n_disable=1
alias pci:v000010ECd00008176sv00000315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001139sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001629sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001A39sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002057sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002A57sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003824sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003874sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007185sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007611sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008194sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008197sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000824Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000874Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009196sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009197sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008177sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008185sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008191sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00000035sd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00000066sd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00000CD6sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00006894sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv0000831Fsd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008341sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv*sd*bc*sc*i* ndiswrapper
alias usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8199d*dc*dsc*dp*ic*isc*ip* ndiswrapper
> hal.1: read hal dataprocess 3745: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
24: PCI 700.0: 0280 Network controller                          
  [Created at pci.318]
  Unique ID: aK5u.8tgfMAdnug1
  Parent ID: qTvu._YnTqJrwYv4
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:07:00.0
  SysFS BusID: 0000:07:00.0
  Hardware Class: network
  Model: "Realtek Network controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8176 
  SubVendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  SubDevice: pci 0x8181 
  Revision: 0x01
  I/O Ports: 0x2000-0x2fff (rw)
  Memory Range: 0xf0100000-0xf0103fff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v000010ECd00008176sv000010ECsd00008181bc02sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)

25: PCI 900.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.Td1o4Dx_iM8
  Parent ID: hoOk.0OgznS4Lcg5
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:09:00.0
  SysFS BusID: 0000:09:00.0
  Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0xfdc0 
  Revision: 0x05
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x3000-0x3fff (rw)
  Memory Range: 0xf050c000-0xf050cfff (ro,non-prefetchable)
  Memory Range: 0xf0508000-0xf050bfff (ro,non-prefetchable)
  IRQ: 44 (21647 events)
  HW Address: 1c:75:08:76:fd:72
  Link detected: yes
  Module Alias: "pci:v000010ECd00008136sv00001179sd0000FDC0bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
i915                  295435  3 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
drm_kms_helper         30200  1 i915
drm                   168060  3 i915,drm_kms_helper
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26566  2 i915
ndiswrapper           184207  0 
psmouse                59033  0 
videodev               43098  1 uvcvideo
joydev                  8767  0 
i2c_algo_bit            5168  1 i915
serio_raw               4022  0 
v4l1_compat            13359  2 uvcvideo,videodev
video                  18712  1 i915
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40204  0 
r8169                  36521  0 
ahci                   19198  2 
libahci                21728  1 ahci
mii                     4425  1 r8169

---

### Post by bkratz on 2011-03-13
See posts 29 and 30 of this thread. He/she has the same card and gives instructions.

[http://ubuntuforums.org/showthread.php?t=1689148&page=3](http://ubuntuforums.org/showthread.php?t=1689148&page=3)

---

