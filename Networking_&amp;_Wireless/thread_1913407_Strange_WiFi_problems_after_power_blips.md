---
title: "Strange WiFi problems after power blips"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by c.cobb on 2012-01-22
Everything was fine until we had a couple of small power blips the other night. They were so short that my UPS alarms didn't even sound. Fairly common here, and I didn't think any more about it.

Now we're having some strange WiFi issues. There are two houses involved, my house and a guest house with some folks who brought PCs and wireless IP phones for work, school, and personal use.

My guests reported that, immediately after the blips, several of their devices would no longer connect or even see the SSID for the Access Point. The strange part is that when walking a couple of the affected devices over into range of a second Access Point, they can connect. Not all of their devices are having problems, and none of my devices have any problems with either AP. A list of the devices is included below.

Before I post a lot of router configs, does anyone know where I might start looking? I've done a 30-second restart of both routers. I'll post some hardware details on the problem PC in a follow-up post.

This really has me baffled, as it seems all of the hardware is okay, and both SSIDs are being broadcast.
Thank you,

Cheesy diagram
```

 My House                                            Guest House
-----------------------------------------------     --------------------
---- these devices have UPS battery backup ----

                         Alcon Router
                     /--[ASU-24005g] AP-1 )))       ((( various devices
                    /
                  Buffalo
 ((( [WiMax ]----[G300NH] AP-2 )))  ((( Laptops
     Receiver     Router            ((( Palm Pre2
                    \    Gateway
                     \--[Desktop PC]
```Before power blip, everything connected fine:
AP-1:
-  1st laptop for work -- Win7
-  2nd laptop for school -- Win7
-  3rd laptop for other -- Win7
-  Android phone
-  Cisco 9971 wireless IP phone
-  Cisco 7925 wireless IP phone

AP-1, and AP-2:
-  my two laptops -- WinXP and Ubuntu
-  my Palm Pre2 phone

After power blip, some no longer see AP-1
-  3rd laptop for other -- Win7
-  Android phone
-  Cisco 9971 wireless IP phone
-  Cisco 7925 wireless IP phone
but the other devices still work fine

However, when walking a couple of the "blind" devices over to my house, they find and connect to "AP-2":
-  3rd laptop for other -- Win7
-  Android phone

Also, just installed inSSIDer on both the 2nd and 3rd laptops. Attached screen shots show that Mike's PC (3rd laptop, image on left) can only find "AP-2" (labeled "AP Casa Verde" in the screen shot), but Alex's PC (2nd laptop, image on right) can see both.

Thanks again for any ideas,

---

### Post by c.cobb on 2012-01-22
I booted Ubuntu from a Live USB on the 3rd laptop that can't see the AP, and ran commands listed on [this support page](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure).

My Live Ubuntu doesn't have the 'hwinfo' command, but if that's necessary, I've downloaded Debs for this command and its dependencies and can reboot, install, and re-run if needed.

When booting my Live Ubuntu on his 3rd laptop, it doesn't find any networking at all... I noticed [a coincidental post](http://ubuntuforums.org/showthread.php?t=1911251) about a similar problem today. Would installing the package mentioned there work on this PC? Windows 7 reports it's using the "Rlink RT5390 802.11b/g/n" driver.
  
sudo lshw -C network >> $OUT 2>&1
rfkill list >> $OUT 2>&1
sudo iwlist scanning >> $OUT 2>&1
cat /etc/network/interfaces >> $OUT 2>&1
cat /etc/lsb-release >> $OUT 2>&1
lspci -nn >> $OUT 2>&1
lsusb >> $OUT 2>&1
sudo lshw -short >> $OUT 2>&1
uname -a >> $OUT 2>&1
dmesg | egrep 'acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl' >> $OUT 2>&1
sudo dmidecode|egrep 'anufact|roduct|erial|elease' >> $OUT 2>&1
iwconfig >> $OUT 2>&1
cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|wmi|witch|wl' >> $OUT 2>&1
cat /var/lib/NetworkManager/NetworkManager.state >> $OUT 2>&1
sudo hwinfo --netcard  >> $OUT 2>&1
ps -aux|egrep 'wpa|icd|etwork' >> $OUT 2>&1
sudo lsmod >> $OUT 2>&1

Output:

