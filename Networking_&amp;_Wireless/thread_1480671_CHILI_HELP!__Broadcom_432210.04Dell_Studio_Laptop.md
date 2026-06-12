---
title: "CHILI HELP!  Broadcom 4322/10.04/Dell Studio Laptop"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by jschille on 2010-05-11
EDIT: Problem has been solved.  
```
 sudo apt-get remove --purge linux-backports-modules-*
```Then System-->Admin-->Hardware Drivers
Click on the STA Driver
Click Remove
Click Activate
Restart
and should be up and running!
-------------------------------------------------------------------------------------------

_ORIGINAL POST_

After fumbling around with this for the past few days the problems I have noticed are.
(1) Broadcom STA Driver Activated **but not in use.**
(2) network is UNCLAIMED

Problems that I am having: Cannot view Wireless Networks, when I click I can only see Wired Networks, Wireless Networks does not even come up.

Chili, if you are out there i'd love some help! I see you everywhere in this forum, come to me! :)

lspci
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)
06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```lsusb
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ca:18a3 Ricoh Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:22:19:f7:92:be  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fef7:92be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1917228 (1.9 MB)  TX bytes:263387 (263.3 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1439580 (1.4 MB)  TX bytes:1439580 (1.4 MB)

```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:f7:92:be
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.6 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:f0888000-f0888fff ioport:30d0(size=8) memory:f0889c00-f0889cff memory:f0889800-f088980f
  *-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f0403fff

```If anyone can help that would be great. I am getting desperate.

---

### Post by bkratz on 2010-05-11
Dr. Chili is probably getting some coffee, in the mean time can you attach your wired cable and simply try to disable the driver and re-enable and see if your wireless comes back, if it does let us know.


It is just wireless don't get desperate!

---

### Post by jschille on 2010-05-11
> **bkratz said:**
> Dr. Chili is probably getting some coffee, in the mean time can you attach your wired cable and simply try to disable the driver and re-enable and see if your wireless comes back, if it does let us know.


It is just wireless don't get desperate!

hehe, thanks for the reply. just gets frustrating after trying so many things!

I have disabled the driver and re-enabled and it did not fix the problem.
After disabling and re-enabling it states "Activated, but not in use"

---

### Post by bkratz on 2010-05-11
Could you copy/paste the output of  (fairly long so use code tags)

lsmod

that is LSMOD in lowercase and 

cat /etc/modules
rfkill list

---

### Post by jschille on 2010-05-11
[B]lsmod
[/B]```
Module                  Size  Used by
snd_hda_codec_nvhdmi     4760  1 
snd_hda_codec_idt      61418  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
joydev                 11072  0 
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
dell_wmi                2177  0 
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
lib80211                6183  0 
dell_laptop             7941  0 
dcdbas                  6886  1 dell_laptop
snd                    70978  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  0 
vgastate                9857  1 vga16fb
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  1 sdhci
soundcore               8052  1 snd
psmouse                64608  0 
serio_raw               4918  0 
i2c_nforce2             6099  0 
nvidia              10799466  40 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
shpchp                 33679  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvesafb                24962  1 
ohci1394               30260  0 
video                  20623  0 
output                  2503  1 video
ieee1394               94675  1 ohci1394
ahci                   37646  2 
forcedeth              55592  0

```**cat /etc/modules**
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```[B]rfkill list
[/B]nothing came up for this command, just sent me to a new line
     Edit: When typing in 'rfkill' I can see a command that is 'rfkill list [IDENTIFIER]' what should i put in for that identifier?

---

### Post by bkratz on 2010-05-11
I'll have to look into the rfkill list command-- I thought that was enough. Anyway, I don't see the STA (wl) modules listed in the lsmod listing or in /etc/modules at all,  unless I just missed it, I think I will get some coffee myself.

See what errors 

sudo modprobe wl 

produces if any, with luck maybe that is all that is needed, for now.

---

### Post by bkratz on 2010-05-11
By the way, I found a whole lot of people with this same problem on that particular card with a google search.  I only found one that claims success though.

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

---

### Post by jschille on 2010-05-11
> **bkratz said:**
> I'll have to look into the rfkill list command-- I thought that was enough. Anyway, I don't see the STA (wl) modules listed in the lsmod listing or in /etc/modules at all,  unless I just missed it, I think I will get some coffee myself.

See what errors 

sudo modprobe wl 

produces if any, with luck maybe that is all that is needed, for now.

well i got an error, says it's FATAL
```
ATAL: Error inserting wl (/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```enjoy your coffee, ill be here!

