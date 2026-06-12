---
title: "No Ethernet or Wireless connection on MSI GT780 DX"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by mmtaylor on 2012-02-22
I just bought this laptop and want to dual-boot Windows and Ubuntu. Everything in Windows (came pre-installed) is working fine. In Ubuntu (installed Natty because that's what I had on a disk already) I cannot connect to the internet at all. Left-click on the connection icon in the status bar shows only Wired Networks (greyed out) and disconnected below that, then VPN Connections.

 **lshw -C Network output**:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 6c:62:6d:37:a5:7d
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.028.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6200000-f6201fff
```

**lspci  output:**

```
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 1210 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0e0c (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Intel Corporation Device 0896 (rev 34)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

**lsusb  output:**

```
4Bus 002 Device 004: ID 1770:ff00  
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 13fe:3100 Kingston Technology Company Inc. 2 GB USB stick
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**lspci -nn  output:**

```
00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c4b] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1210] (rev a1)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0e0c] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
03:00.0 Network controller [0280]: Intel Corporation Device [8086:0896] (rev 34)
04:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
```

**ifconfig  output:**

```
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:37:a5:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)
```

**iwconfig  output:**

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

**lsmod  output:**

```
Module                  Size  Used by
ndiswrapper           184207  0 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
nls_utf8                1069  1 
isofs                  30022  1 
aes_i586                7280  146 
aes_generic            26875  1 aes_i586
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
binfmt_misc             6599  1 
joydev                  8735  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_seq_midi            4588  0 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
serio_raw               4022  0 
xhci_hcd               51737  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
nouveau               516971  0 
ttm                    56633  1 nouveau
usbhid                 36882  0 
drm_kms_helper         30200  1 nouveau
hid                    67742  1 usbhid
drm                   168054  3 nouveau,ttm,drm_kms_helper
ahci                   19013  0 
libahci                21667  5 ahci
r8168                 192590  0 
video                  18712  0 
intel_agp              26360  0 
output                  1883  1 video
agpgart                32011  3 ttm,drm,intel_agp
i2c_algo_bit            5168  1 nouveau

```

** iwlist scan output:**

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Any help would be greatly appreciated.

---

### Post by chili555 on 2012-02-23
Interesting set of problems there. I notice this in your *lshw*:> description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       <snip>
       logical name: eth0
       <snip>
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.028.00-NAPI duplex=half latency=0 [COLOR="Red"]link=no[/COLOR] multicast=yes port=twisted pair
       resources: irq:44 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fffI assume that the ethernet cable is actually attached. You might check here: [https://wiki.archlinux.org/index.php/Configuring_Network#Realtek_no_link_.2F_WOL_issue](https://wiki.archlinux.org/index.php/Configuring_Network#Realtek_no_link_.2F_WOL_issue)> Users with Realtek 8168 8169 8101 8111(C) based NICs (cards / and on-board) may notice an issue where the NIC seems to be disabled on boot and has no Link light. This can usually be found on a dual boot system where Windows is also installed. It seems that using the offical Realtek drivers (dated anything after May 2007) under Windows is the cause. These newer drivers disable the Wake-On-LAN feature by disabling the NIC at Windows shutdown time, where it will remain disabled until the next time Windows boots.There are some suggested fixes there. I would start with Method 2.

As for the wireless, your device uses the driver iwlagn. There is sometimes a firmware problem. Let's load it and see what the logs say. Please run and post:```
rfkill list all
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

---

### Post by mmtaylor on 2012-02-23
Thanks, I looked at that Realtek issue stuff. Method 2 doesn't work for me as I apparently have one of the newer drivers.

> **Note: **Newer Realtek Windows drivers (tested with *Realtek 8111/8169 LAN Driver v5.708.1030.2008*, dated 2009/01/22, available from GIGABYTE) may refer to this option slightly differently, like *Shutdown Wake-On-LAN --> Enable*. It seems that switching it to [COLOR=#222][FONT=monospace]Disable[/FONT][/COLOR]  has no effect (you will notice the Link light still turns off upon  Windows shutdown).

Perhaps I should try rolling back to an older driver?

I also tried method 3, using a newer Linux driver, but that didn't work.

**rfkill list all output:**

```
0: hci0: Bluetooth
[INDENT]Soft blocked: no
Hard blocked: no[/INDENT]
```

sudo modprobe iwlagn didn't appear to do anything.

**dmesg | grep iwl output:**

```
[  428.308667] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  428.308668] iwlagn: Copyright(c) 2003-2010 Intel Corporation
```

---

### Post by mmtaylor on 2012-02-25
OK! So, I upgraded via USB to Oneiric. Having some graphics glitches, but I think I can figure that out, and more importantly, I have internets!

---