```
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d340ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 2c:27:d7:c0:5a:8e
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:2000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: RaLink Device [1814:5390]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
Bus 002 Device 004: ID 090c:37bc Feiya Technology Corp. 
Bus 002 Device 003: ID 3538:0059 Power Quotient International Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path         Device      Class          Description
=======================================================
                             system         HP G62 Notebook PC
/0                           bus            1425
/0/0                         memory         1MiB BIOS
/0/16                        processor      Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
/0/16/17                     memory         3MiB L3 cache
/0/16/19                     memory         256KiB L2 cache
/0/16/1a                     memory         32KiB L1 cache
/0/16/1.1                    processor      Logical CPU
/0/16/1.2                    processor      Logical CPU
/0/16/1.3                    processor      Logical CPU
/0/16/1.4                    processor      Logical CPU
/0/16/1.5                    processor      Logical CPU
/0/16/1.6                    processor      Logical CPU
/0/16/1.7                    processor      Logical CPU
/0/16/1.8                    processor      Logical CPU
/0/16/1.9                    processor      Logical CPU
/0/16/1.a                    processor      Logical CPU
/0/16/1.b                    processor      Logical CPU
/0/16/1.c                    processor      Logical CPU
/0/16/1.d                    processor      Logical CPU
/0/16/1.e                    processor      Logical CPU
/0/16/1.f                    processor      Logical CPU
/0/16/1.10                   processor      Logical CPU
/0/18                        memory         32KiB L1 cache
/0/1b                        memory         4GiB System Memory
/0/1b/0                      memory         2GiB SODIMM Synchronous 1067 MHz (0.9 ns)
/0/1b/1                      memory         2GiB SODIMM Synchronous 1067 MHz (0.9 ns)
/0/100                       bridge         Core Processor DRAM Controller
/0/100/2                     display        Core Processor Integrated Graphics Controller
/0/100/16                    communication  5 Series/3400 Series Chipset HECI Controller
/0/100/1a                    bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1b                    multimedia     5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c/0                  network        RaLink
/0/100/1c.1                  bridge         5 Series/3400 Series Chipset PCI Express Root Port 2
/0/100/1c.1/0    eth0        network        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
/0/100/1d                    bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                    bridge         82801 Mobile PCI Bridge
/0/100/1f                    bridge         Mobile 5 Series Chipset LPC Interface Controller
/0/100/1f.2      scsi0       storage        5 Series/3400 Series Chipset 4 port SATA AHCI Controller
/0/100/1f.2/0    /dev/sda    disk           500GB Hitachi HTS54505
/0/100/1f.2/0/1  /dev/sda1   volume         199MiB Windows NTFS volume
/0/100/1f.2/0/2  /dev/sda2   volume         446GiB Windows NTFS volume
/0/100/1f.2/0/3  /dev/sda3   volume         19GiB Windows NTFS volume
/0/100/1f.2/0/4  /dev/sda4   volume         103MiB Windows FAT volume
/0/100/1f.2/1    /dev/cdrom  disk           CDDVDW TS-L633R
/0/100/1f.3                  bus            5 Series/3400 Series Chipset SMBus Controller
/0/100/1f.6                  generic        5 Series/3400 Series Chipset Thermal Subsystem
/0/101                       bridge         Core Processor QuickPath Architecture Generic Non-core Registers
/0/102                       bridge         Core Processor QuickPath Architecture System Address Decoder
/0/103                       bridge         Core Processor QPI Link 0
/0/104                       bridge         Core Processor QPI Physical 0
/0/105                       bridge         Core Processor Reserved
/0/106                       bridge         Core Processor Reserved
/0/1             scsi4       storage        
/0/1/0.0.0       /dev/sdb    disk           SCSI Disk
/0/2             scsi5       storage        
/0/2/0.0.0       /dev/sdc    disk           4043MB SCSI Disk
/0/2/0.0.0/1     /dev/sdc1   volume         3852MiB Windows FAT volume
/1                           power          MU06047
Linux custom 2.6.32-36-generic #79-Ubuntu SMP Tue Nov 8 22:29:26 UTC 2011 i686 GNU/Linux
[    0.000000] Kernel command line: initrd=/ubuntu-ebank/casper/initrd.gz boot=casper quickreboot noprompt noswap nopersistent ignore_uuid live-media-path=/ubuntu-ebank/casper iso-scan/filename=/ubuntu-ebank/md5sum.txt splash -- BOOT_IMAGE=/ubuntu-ebank/casper/vmlinuz 
[    0.598970] ACPI: No dock devices found.
[    0.623265] usbcore: registered new interface driver usbfs
[    0.623337] usbcore: registered new interface driver hub
[    0.623427] usbcore: registered new device driver usb
[    0.626584] Switching to clocksource tsc
[    0.632415] pnp: PnP ACPI: found 11 devices
[    0.668524] pci 0000:03:00.0: BAR 6: no parent found for of device [0xffff0000-0xffffffff]
[    0.722042] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.722560] ACPI: Lid Switch [LID0]
[    0.786955] usb usb1: configuration #1 chosen from 1 choice
[    0.787056] hub 1-0:1.0: USB hub found
[    0.806901] usb usb2: configuration #1 chosen from 1 choice
[    0.806997] hub 2-0:1.0: USB hub found
[    0.826903] device-mapper: multipath: version 1.1.0 loaded
[    0.826969] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.833019] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.097423] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.128418] isapnp: No Plug & Play device found
[    1.193118] eth0: RTL8102e at 0xf810a000, 2c:27:d7:c0:5a:8e, XID 04e00000 IRQ 27
[    1.230501] usb 1-1: configuration #1 chosen from 1 choice
[    1.230672] hub 1-1:1.0: USB hub found
[    1.341552] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.473856] usb 2-1: configuration #1 chosen from 1 choice
[    1.474107] hub 2-1:1.0: USB hub found
[    1.549375] usb 1-1.5: new high speed USB device using ehci_hcd and address 3
[    1.652469] usb 1-1.5: configuration #1 chosen from 1 choice
[    1.663999] usbcore: registered new interface driver usb-storage
[    1.664380] usb-storage: device found at 3
[    1.664382] usb-storage: waiting for device to settle before scanning
[    1.748985] usb 2-1.1: new high speed USB device using ehci_hcd and address 3
[    1.847759] usb 2-1.1: configuration #1 chosen from 1 choice
[    1.848197] usb-storage: device found at 3
[    1.848199] usb-storage: waiting for device to settle before scanning
[    1.917439] usb 2-1.5: new high speed USB device using ehci_hcd and address 4
[    2.017191] usb 2-1.5: configuration #1 chosen from 1 choice
[    2.471221] Console: switching to colour frame buffer device 170x48
[    6.653161] usb-storage: device scan complete
[    6.836618] usb-storage: device scan complete
[   25.293869] lp: driver loaded but no devices found
[   25.312348] uvcvideo: Found UVC 1.00 device HP Webcam-101 (090c:37bc)
[   25.313541] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input6
[   25.313597] usbcore: registered new interface driver uvcvideo
[   26.361929] r8169: eth0: link down
[   26.362051] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.512075] vboxguest: VirtualBox Guest PCI device not found.
    Release Date: 02/08/2011
    Manufacturer: Hewlett-Packard
    Product Name: HP G62 Notebook PC
    Serial Number: CNF1152SMK
    Manufacturer: Hewlett-Packard
    Product Name: 1425
    Serial Number: PX11R011Z09GRD
    Manufacturer: Hewlett-Packard
    Serial Number: None
    Option 1: String1 for Type12 Equipment Manufacturer
    Option 2: String2 for Type12 Equipment Manufacturer
    Option 3: String3 for Type12 Equipment Manufacturer
    Option 4: String4 for Type12 Equipment Manufacturer
    Manufacturer: 13-54
    SBDS Serial Number: 2B3C
    SBDS Manufacture Date: 2010-12-24
    Manufacturer: Intel(R) Corporation
    Serial Number: Not Specified
    Manufacturer: Samsung
    Serial Number: 87669AFB
    Manufacturer: Samsung
    Serial Number: 87669AF3
lo        no wireless extensions.

eth0      no wireless extensions.

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
sudo: hwinfo: command not found
root      2070  0.0  0.1   8332  3632 ?        Ss   02:57   0:00 NetworkManager
root      2133  0.0  0.0   4836  1736 ?        S    02:57   0:00 /sbin/wpa_supplicant -u -s
custom    3643  0.0  0.0   3324   828 pts/0    R+   03:00   0:00 egrep wpa|icd|etwork
Module                  Size  Used by
binfmt_misc             6587  1 
dm_crypt               11331  0 
joydev                  8740  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203408  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
uvcvideo               57406  0 
lp                      7028  0 
soundcore               6620  1 snd
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
parport                32635  1 lp
squashfs               20744  1 
aufs                  149050  1 
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8933  2 
fat                    47767  1 vfat
jfs                   172461  0 
xfs                   513552  0 
exportfs                3437  1 xfs
reiserfs              225481  0 
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usb_storage            39905  1 
i915                  289683  3 
drm_kms_helper         29329  1 i915
drm                   163747  4 i915,drm_kms_helper
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
intel_agp              24375  2 i915
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video

```

---

### Post by c.cobb on 2012-01-30
So, tonight we had inSSIDer running on the two PCs side-by-side: One could see the SSID and connect, no problems. The other still could not see the SSID. The SSID was showing up on channel 13, while my guest remembered that originally, when things were working, it was on channel 11.

I logged into the AP and changed the Wireless setting from "SmartSelect" and forced it to broadcast on channel 11. 

The one PC that could see the SSID immediately noticed the change and continued to work. The other PC could immediately see the SSID again and was then able to connect. After that, my guest was able to get his other devices to work again. 

It works, but I have no idea why. Any ideas?

(FWIW, before making the change, I confirmed that the other AP was not broadcasting on that channel.)

---

### Post by c.cobb on 2012-01-31
Two words: Regulatory Domain. 

Channels 1 - 11 for U.S., 12 - 14 in various other locations.

---