Edit: it said see dmesg so here is that output. it's so big i don't think i got the very top...
```
[    0.421504] AppArmor: AppArmor Filesystem Enabled
[    0.421514] pnp: PnP ACPI init
[    0.421525] ACPI: bus type pnp registered
[    0.422455] pnp 00:03: mem resource (0xf0600000-0xf0607fff) overlaps 0000:00:03.5 BAR 0 (0xf0600000-0xf067ffff), disabling
[    0.425600] pnp: PnP ACPI: found 13 devices
[    0.425602] ACPI: ACPI bus type pnp unregistered
[    0.425611] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.425613] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.425616] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.425618] system 00:00: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.425625] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.425628] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.425630] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.425632] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.425634] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.425636] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.425640] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.425642] system 00:07: ioport range 0x910-0x911 has been reserved
[    0.425645] system 00:07: ioport range 0x295-0x296 has been reserved
[    0.430424] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    0.430426] pci 0000:00:09.0:   IO window: disabled
[    0.430429] pci 0000:00:09.0:   MEM window: 0xf0500000-0xf05fffff
[    0.430432] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.430438] pci 0000:02:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.430440] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:02
[    0.430445] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.430455] pci 0000:00:0c.0:   MEM window: 0xac000000-0xaeffffff
[    0.430462] pci 0000:00:0c.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.430475] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.430477] pci 0000:00:10.0:   IO window: 0x5000-0x5fff
[    0.430480] pci 0000:00:10.0:   MEM window: 0xaa000000-0xaaffffff
[    0.430482] pci 0000:00:10.0:   PREFETCH window: 0x000000b0000000-0x000000cdffffff
[    0.430486] pci 0000:00:15.0: PCI bridge, secondary bus 0000:04
[    0.430490] pci 0000:00:15.0:   IO window: 0x6000-0x6fff
[    0.430500] pci 0000:00:15.0:   MEM window: 0xf0200000-0xf03fffff
[    0.430508] pci 0000:00:15.0:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.430521] pci 0000:00:16.0: PCI bridge, secondary bus 0000:06
[    0.430522] pci 0000:00:16.0:   IO window: disabled
[    0.430531] pci 0000:00:16.0:   MEM window: 0xf0400000-0xf04fffff
[    0.430538] pci 0000:00:16.0:   PREFETCH window: disabled
[    0.430551] pci 0000:00:17.0: PCI bridge, secondary bus 0000:07
[    0.430552] pci 0000:00:17.0:   IO window: disabled
[    0.430562] pci 0000:00:17.0:   MEM window: disabled
[    0.430568] pci 0000:00:17.0:   PREFETCH window: disabled
[    0.430581] pci 0000:00:18.0: PCI bridge, secondary bus 0000:08
[    0.430582] pci 0000:00:18.0:   IO window: disabled
[    0.430591] pci 0000:00:18.0:   MEM window: disabled
[    0.430598] pci 0000:00:18.0:   PREFETCH window: disabled
[    0.430617] pci 0000:00:09.0: setting latency timer to 64
[    0.430904] ACPI: PCI Interrupt Link [Z00Q] enabled at IRQ 23
[    0.430907]   alloc irq_desc for 23 on node -1
[    0.430908]   alloc kstat_irqs on node -1
[    0.430913] pci 0000:00:0c.0: PCI INT A -> Link[Z00Q] -> GSI 23 (level, low) -> IRQ 23
[    0.430921] pci 0000:00:0c.0: setting latency timer to 64
[    0.430928] pci 0000:00:10.0: setting latency timer to 64
[    0.431203] ACPI: PCI Interrupt Link [Z012] enabled at IRQ 22
[    0.431206]   alloc irq_desc for 22 on node -1
[    0.431207]   alloc kstat_irqs on node -1
[    0.431210] pci 0000:00:15.0: PCI INT A -> Link[Z012] -> GSI 22 (level, low) -> IRQ 22
[    0.431218] pci 0000:00:15.0: setting latency timer to 64
[    0.431492] ACPI: PCI Interrupt Link [Z016] enabled at IRQ 21
[    0.431494]   alloc irq_desc for 21 on node -1
[    0.431496]   alloc kstat_irqs on node -1
[    0.431498] pci 0000:00:16.0: PCI INT A -> Link[Z016] -> GSI 21 (level, low) -> IRQ 21
[    0.431506] pci 0000:00:16.0: setting latency timer to 64
[    0.431781] ACPI: PCI Interrupt Link [Z01A] enabled at IRQ 20
[    0.431784]   alloc irq_desc for 20 on node -1
[    0.431785]   alloc kstat_irqs on node -1
[    0.431788] pci 0000:00:17.0: PCI INT A -> Link[Z01A] -> GSI 20 (level, low) -> IRQ 20
[    0.431796] pci 0000:00:17.0: setting latency timer to 64
[    0.432068] ACPI: PCI Interrupt Link [Z01E] enabled at IRQ 19
[    0.432070]   alloc irq_desc for 19 on node -1
[    0.432072]   alloc kstat_irqs on node -1
[    0.432075] pci 0000:00:18.0: PCI INT A -> Link[Z01E] -> GSI 19 (level, low) -> IRQ 19
[    0.432083] pci 0000:00:18.0: setting latency timer to 64
[    0.432088] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.432090] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.432092] pci_bus 0000:01: resource 1 mem: [0xf0500000-0xf05fffff]
[    0.432094] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.432096] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.432098] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.432099] pci_bus 0000:02: resource 1 mem: [0xac000000-0xaeffffff]
[    0.432101] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.432103] pci_bus 0000:03: resource 0 io:  [0x5000-0x5fff]
[    0.432105] pci_bus 0000:03: resource 1 mem: [0xaa000000-0xaaffffff]
[    0.432107] pci_bus 0000:03: resource 2 pref mem [0xb0000000-0xcdffffff]
[    0.432109] pci_bus 0000:04: resource 0 io:  [0x6000-0x6fff]
[    0.432110] pci_bus 0000:04: resource 1 mem: [0xf0200000-0xf03fffff]
[    0.432112] pci_bus 0000:04: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.432114] pci_bus 0000:06: resource 1 mem: [0xf0400000-0xf04fffff]
[    0.432144] NET: Registered protocol family 2
[    0.432282] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.433342] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.437392] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.437967] TCP: Hash tables configured (established 524288 bind 65536)
[    0.437969] TCP reno registered
[    0.438070] NET: Registered protocol family 1
[    0.438378] pci 0000:03:00.0: Boot video device
[    0.438436] Simple Boot Flag at 0x36 set to 0x1
[    0.438606] Scanning for low memory corruption every 60 seconds
[    0.438740] audit: initializing netlink socket (disabled)
[    0.438750] type=2000 audit(1273598610.429:1): initialized
[    0.446226] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.447307] VFS: Disk quotas dquot_6.5.2
[    0.447351] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.447805] fuse init (API version 7.13)
[    0.447868] msgmni has been set to 7392
[    0.448036] alg: No test for stdrng (krng)
[    0.448075] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.448078] io scheduler noop registered
[    0.448079] io scheduler anticipatory registered
[    0.448081] io scheduler deadline registered
[    0.448110] io scheduler cfq registered (default)
[    0.448398]   alloc irq_desc for 24 on node -1
[    0.448400]   alloc kstat_irqs on node -1
[    0.448419] pcieport 0000:00:0c.0: irq 24 for MSI/MSI-X
[    0.448439] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.448790]   alloc irq_desc for 25 on node -1
[    0.448792]   alloc kstat_irqs on node -1
[    0.448808] pcieport 0000:00:15.0: irq 25 for MSI/MSI-X
[    0.448826] pcieport 0000:00:15.0: setting latency timer to 64
[    0.449166]   alloc irq_desc for 26 on node -1
[    0.449168]   alloc kstat_irqs on node -1
[    0.449183] pcieport 0000:00:16.0: irq 26 for MSI/MSI-X
[    0.449202] pcieport 0000:00:16.0: setting latency timer to 64
[    0.449543]   alloc irq_desc for 27 on node -1
[    0.449545]   alloc kstat_irqs on node -1
[    0.449561] pcieport 0000:00:17.0: irq 27 for MSI/MSI-X
[    0.449580] pcieport 0000:00:17.0: setting latency timer to 64
[    0.449926]   alloc irq_desc for 28 on node -1
[    0.449928]   alloc kstat_irqs on node -1
[    0.449944] pcieport 0000:00:18.0: irq 28 for MSI/MSI-X
[    0.449963] pcieport 0000:00:18.0: setting latency timer to 64
[    0.450113] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.450130] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.451184] ACPI: AC Adapter [ADP0] (on-line)
[    0.451258] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.451261] ACPI: Power Button [PWRB]
[    0.451303] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:27/PNP0C0E:00/input/input1
[    0.451305] ACPI: Sleep Button [SLPB]
[    0.451345] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.452919] ACPI: Lid Switch [LID]
[    0.452954] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.452956] ACPI: Power Button [PWRF]
[    0.453713] ACPI: SSDT 000000008fee10c8 00261 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.454607] ACPI: SSDT 000000008fee16cc 0067D (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.456321] Monitor-Mwait will be used to enter C-1 state
[    0.456341] Monitor-Mwait will be used to enter C-2 state
[    0.456358] Monitor-Mwait will be used to enter C-3 state
[    0.456362] Marking TSC unstable due to TSC halts in idle
[    0.456405] processor LNXCPU:00: registered as cooling_device0
[    0.456819] ACPI: SSDT 000000008fee0ed6 001F2 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.457176] ACPI: SSDT 000000008fee1647 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.457642] Switching to clocksource hpet
[    0.462723] processor LNXCPU:01: registered as cooling_device1
[    0.470422] thermal LNXTHERM:01: registered as thermal_zone0
[    0.470428] ACPI: Thermal Zone [THRM] (61 C)
[    0.471612] Linux agpgart interface v0.103
[    0.471642] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.472636] brd: module loaded
[    0.472999] loop: module loaded
[    0.473061] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.473377] Fixed MDIO Bus: probed
[    0.473400] PPP generic driver version 2.4.2
[    0.473425] tun: Universal TUN/TAP device driver, 1.6
[    0.473427] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.473489] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.473781] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 18
[    0.473786]   alloc irq_desc for 18 on node -1
[    0.473787]   alloc kstat_irqs on node -1
[    0.473793] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 18 (level, low) -> IRQ 18
[    0.473804] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.473807] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.473834] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.473860] ehci_hcd 0000:00:04.1: debug port 1
[    0.473868] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.473882] ehci_hcd 0000:00:04.1: irq 18, io mem 0xf0889000
[    0.500020] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.500121] usb usb1: configuration #1 chosen from 1 choice
[    0.500149] hub 1-0:1.0: USB hub found
[    0.500157] hub 1-0:1.0: 4 ports detected
[    0.500504] ACPI: PCI Interrupt Link [Z00P] enabled at IRQ 23
[    0.500509] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z00P] -> GSI 23 (level, low) -> IRQ 23
[    0.500532] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.500535] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.500566] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.500586] ehci_hcd 0000:00:06.1: debug port 1
[    0.500593] ehci_hcd 0000:00:06.1: cache line size of 32 is not supported
[    0.500611] ehci_hcd 0000:00:06.1: irq 23, io mem 0xf0889400
[    0.520015] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.520101] usb usb2: configuration #1 chosen from 1 choice
[    0.520122] hub 2-0:1.0: USB hub found
[    0.520129] hub 2-0:1.0: 3 ports detected
[    0.520177] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.520489] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.520492] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, low) -> IRQ 22
[    0.520509] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.520511] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.520541] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.520561] ohci_hcd 0000:00:04.0: irq 22, io mem 0xf0886000
[    0.544981] Freeing initrd memory: 13119k freed
[    0.582163] usb usb3: configuration #1 chosen from 1 choice
[    0.582191] hub 3-0:1.0: USB hub found
[    0.582201] hub 3-0:1.0: 4 ports detected
[    0.582573] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 21
[    0.582577] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z00O] -> GSI 21 (level, low) -> IRQ 21
[    0.582606] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.582608] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.582647] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.582674] ohci_hcd 0000:00:06.0: irq 21, io mem 0xf0887000
[    0.642066] usb usb4: configuration #1 chosen from 1 choice
[    0.642085] hub 4-0:1.0: USB hub found
[    0.642091] hub 4-0:1.0: 3 ports detected
[    0.642136] uhci_hcd: USB Universal Host Controller Interface driver
[    0.642216] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.646960] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.646965] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.647074] mice: PS/2 mouse device common for all mice
[    0.647199] rtc_cmos 00:0a: RTC can wake from S4
[    0.647235] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    0.647282] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.647375] device-mapper: uevent: version 1.0.3
[    0.647476] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.647554] device-mapper: multipath: version 1.1.0 loaded
[    0.647556] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.647762] cpuidle: using governor ladder
[    0.647846] cpuidle: using governor menu
[    0.648126] TCP cubic registered
[    0.648227] NET: Registered protocol family 10
[    0.648583] lo: Disabled Privacy Extensions
[    0.648805] NET: Registered protocol family 17
[    0.649233] PM: Resume from disk failed.
[    0.649259] registered taskstats version 1
[    0.649812] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.650205]   Magic number: 10:445:390
[    0.650347] rtc_cmos 00:0a: setting system clock to 2010-05-11 17:23:31 UTC (1273598611)
[    0.650349] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.650351] EDD information not available.
[    0.650396] Freeing unused kernel memory: 876k freed
[    0.650736] Write protecting the kernel read-only data: 7680k
[    0.664096] udev: starting version 151
[    0.704863] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.705170] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    0.705175] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    0.705179] forcedeth 0000:00:0a.0: setting latency timer to 64
[    0.707695] ACPI: Battery Slot [BAT0] (battery present)
[    0.751709] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    0.752100] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/LNXVIDEO:00/input/input6
[    0.752139] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    0.752157] [Firmware Bug]: ACPI(Z01I) defines _DOD but not _DOS
[    0.752260] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:01/input/input7
[    0.752283] ACPI: Video Device [Z01I] (multi-head: yes  rom: yes  post: no)
[    0.758083] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[    0.758093] ohci1394 0000:01:07.0: PCI INT A -> Link[LNK1] -> GSI 11 (level, low) -> IRQ 11
[    0.814675] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[f0500000-f05007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    0.830097] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    0.987346] usb 2-3: configuration #1 chosen from 1 choice
[    1.230724] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:22:19:f7:92:be
[    1.230726] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.230825] ahci 0000:00:0b.0: version 3.0
[    1.231122] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 19
[    1.231125] ahci 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 19 (level, low) -> IRQ 19
[    1.231180]   alloc irq_desc for 29 on node -1
[    1.231182]   alloc kstat_irqs on node -1
[    1.231189] ahci 0000:00:0b.0: irq 29 for MSI/MSI-X
[    1.231243] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.231246] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pmp pio slum part sxs boh 
[    1.231249] ahci 0000:00:0b.0: setting latency timer to 64
[    1.231579] scsi0 : ahci
[    1.231664] scsi1 : ahci
[    1.231720] scsi2 : ahci
[    1.231764] scsi3 : ahci
[    1.231810] scsi4 : ahci
[    1.231854] scsi5 : ahci
[    1.231972] ata1: SATA max UDMA/133 abar m8192@0xf0884000 port 0xf0884100 irq 29
[    1.231974] ata2: SATA max UDMA/133 abar m8192@0xf0884000 port 0xf0884180 irq 29
[    1.231976] ata3: SATA max UDMA/133 abar m8192@0xf0884000 port 0xf0884200 irq 29
[    1.231978] ata4: SATA max UDMA/133 abar m8192@0xf0884000 port 0xf0884280 irq 29
[    1.231980] ata5: SATA max UDMA/133 abar m8192@0xf0884000 port 0xf0884300 irq 29
[    1.231982] ata6: SATA max UDMA/133 abar m8192@0xf0884000 port 0xf0884380 irq 29
[    1.580044] ata4: SATA link down (SStatus 0 SControl 300)
[    1.580071] ata3: SATA link down (SStatus 0 SControl 300)
[    1.580084] ata6: SATA link down (SStatus 0 SControl 300)
[    1.580099] ata5: SATA link down (SStatus 0 SControl 300)
[    1.760032] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.760046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.762344] ata1.00: ATA-8: ST9500420ASG, 0002SDM1, max UDMA/133
[    1.762348] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.764538] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GS20N, A109, max UDMA/133
[    1.765124] ata1.00: configured for UDMA/133
[    1.765237] scsi 0:0:0:0: Direct-Access     ATA      ST9500420ASG     0002 PQ: 0 ANSI: 5
[    1.765352] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.765412] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.765446] sd 0:0:0:0: [sda] Write Protect is off
[    1.765448] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.765466] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.765571]  sda:
[    1.769369] ata2.00: configured for UDMA/133
[    1.774904] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GS20N    A109 PQ: 0 ANSI: 5
[    1.786150] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.786154] Uniform CD-ROM driver Revision: 3.20
[    1.786259] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.786306] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.789840]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.841607] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.130457] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc00029cc1e21]
[    2.698277] uvesafb: NVIDIA Corporation, MCP79 Board - mcp79mxo, Chip Rev   , OEM: NVIDIA, VBE v3.0
[    2.805619] uvesafb: VBIOS/hardware doesn't support DDC transfers
[    2.805621] uvesafb: no monitor limits have been set, default refresh rate will be used
[    2.805929] uvesafb: scrolling: redraw
[    2.806127] mtrr: type mismatch for cd000000,400000 old: write-back new: write-combining
[    2.806130] mtrr: type mismatch for cd000000,200000 old: write-back new: write-combining
[    2.806133] mtrr: type mismatch for cd000000,100000 old: write-back new: write-combining
[    2.806136] mtrr: type mismatch for cd000000,80000 old: write-back new: write-combining
[    2.806139] mtrr: type mismatch for cd000000,40000 old: write-back new: write-combining
[    2.806142] mtrr: type mismatch for cd000000,20000 old: write-back new: write-combining
[    2.806144] mtrr: type mismatch for cd000000,10000 old: write-back new: write-combining
[    2.806147] mtrr: type mismatch for cd000000,8000 old: write-back new: write-combining
[    2.806150] mtrr: type mismatch for cd000000,4000 old: write-back new: write-combining
[    2.806153] mtrr: type mismatch for cd000000,2000 old: write-back new: write-combining
[    2.806156] mtrr: type mismatch for cd000000,1000 old: write-back new: write-combining
[    2.806204] uvesafb: framebuffer at 0xcd000000, mapped to 0xffffc90001900000, using 8000k, total 14336k
[    2.806206] fb0: VESA VGA frame buffer device
[    3.184092] Console: switching to colour frame buffer device 128x48
[    3.483114] kjournald starting.  Commit interval 5 seconds
[    3.483152] EXT3-fs: mounted filesystem with ordered data mode.
[   20.946828] udev: starting version 151
[   20.968450] ACPI: EC: GPE storm detected, transactions will use polling mode
[   21.058045] lp: driver loaded but no devices found
[   21.060157] Adding 4313412k swap on /dev/sda6.  Priority:-1 extents:1 across:4313412k 
[   21.098540] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.173615] type=1505 audit(1273623832.019:2):  operation="profile_load" pid=680 name="/sbin/dhclient3"
[   21.174117] type=1505 audit(1273623832.019:3):  operation="profile_load" pid=680 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.174387] type=1505 audit(1273623832.019:4):  operation="profile_load" pid=680 name="/usr/lib/connman/scripts/dhclient-script"
[   21.229517] nvidia: module license 'NVIDIA' taints kernel.
[   21.229519] Disabling lock debugging due to kernel taint
[   21.530338] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   21.530355] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   21.535537] sdhci: Secure Digital Host Controller Interface driver
[   21.535539] sdhci: Copyright(c) Pierre Ossman
[   21.536421] sdhci-pci 0000:01:07.1: SDHCI controller found [1180:0822] (rev 22)
[   21.536734] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   21.536738] sdhci-pci 0000:01:07.1: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
[   21.536841] sdhci-pci 0000:01:07.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   21.536869] Registered led device: mmc0::
[   21.536897] mmc0: SDHCI controller on PCI [0000:01:07.1] using DMA
[   21.545218] vga16fb: initializing
[   21.545221] vga16fb: mapped to 0xffff8800000a0000
[   21.545224] vga16fb: not registering due to another framebuffer present
[   21.569771] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.572233] lib80211: common routines for IEEE802.11 drivers
[   21.572236] lib80211_crypt: registered algorithm 'NULL'
[   21.575656] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   21.575660] wl: Unknown symbol lib80211_get_crypto_ops
[   21.625923] Linux video capture interface: v2.00
[   21.628055] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a3)
[   21.630794] input: Integrated Webcam as /devices/pci0000:00/0000:00:06.1/usb2/2-3/2-3:1.0/input/input8
[   21.782144] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 18
[   21.782149] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 18 (level, low) -> IRQ 18
[   21.782182] nvidia 0000:02:00.0: enabling device (0004 -> 0007)
[   21.782193] nvidia 0000:02:00.0: PCI INT A -> Link[Z00Q] -> GSI 23 (level, low) -> IRQ 23
[   21.782204] nvidia 0000:02:00.0: setting latency timer to 64
[   21.782212] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[   21.782574] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 23
[   21.782577] nvidia 0000:03:00.0: PCI INT A -> Link[LGPU] -> GSI 23 (level, low) -> IRQ 23
[   21.782581] nvidia 0000:03:00.0: setting latency timer to 64
[   21.782584] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.782947] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[   21.811268] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   21.811287] usbcore: registered new interface driver uvcvideo
[   21.811290] USB Video Class driver (v0.1.0)
[   21.928363] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   21.928642] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   21.928646]   alloc irq_desc for 17 on node -1
[   21.928648]   alloc kstat_irqs on node -1
[   21.928654] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 17 (level, low) -> IRQ 17
[   21.928658] hda_intel: Disable MSI for Nvidia chipset
[   21.928698] HDA Intel 0000:00:08.0: setting latency timer to 64
[   22.310995] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   22.357566] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   23.040039] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   23.172156] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   23.172890] EXT3 FS on sda5, internal journal
[   23.335682] type=1505 audit(1273623834.179:5):  operation="profile_load" pid=910 name="/usr/share/gdm/guest-session/Xsession"
[   23.336847] type=1505 audit(1273623834.179:6):  operation="profile_replace" pid=911 name="/sbin/dhclient3"
[   23.337352] type=1505 audit(1273623834.179:7):  operation="profile_replace" pid=911 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.337625] type=1505 audit(1273623834.179:8):  operation="profile_replace" pid=911 name="/usr/lib/connman/scripts/dhclient-script"
[   23.339717] type=1505 audit(1273623834.179:9):  operation="profile_load" pid=912 name="/usr/bin/evince"
[   23.345940] type=1505 audit(1273623834.189:10):  operation="profile_load" pid=912 name="/usr/bin/evince-previewer"
[   23.349666] type=1505 audit(1273623834.189:11):  operation="profile_load" pid=912 name="/usr/bin/evince-thumbnailer"
[   23.836857] ppdev: user-space parallel port driver
[   24.062549] hda-intel: Codec #1 probe error; disabling it...
[   25.331420] NVRM: failed to copy vbios to system memory.
[   25.331598] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
[   25.331603] NVRM: rm_init_adapter(0) failed
[   26.100160] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input11
[   26.960299] input: HDA NVidia Mic at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input12
[   26.960439] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input13
[   26.960523] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input14
[   33.910022] eth0: no IPv6 routers present
[  778.603112] eth0: link down.
[  814.854072] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[  814.854077] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
[ 3290.110414] eth0: link up.
[ 6332.856842] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 6332.856846] wl: Unknown symbol lib80211_get_crypto_ops

```

