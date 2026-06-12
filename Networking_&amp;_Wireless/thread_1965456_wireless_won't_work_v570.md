---
title: "wireless won't work v570"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by MrMagoos on 2012-04-25
Hi there,  I am very new to ubuntu.  My lenovo v570's wireless does not work.  The wire network works just fine.  I ran ```
sudo apt-get update; sudo apt-get install hwinfo grep rfkill; sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep 'acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl';sudo dmidecode|egrep 'anufact|roduct|erial|elease'; iwconfig; cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|wmi|witch|wl'; cat /var/lib/NetworkManager/NetworkManager.state; sudo hwinfo --netcard ; ps -aux|egrep 'wpa|icd|etwork'; sudo lsmod
```and it returned
```
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Get:2 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:4 http://security.ubuntu.com lucid-security Release [57.3kB]
Get:5 http://us.archive.ubuntu.com lucid Release [57.2kB]
Get:6 http://us.archive.ubuntu.com lucid-updates Release [57.3kB]
Get:7 http://security.ubuntu.com lucid-security/main Packages [398kB]          
Get:8 http://us.archive.ubuntu.com lucid/main Packages [1,386kB]
Get:9 http://security.ubuntu.com lucid-security/restricted Packages [2,855B]  
Get:10 http://security.ubuntu.com lucid-security/main Sources [121kB]          
Get:11 http://us.archive.ubuntu.com lucid/restricted Packages [6,208B]         
Get:12 http://us.archive.ubuntu.com lucid/main Sources [659kB]                 
Get:13 http://security.ubuntu.com lucid-security/restricted Sources [1,259B]   
Get:14 http://security.ubuntu.com lucid-security/universe Packages [121kB]
Get:15 http://security.ubuntu.com lucid-security/universe Sources [36.4kB]     
Get:16 http://security.ubuntu.com lucid-security/multiverse Packages [4,558B]  
Get:17 http://security.ubuntu.com lucid-security/multiverse Sources [1,766B]   
Get:18 http://us.archive.ubuntu.com lucid/restricted Sources [3,775B]          
Get:19 http://us.archive.ubuntu.com lucid/universe Packages [5,448kB]
Get:20 http://us.archive.ubuntu.com lucid/universe Sources [3,165kB]
Get:21 http://us.archive.ubuntu.com lucid/multiverse Packages [180kB]
Get:22 http://us.archive.ubuntu.com lucid/multiverse Sources [119kB]
Get:23 http://us.archive.ubuntu.com lucid-updates/main Packages [592kB]
Get:24 http://us.archive.ubuntu.com lucid-updates/restricted Packages [4,617B]
Get:25 http://us.archive.ubuntu.com lucid-updates/main Sources [220kB]
Get:26 http://us.archive.ubuntu.com lucid-updates/restricted Sources [2,194B]
Get:27 http://us.archive.ubuntu.com lucid-updates/universe Packages [263kB]
Get:28 http://us.archive.ubuntu.com lucid-updates/universe Sources [95.5kB]
Get:29 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]
Get:30 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [5,063B]
Fetched 13.0MB in 8s (1,577kB/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grep is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libhd16
The following NEW packages will be installed:
  hwinfo libhd16 rfkill
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 751kB of archives.
After this operation, 2,126kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libhd16 16.0-2 [698kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/universe hwinfo 16.0-2 [46.1kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/universe rfkill 0.3-3 [7,574B]
Fetched 751kB in 1s (545kB/s)    
Selecting previously deselected package libhd16.
(Reading database ... 145523 files and directories currently installed.)
Unpacking libhd16 (from .../libhd16_16.0-2_i386.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2_i386.deb) ...
Selecting previously deselected package rfkill.
Unpacking rfkill (from .../archives/rfkill_0.3-3_i386.deb) ...
Processing triggers for man-db ...
Setting up libhd16 (16.0-2) ...

Setting up hwinfo (16.0-2) ...
Setting up rfkill (0.3-3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 67
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0500000-d0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:6b:9f:44
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.190 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:28 ioport:2000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
02:00.0 Network controller [0280]: Intel Corporation Device [8086:0886] (rev 67)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:58ea Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 8087:07d7  
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path           Device      Class          Description
=========================================================
                               system         1066A9U
/0                             bus            Emerald Lake
/0/0                           memory         128KiB BIOS
/0/30                          processor      Intel(R) Core(TM) i5-2410M CPU @ 2
/0/30/31                       memory         64KiB L1 cache
/0/30/32                       memory         256KiB L2 cache
/0/30/33                       memory         3MiB L3 cache
/0/30/3.1                      processor      Logical CPU
/0/30/3.2                      processor      Logical CPU
/0/30/3.3                      processor      Logical CPU
/0/30/3.4                      processor      Logical CPU
/0/30/3.5                      processor      Logical CPU
/0/30/3.6                      processor      Logical CPU
/0/30/3.7                      processor      Logical CPU
/0/30/3.8                      processor      Logical CPU
/0/30/3.9                      processor      Logical CPU
/0/30/3.a                      processor      Logical CPU
/0/30/3.b                      processor      Logical CPU
/0/30/3.c                      processor      Logical CPU
/0/30/3.d                      processor      Logical CPU
/0/30/3.e                      processor      Logical CPU
/0/30/3.f                      processor      Logical CPU
/0/30/3.10                     processor      Logical CPU
/0/34                          memory         6GiB System Memory
/0/34/0                        memory         4GiB SODIMM Synchronous 1333 MHz (
/0/34/1                        memory         DIMM [empty]
/0/34/2                        memory         2GiB SODIMM Synchronous 1333 MHz (
/0/34/3                        memory         DIMM [empty]
/0/100                         bridge         Intel Corporation
/0/100/2                       display        Intel Corporation
/0/100/16                      communication  Cougar Point HECI Controller #1
/0/100/1a                      bus            Cougar Point USB Enhanced Host Con
/0/100/1b                      multimedia     Cougar Point High Definition Audio
/0/100/1c                      bridge         Cougar Point PCI Express Root Port
/0/100/1c.1                    bridge         Cougar Point PCI Express Root Port
/0/100/1c.1/0                  network        Intel Corporation
/0/100/1c.3                    bridge         Cougar Point PCI Express Root Port
/0/100/1c.3/0      eth0        network        RTL8111/8168B PCI Express Gigabit 
/0/100/1d                      bus            Cougar Point USB Enhanced Host Con
/0/100/1f                      bridge         Intel Corporation
/0/100/1f.2        scsi0       storage        Cougar Point 6 port SATA AHCI Cont
/0/100/1f.2/0      /dev/sda    disk           640GB TOSHIBA MK6465GS
/0/100/1f.2/0/1    /dev/sda1   volume         587GiB EXT4 volume
/0/100/1f.2/0/2    /dev/sda2   volume         8617MiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5   volume         8617MiB Linux swap / Solaris parti
/0/100/1f.2/1      /dev/cdrom  disk           DVD A  DS8A5SH
/0/100/1f.3                    bus            Cougar Point SMBus Controller
/1                             power          Smart Battery
/2                             power          TBD by ODM
Linux tony-laptop 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i686 GNU/Linux
[    0.534468] ACPI: No dock devices found.
[    0.543465] usbcore: registered new interface driver usbfs
[    0.543474] usbcore: registered new interface driver hub
[    0.543498] usbcore: registered new device driver usb
[    0.545824] Switching to clocksource tsc
[    0.549834] pnp: PnP ACPI: found 12 devices
[    0.595567] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.595625] ACPI: Lid Switch [LID0]
[    0.627958] usb usb1: configuration #1 chosen from 1 choice
[    0.627986] hub 1-0:1.0: USB hub found
[    0.647941] usb usb2: configuration #1 chosen from 1 choice
[    0.647969] hub 2-0:1.0: USB hub found
[    0.650980] device-mapper: multipath: version 1.1.0 loaded
[    0.650983] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.654690] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.939683] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.958902] isapnp: No Plug & Play device found
[    1.001205] eth0: RTL8168b/8111b at 0xf80a8000, f0:de:f1:6b:9f:44, XID 0c200000 IRQ 28
[    1.072019] usb 1-1: configuration #1 chosen from 1 choice
[    1.072117] hub 1-1:1.0: USB hub found
[    1.185824] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.318152] usb 2-1: configuration #1 chosen from 1 choice
[    1.318240] hub 2-1:1.0: USB hub found
[    1.393998] usb 1-1.4: new high speed USB device using ehci_hcd and address 3
[    1.490612] usb 1-1.4: configuration #1 chosen from 1 choice
[    1.565904] usb 1-1.5: new high speed USB device using ehci_hcd and address 4
[    1.794574] usb 1-1.5: configuration #1 chosen from 1 choice
[    1.869735] usb 2-1.3: new full speed USB device using ehci_hcd and address 3
[    1.963974] usb 2-1.3: configuration #1 chosen from 1 choice
[    2.033547] usb 2-1.6: new high speed USB device using ehci_hcd and address 4
[    2.126347] usb 2-1.6: configuration #1 chosen from 1 choice
[    6.946968] uvcvideo: Found UVC 1.00 device Lenovo easy camera (0bda:58ea)
[    6.953826] input: Lenovo easy camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[    6.953877] usbcore: registered new interface driver uvcvideo
[    6.978351] lp: driver loaded but no devices found
[    7.421499] Console: switching to colour frame buffer device 80x30
[   12.706135] r8169: eth0: link up
[   12.706151] r8169: eth0: link up
[   23.402846] eth0: no IPv6 routers present
[   35.074420] r8169: eth0: link down
[   64.156437] r8169: eth0: link up
    Release Date: 10/27/2011
        Serial services are supported (int 14h)
    Manufacturer: LENOVO
    Product Name: 1066A9U
    Serial Number: WB02272076WB01061402
    Manufacturer: LENOVO
    Product Name: Emerald Lake
    Serial Number: WB02272076
    Manufacturer: LENOVO
    Serial Number: serial#
    Port Type: Serial Port 16550A Compatible
    Manufacturer: Intel Corp.
    Manufacture Date: 2008
    Serial Number: 1.0
    Manufacturer: TBD by ODM
    Serial Number: TBD by ODM
    Manufacturer: Intel(R) Corporation
    Serial Number: Not Supported by CPU
    Manufacturer: Samsung
    Serial Number: 00500539
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Manufacturer: Samsung
    Serial Number: 00500275
    Manufacturer: Not Specified
    Serial Number: Not Specified
lo        no wireless extensions.

eth0      no wireless extensions.

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist acer-wmi
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist acer-wmi
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist acer-wmi
blacklist uart6850
blacklist twl4030_wdt

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
20: PCI 200.0: 0280 Network controller                          
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_886
  Unique ID: B35A.dmY7n5RpB+5
  Parent ID: qTvu.rWXML16DxOF
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Intel Network controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0886 
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1315 
  Revision: 0x67
  Memory Range: 0xd0500000-0xd0501fff (rw,non-prefetchable)
  IRQ: 10 (no events)
  Module Alias: "pci:v00008086d00000886sv00008086sd00001315bc02sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

21: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8168
  Unique ID: rBUF.8CflRYwxwx9
  Parent ID: Z7uZ.vAJMGJa12x0
  SysFS ID: /devices/pci0000:00/0000:00:1c.3/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x17aa "Lenovo"
  SubDevice: pci 0x3975 
  Revision: 0x06
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x2000-0x2fff (rw)
  Memory Range: 0xd0404000-0xd0404fff (rw,prefetchable)
  Memory Range: 0xd0400000-0xd0403fff (rw,prefetchable)
  IRQ: 28 (36487 events)
  HW Address: f0:de:f1:6b:9f:44
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv000017AAsd00003975bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root       902  0.0  0.1  18896  3928 ?        Ssl  17:24   0:00 NetworkManager
root       909  0.0  0.0   4836  1740 ?        S    17:24   0:00 /sbin/wpa_supplicant -u -s
root      1542  0.0  0.0   2232  1008 ?        S    17:25   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-64864737-05ba-4a57-b8e7-bd862216bb97-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
tony      2585  0.0  0.0   3320   884 pts/0    S+   17:47   0:00 egrep --color=auto wpa|icd|etwork
Module                  Size  Used by
joydev                  8740  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203472  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vga16fb                11385  1 
psmouse                63677  0 
uvcvideo               57438  0 
video                  17375  0 
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
vgastate                8961  1 vga16fb
lp                      7028  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               3978  0 
output                  1871  1 video
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
r8169                  34140  0 
ahci                   32680  2 
mii                     4381  1 r8169

```I was wondering if you guys could tell me what is wrong and help me fix this problem.  Thanks!

---

### Post by chili555 on 2012-04-25
Please let us see:```
modinfo iwlagn | grep 0886
rfkill list all
```Thanks.

---

### Post by MrMagoos on 2012-04-25
rfkill list all doesn't return anything

edit: same with 
modinfo iwlagn | grep 0886

---

### Post by leenfrewin on 2012-04-25
I have the same laptop, and I had the same issue.
This solution worked for me:
[http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution]("http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution")

---

### Post by MrMagoos on 2012-04-25
> **leenfrewin said:**
> I have the same laptop, and I had the same issue.
This solution worked for me:
[http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution](http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution)
doesn't work for me.  I am going to try using the 12.04 lts and see if that fixes all of my MANY issues that I have with this one.

---

### Post by leenfrewin on 2012-04-25
Okay.  I'm using 10.04 LTS.  When I first installed it, the resolution was bad, the wireless didn't work, and a handful of other problems.  I installed a different kernel, and that fixed most things.  Good luck with 12.04.

---

### Post by MrMagoos on 2012-04-25
> **leenfrewin said:**
> Okay.  I'm using 10.04 LTS.  When I first installed it, the resolution was bad, the wireless didn't work, and a handful of other problems.  I installed a different kernel, and that fixed most things.  Good luck with 12.04.
does the 12.04 have a different kernel?  Because I most likely had the same exact problems as you.  This is totally ruining my experience with ubuntu,

---

### Post by chili555 on 2012-04-25
> does the 12.04 have a different kernel?Oh, most definitely. And the driver version iwlwifi claims your wireless device which 10.04 does not:> edit: same with
modinfo iwlagn | grep 0886
On my 12.04 system:```
$ modinfo iwlwifi | grep 0886
alias:          pci:v00008086d0000[COLOR="Red"]0886[/COLOR]sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
```If upgrading is a reasonable option it will solve, at least, your wireless.

---

### Post by leenfrewin on 2012-04-26
> **MrMagoos said:**
> does the 12.04 have a different kernel?  Because I most likely had the same exact problems as you.  This is totally ruining my experience with ubuntu,

Mhmm.
The kernel I'm using right now is 2.6.38-8 generic.
To see what kernel you're using type in terminal:

uname -r

and it should tell you.  If you want to try the kernel i'm using, you can find it here:
[http://packages.ubuntu.com/natty/kernel-image-2.6.38-8-generic-di]("http://packages.ubuntu.com/natty/kernel-image-2.6.38-8-generic-di")
Choose either amd64 or i386 (I'm using amd64.)

After I updated the kernel, the wireless still didn't work, but I used the solution I mentioned earlier, and it runs fine now.

---