---

### Post by chili555 on 2010-05-11
And while my buddy gets his coffee, add to the requests:```

dmesg | grep wl

```Do you have an ethernet connection? If so, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by jschille on 2010-05-11
chili!
dmesg | grep wl
```
[   21.575656] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   21.575660] wl: Unknown symbol lib80211_get_crypto_ops
[ 6332.856842] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 6332.856846] wl: Unknown symbol lib80211_get_crypto_ops

```

And code from the reinstall
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/896kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 201972 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.32-22-generic
Building for architecture x86_64
Building initial module for 2.6.32-22-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic

```

---

### Post by bkratz on 2010-05-11
> **chili555 said:**
> And while my buddy gets his coffee, add to the requests:```

dmesg | grep wl

```Do you have an ethernet connection? If so, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```


Well, the coffee didn't do me any good-- I have to sleep for a little while--I will subscribe and check back a little later to see what happens--It really doesn't appear that the driver wl is in there at all, so Chili's ( the best anyway) suggestion is what I would do next. Is rfkill list not in ubuntu Studio? I know it is in 9.10 and 10.04 standard versions.  My typing is requiring a lot of backspacing, see you a little later.
This paragraph has taken me about 15 minutes, should not have used the decaff!

---

### Post by jschille on 2010-05-11
decaf coffee? what's the point!?
rfkill seems to work, just looks like it wants an identifier after the list
```
jb@jb-laptop:~$ rfkill
Usage:    rfkill [options] command
Options:
    --version    show version (0.4)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

```
enjoy your rest - thank you for your help

---

### Post by jschille on 2010-05-11
> **bkratz said:**
> By the way, I found a whole lot of people with this same problem on that particular card with a google search.  I only found one that claims success though.

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

Chili, in regards to that thread.  I read that thread and ATTEMPTED to follow the directions, but am way too new to this to figure it out.
Edit: Not sure if I should be following that thread or just waiting to hear from the master, but I unpacked the files into a folder on my desktop and added the line #include < linux/sched.h > on line 35. It then tells to me 'make' the file. No idea how to do that, and also not sure if I unpacked the contents to the correct location, i just unpacked them to a folder on my desktop...

---

### Post by chili555 on 2010-05-11
OK, we are getting there! Now do:```
sudo modprobe wl
iwconfig
```Some systems respond to rfkill; some including mine, do not. Hey, we tried.

---

### Post by jschille on 2010-05-11
Hmm.. no go i think.

```

jb@jb-laptop:~$ sudo modprobe wl
[sudo] password for jb: 
FATAL: Error inserting wl (/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jb@jb-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by chili555 on 2010-05-11
I am getting close to jammie time. Would you please reboot and see if the module loaded:```
lsmod | grep wl
```If not, try to load it:```
sudo modprobe wl
```If it doesn't work, we will compile tomorrow. I will test it and write detailed instructions.

---

### Post by jschille on 2010-05-11
Thanks so much for the help tonight Chili.
After entering the command I was just returned to another command line after entering lsmod | grep wl
So I am guessing that means nothing...
And then I get another Fatal error after entering the sudo command
```
FATAL: Error inserting wl (/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Hopefully will see you tomorrow!

---

### Post by chili555 on 2010-05-11
> Hopefully will see you tomorrow!Absolutely. I should have it all done by 9:00 am EDT.

---

### Post by chili555 on 2010-05-12
Let's put on our Linux geek glasses and get busy!

Make sure you have the correct tools in place required to compile:```
sudo apt-get install linux-headers-generic build-essential
```Download the package here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I downloaded it to my desktop and then created a folder called *broadcomwl*. I dragged the file into my new folder. Make sure you get the correct version; 32-bit or 64-bit. If you run the command:```
uname -a
```and it says 'x64_86' in the string, you need 64-bit. If not, you need 32-bit. 

Double-click the folder on your desktop. The file manager will open showing the tar.gz package. Right-click it and select Extract Here. A folder will be created called hybrid-portsrc-x86_32-v5.60.48.36 for the 32-bit version. Don't worry about the cumbersome name; we are going to use geek tools to make it easy!

Double click the folder and navigate down to src/wl/sys. Right-click the file wl_linux.c and select Open with gedit. Scroll down to line 35 and add a line:```
#include <linux/sched.h>
```Save and close gedit.

NOTE: The howto referred to incorrectly says: #include <  linux/sched.h  >
 The space is incorrect. It must be #include <linux/sched.h>

Now open a terminal and get your geek on:```
cd Desktop/broadcomwl/hybrid
```Press Tab and the remainder will fill in automagically. Cool, eh?

Now do:```
make
```If all goes well, you have no errors and one harmeless license warning. If you have any more, stop and post here. If it 'makes' without any errors or other warnings, then do:```
sudo cp wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
```That moves the module we just built to the correct place in your system.

See where it says $(uname -r)? That means that it is in the correct place for you currently running kernel. When updates bring you a later kernel version, also known as linux-image, the module wl will no longer work; just navigate to the Desktop/broadcomwl/hybrid-etc. folder again and run the command again:```
sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
```Now can you insert the module and get your wireless going?```
sudo modprobe wl
iwconfig
```Post back with any questions or problems.

---

### Post by chili555 on 2010-05-12
EDIT: Before you start, run:```
modinfo wl
```If you find it is located in  /lib/modules/2.6.32-whatever/updates/dkms, then modify the mv command above to:```
sudo cp wl.ko /lib/modules/$(uname -r)/updates/dkms/

```

---

### Post by bkratz on 2010-05-12
I have already bookmarked this page, in eager anticipation. Excellent instructions-- I wish I had one to try!

---

### Post by chili555 on 2010-05-12
> **bkratz said:**
> I have already bookmarked this page, in eager anticipation. Excellent instructions-- I wish I had one to try!Hey, I don't even have one! However, it was interesting to build the module and modprobe it and see if it errors out. It doesn't but I don't have the device to try.

---

### Post by jschille on 2010-05-12
MORNING CHILI!

Going to post responses to what I get as I follow your directions just to make sure I don't mess anything up :)

I downloaded the file - I have a 64bit OS although when I type the following 
**uname -r**
I get 
```
2.6.32-22-generic 
```
No 64 in that line, however I downloaded the 64 bit anyway... We will see...
I found the file, changed it, added the new header file to line 35.

I am next assuming when I am supposed to enter in the command 
```
 cd desktop/broadcomwl/hybrid
```
and then press Tab that the folder we extracted to the desktop should be moved to the broadcomwl folder.
I completed that step.

After "make" I only received that one warning.
```
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/jb/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/wl.o
see include/linux/module.h for more information
  LD [M]  /home/jb/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'

```

Your next line states 
```
sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
```
I am assuming I am supposed to be in desktop/broadcomwl/hybridxxxx
Your edit says to look where modinfo is and mine states
```
filename:       /lib/modules/2.6.32-22-generic/updates/dkms/wl.ko

```
So, I will use the command your edit states instead...
Let's see what happens..

Dangit, ok. Problem is here.
When I enter in the command (note, I am in desktop/broadcomlw/hybridxxx)
```
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ sudo mv wl.ko /lib/modules/$(uname -r)/updates/dkms/
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ sudo mv wl.ko /lib/modules/$(uname -r)/updates/dkms/
mv: cannot stat `wl.ko': No such file or directory

```

From the commands you can see I entered in the command in your edit.  It simply took me to the next line.  And then entered in sudo modprobe wl and got the fatal error.

I again tried the line from the edit post and then it said No such file or directory. Is that because I have to "make" again?

I FEEL WE ARE GETTING CLOSER! Thanks so much Chili!

---

### Post by jschille on 2010-05-12
Same thing as above but just ALL my code together.
```
jb@jb-laptop:~$ **cd Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/**
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **make**
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/jb/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/wl.o
see include/linux/module.h for more information
  LD [M]  /home/jb/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **modinfo wl**
filename:       /lib/modules/2.6.32-22-generic/updates/dkms/wl.ko
srcversion:     C0B8016F62A3C611905F674
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **sudo mv wl.ko /lib/modules/$(uname -r)/updates/dkms/**
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **sudo modprobe wl**
FATAL: Error inserting wl (/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **iwoconfig**
No command 'iwoconfig' found, did you mean:
 Command 'iwconfig' from package 'wireless-tools' (main)
iwoconfig: command not found
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

```Just in case you ask for it here this is
```
jb@jb-laptop:~$ **dmesg | grep wl**
[   26.518928] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   26.518931] wl: Unknown symbol lib80211_get_crypto_ops
[  611.653978] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  611.653983] wl: Unknown symbol lib80211_get_crypto_ops
[  652.713535] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  652.713541] wl: Unknown symbol lib80211_get_crypto_ops
[ 1621.291869] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 1621.291874] wl: Unknown symbol lib80211_get_crypto_ops
[ 2236.063297] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 2236.063302] wl: Unknown symbol lib80211_get_crypto_ops
[ 2293.731101] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 2293.731106] wl: Unknown symbol lib80211_get_crypto_ops
[ 2478.413245] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 2478.413249] wl: Unknown symbol lib80211_get_crypto_ops

```

---

### Post by chili555 on 2010-05-12
Please do:```
cd ~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36
make
sudo cp wl.ko /lib/modules/$(uname -r)/updates/dkms/

```The problem, in the original howto, is that after you move it (mv) it's moved! That is, it's no longer there if you need it again. So we will copy it (cp). Next do:```
sudo modprobe wl
iwconfig
```I made a slight error; the command should be:```
uname -[COLOR="Red"]r[/COLOR]
```I have amended my posts above to correct these errors.

---

### Post by jschille on 2010-05-12
hmm... still getting the same thing it looks like...

```
jb@jb-laptop:~$** cd Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/**
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **make**
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/jb/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/wl.o
see include/linux/module.h for more information
  LD [M]  /home/jb/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **sudo cp wl.ko /lib/modules/$(uname -r)/updates/dkms/**
[sudo] password for jb: 
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **sudo modprobe wl**
FATAL: Error inserting wl (/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jb@jb-laptop:~/Desktop/broadcomwl/hybrid-portsrc-x86_64-v5.60.48.36$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by jschille on 2010-05-12
Hey Chili, don't forget about me, but I am heading out for now.
I am going to a place where I do not have an ethernet connection, but my wireless card on my XP side will still work.
Worse case scenario we can continue this on Friday when I return back to my home.

Thank you so much for the help Chili.
Talk to you soon hopefully.

---

### Post by chili555 on 2010-05-12
Nice little Chili never curses, but if he did, today might be a good day to start.

I saw this: [http://www.backports.ubuntuforums.org/showthread.php?t=1401290&page=2](http://www.backports.ubuntuforums.org/showthread.php?t=1401290&page=2)

See posts 15 and 16. Assuming you are still in the directory where you built the driver, do:```
sudo apt-get remove --purge linux-backports-modules-*
make clean
make
modinfo wl
```Wherever the module wl is now, copy it over:```
sudo cp wl.ko /lib/modules/wherever/whatever
sudo modprobe wl
```Any errors before I get my anti-depressants?

---

### Post by jschille on 2010-05-12
Alright Chili, I am going to try this first thing once I get back home (Thursday night).
I'll shoot you PM on Friday morning and to the thread and let you know how it went.
Thank you for all the help!

I would avoid those anti-depressants :)

Edit:  Not sure if this has any relevance at all, but I did run across that command earlier in trying to figure out my problems. I ran the command
```

sudo apt-get install linux-backports-modules-wireless-lucid-generic

```
And after I ran that is when I lost my ability to see wireless connections.
Although I never entered the commands that follow, so, I will let you know what happens.
haha, now that I look at the commands it looks like the one you are telling me to run REMOVES 
the backports when I was installing them... yikes..

---

### Post by bkratz on 2010-05-12
Please post what happens here so we can all benefit and stop worrying!


Sorry, reread and see you said to here too!

---

### Post by chili555 on 2010-05-12
> now that I look at the commands it looks like the one you are telling me to run REMOVES
the backports when I was installing them... yikes..I know! It's very sad. If you search far enough, you can see many different fixes for this problem. As you can see by the link I gave you, they say it works. You will know when you try it.

I am holding in reserve the Broadcom fix involving poisonous snakes and exorcism.

---

### Post by jschille on 2010-05-12
CHILI!
haha, well. 
I removed the linux-backports-modules
make clean
make
 and then copied the module
and then ran 
sudo modprobe wl

I got that fatal error again...
BUT! that did not stop me!

After removing those backports I deactivated and then activated the STA driver.
Restarted....
and...
I am now writing this Reply to you on my linux partition with NO ETHERNET CORD plugged into it!!!

YOU SAVED ME!! haha

Thanks so much Chili!

So, just to get this right.. in the end all that was needed to do was for me to enter the command...
```

sudo apt-get remove  --purge linux-backports-modules-*

```
and then just remove and then activate the STA driver and reboot?
All the other things (dl the driver, editing the header files) was not needed? (but at least good practice with the terminal for me...)

I guess this goes to show that it is never a good idea to just randomly start entering commands into my terminal :)

Again Chili, thanks a lot.
SOLVED!

---

### Post by bkratz on 2010-05-12
Congratulations, you worked hard for this one.

---

### Post by jetsam on 2010-05-12
> **chili555 said:**
> I am holding in reserve the Broadcom fix involving poisonous snakes and exorcism.

Darn.  I was hoping for the exorcism. 

:KS:popcorn:

...maybe one of these days...

---

### Post by chili555 on 2010-05-12
Woo hoo! Great job. I am very glad it's working for you. Have fun and feel free to call on any of us again.

---

### Post by jasonlfunk on 2010-05-13
> **jschille said:**
> CHILI!
haha, well. 
I removed the linux-backports-modules
make clean
make
 and then copied the module
and then ran 
sudo modprobe wl

I got that fatal error again...
BUT! that did not stop me!

After removing those backports I deactivated and then activated the STA driver.
Restarted....
and...
I am now writing this Reply to you on my linux partition with NO ETHERNET CORD plugged into it!!!

YOU SAVED ME!! haha

Thanks so much Chili!

So, just to get this right.. in the end all that was needed to do was for me to enter the command...
```

sudo apt-get remove  --purge linux-backports-modules-*

```
and then just remove and then activate the STA driver and reboot?
All the other things (dl the driver, editing the header files) was not needed? (but at least good practice with the terminal for me...)

I guess this goes to show that it is never a good idea to just randomly start entering commands into my terminal :)

Again Chili, thanks a lot.
SOLVED!

This fixed my problem too. Thanks a million.:guitar:

---

### Post by fyq on 2010-09-09
I run all command above . 
But when I run  "sudo modprobe wl" , it show me a meesage : "FATAL: Module wl not found."
Could you tell me how to solve this problem ? Thanks .

---

### Post by maedelo on 2010-11-07
try using Ubuntu Netbook Edition

worked for me! ... have to get used to this layout though :(

---

### Post by chirojoseph on 2010-11-14
bump and double bump
[FONT=Times New Roman][SIZE=6]ive followed this thread through and MANY other threads about problems with the broadcom drivers in ASUS eeepc 1015pem...i thought perhaps this clearing of the backports might help in my situation but i think it must be much more simple...obviously im a complete and utter newbie and just running through a forest blindfolded at this point.
Have a new eeepc1015pem, windows 7 the wireless worked fine, installed ppermint and only have ethernet now. 

while searching for answwers a week ago someone said id be better off with different distro but now have tried easypeasy, lubuntu, mint...its all the same when it comes to the fact that when i go to "hardware drivers" it says STA broadcom tested by peppermint developers..propietary..for use with broadcom 4311, 4322, etc etc

it says the drivers are NOT activated. when i click on ACTIVATE i get the error message

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

same deal no matter the distro im using..of course..and ive no idea where to look for the jockey log file and wouldnt understand what it was telling me anyway if i found it!

basically im wasting time and banging my head against about 20 different linux forums trying to find others with the same problem..but most of the solutions i find appear to be more complex and convoluted than this problem deserves...it seems more of a "this shmuck is a complete newb and just needs to click the so and so tab in the such and such file...
so a little help for the super newb please__im about to chuck the whole linux project in the garbage adn go back to XP but i know i just need a little expert advice to get over this first HUGE hurdle of WIRELESS internet.

 btway whoever can help me with this, and a few other minor problems with this new netbook, has a free place to crash in the cancun-playa del carmen area of the caribbean mexican coast...just thought id throw that little incentive out there!! jeje

chirojoseph 
[/SIZE][/FONT]

---

### Post by ayqazi on 2011-03-12
(Please read the rest of this thread before trying to understand what I'm about to say.  I'm tired and sleepy and don't want to have to explain from the beginning).

Firstly, I've got an HP Pavilion dv6 manufactured around the beginning of 2011.  It has a Broadcom BCM4313 802.11b/g LP-PHY (rev 01) wifi card built-in.

OK, I tried chilli's instructions, and I was still getting those annoying 'unknown symbol lib80211_get_crypto_ops' and 'wl: disagrees about version of symbol lib80211_get_crypto_ops', and it suddenly struck me: what if the disagreement is to do with kernel version?

So I did a 'dpkg -l | grep linux-headers', and I did a 'sudo aptitude remove --purge <package>' for every linux-header that was NOT for the current kernel version.

Then I tried chilli's instructions about building again, did a depmod -a after copying wl.ko to the right place, and still the same.....

So another try.  First I did a 'modprobe -r lib80211' (you may need to do a 'lsmod' to find all the other lib80211 modules to remove before you can remove that one), then finally did a 'modprobe wl'..... and it worked!

So that's another piece of the puzzle solved.  Stupid pile of...... ok, I'm going to bed.

EDIT: and as a bonus, after getting rid of old linux-headers, aptitude install-ing bcmwl-kernel-source also works.

EDIT 2: it turns out that removing the headers (while a useful thing to do) is not the problem: it is the fact that those stupid backports packages contain a lib80211.ko module that stays loaded into the kernel even after you remove the backports packages!  So it may have been the modprobe --r (kernel module removal) of it before doing a modprobe wl that made it work.

---

