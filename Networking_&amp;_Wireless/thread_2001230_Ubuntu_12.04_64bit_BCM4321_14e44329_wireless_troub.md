---
title: "Ubuntu 12.04 64bit BCM4321 14e4:4329 wireless troubleshooting"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by RagingDoug on 2012-06-10
Hello, 

I recently installed Ubuntu 12.04 64 bit on my desktop. I have been running this Linksys wireless N card for years, and it has always required some extra attention to get working. However, an operation that used to take less than half an hour has now spanned days, with no results.

My card is a BCM4321 chipset [14e4:4329] so in theory it should be supported by both the Broadcom STA restricted driver and by b43.

Having attempted to get both working, and getting my hands dirty with modprobe and blacklists, I am coming here for help.

I have done a fresh install, and not installed the STA driver, as I could never even get a list of networks with that installed. With the b43 driver installed, I can see a list of networks but I cannot connect to them. I know the network is up as I am connecting to it with my laptop, and have been using this desktop wifi card for years.

Here are my current setup details, I have done my best to exhaust the information I have found online.

$ lsb_release -d
```
Description:    Ubuntu 12.04 LTS
```$ uname -mr
```
3.2.0-23-generic x86_64
```$ lspci -vnn | grep -C 10 road
```
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81f8]
    Flags: bus master, fast devsel, latency 0, IRQ 75
    Memory at fbdfc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at d800 [size=256]
    Expansion ROM at fbdc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

07:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Linksys Device [1737:0060]
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

```^ I notice that most things appear to have 64 bit drivers here, but not the card, and I've been hearing some noise about ffwcutter not grabbing the right drivers. However, I did attempt to install the latest Broadcom drivers from the linux wireless page manually, and still the same results: lists of networks, can't connect.

$ iwconfig wlan0
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```$ lsmod | egrep 'b43|bc|bm|wl|ssb|xx'
```
b43                   365785  0 
mac80211              506816  1 b43
cfg80211              205544  2 b43,mac80211
bcma                   26696  1 b43
ssb                    52752  1 b43

```dmesg | egrep 'b43|bc|bm|wl|ssb|xx'
```
[    1.046058] pci 0000:01:00.0: reg 10: [io  0xbc00-0xbc07]
[    1.059566] pci 0000:03:00.0: reg 18: [mem 0xfbcc0000-0xfbcdffff 64bit]
[    1.059584] pci 0000:03:00.0: reg 30: [mem 0xfbca0000-0xfbcbffff pref]
[    1.059644] pci 0000:03:00.1: reg 10: [mem 0xfbcfc000-0xfbcfffff 64bit]
[    1.067483] pci 0000:00:03.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    1.085127] usbcore: registered new interface driver usbfs
[    1.085134] usbcore: registered new interface driver hub
[    1.085150] usbcore: registered new device driver usb
[    1.124011] pci 0000:00:03.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    1.124143] pci_bus 0000:03: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    1.444799] ata9: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 20
[    1.444804] ata10: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 20
[    1.445606] ata11: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 20
[    1.445610] ata12: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 20
[    1.530559] usbcore: registered new interface driver libusual
[    1.817185] scsi 7:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    2.460887] b43-pci-bridge 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.480502] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x12, vendor 0x4243)
[    2.480508] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0B, vendor 0x4243)
[    2.480513] ssb: Core 2 found: PCI-E (cc 0x820, rev 0x02, vendor 0x4243)
[    2.480518] ssb: Core 3 found: PCI (cc 0x804, rev 0x0D, vendor 0x4243)
[    2.480523] ssb: Core 4 found: USB 1.1 Host (cc 0x817, rev 0x04, vendor 0x4243)
[    2.532115] ssb: Sonics Silicon Backplane found on PCI device 0000:07:01.0
[    2.666183] usbcore: registered new interface driver usbhid
[   14.563859] fbcon: radeondrmfb (fb0) is primary device
[   14.670594] usbcore: registered new interface driver btusb
[   14.803404] b43-phy0: Broadcom 4321 WLAN found (core revision 11)
[   15.000013] Registered led device: b43-phy0::tx
[   15.000037] Registered led device: b43-phy0::rx
[   15.000057] Registered led device: b43-phy0::radio
[   15.000067] Broadcom 43xx driver loaded [ Features: PNL ]
[   16.913339] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   17.009377] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   17.009381] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   17.009383] b43-phy0: Controller RESET (DMA error) ...
[   17.232408] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   17.324219] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.
[   17.348751] b43-phy0: Controller restarted
[   17.349949] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.351259] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.727970] wlan0: authenticate with 00:1e:58:40:f5:eb (try 1)
[   20.729629] wlan0: authenticated
[   20.759800] wlan0: associate with 00:1e:58:40:f5:eb (try 1)
[   20.762628] wlan0: RX AssocResp from 00:1e:58:40:f5:eb (capab=0x431 status=0 aid=3)
[   20.762632] wlan0: associated
[   20.764410] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.514720] ieee80211 phy0: wlan0: No probe response from AP 00:1e:58:40:f5:eb after 500ms, disconnecting.
[   25.935529] wlan0: authenticate with 00:1e:58:40:f5:eb (try 1)
[   26.134718] wlan0: authenticate with 00:1e:58:40:f5:eb (try 2)
[   26.334264] wlan0: authenticate with 00:1e:58:40:f5:eb (try 3)
[   26.533758] wlan0: authentication with 00:1e:58:40:f5:eb timed out
[ 3686.530454] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[ 3686.602391] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.
[ 3686.636489] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3690.078105] wlan0: authenticate with 00:1e:58:40:f5:eb (try 1)
[ 3690.079644] wlan0: authenticated
[ 3690.079977] wlan0: associate with 00:1e:58:40:f5:eb (try 1)
[ 3690.082727] wlan0: RX AssocResp from 00:1e:58:40:f5:eb (capab=0x431 status=0 aid=5)
[ 3690.082731] wlan0: associated
[ 3690.085138] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3693.581404] ieee80211 phy0: wlan0: No probe response from AP 00:1e:58:40:f5:eb after 500ms, disconnecting.
[ 3695.021920] wlan0: authenticate with 00:1e:58:40:f5:eb (try 1)
[ 3695.221323] wlan0: authenticate with 00:1e:58:40:f5:eb (try 2)
[ 3695.420865] wlan0: authenticate with 00:1e:58:40:f5:eb (try 3)
[ 3695.620385] wlan0: authentication with 00:1e:58:40:f5:eb timed out

```$ sudo lshw -C network
 ```
 *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 48:5b:39:7e:02:d6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.186 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:75 memory:fbdfc000-fbdfffff ioport:d800(size=256) memory:fbdc0000-fbddffff
  *-network
       description: Network controller
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:07:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:fbefc000-fbefffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:39:15:8a:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg
```$ iwlist scan
```
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.
```

---

### Post by chili555 on 2012-06-10
Everything I have or have read suggests that STA is correct and b43 is not. I suggest you blacklist b43, install STA and that we troubleshoot from there.

This is ugly:> [   17.009377] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   17.009381] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   17.009383] b43-phy0: Controller RESET (DMA error) ...
[   17.232408] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   17.324219] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.

---

### Post by RagingDoug on 2012-06-10
I agree it is ugly. Last time I tried STA with blacklisted b43 I couldn't even get a list of wireless networks, but I'll try it again. I'll post my results shortly.

---

### Post by RagingDoug on 2012-06-10
I blacklisted b43 in /etc/modprobe.d/blacklist.conf, followed by

```
sudo modprobe -r b43
```Then I installed the STA drivers from additional drivers, I see my chipset is supposedly supported(BCM4329). The  light goes green and states that it is active and currently in use.

After toggling networking on and off, my wired connection comes back and I have lost my list of wifi networks, all I see now is Wireless Networks : disconnected, same after ```
modprobe -r wl; modprobe wl
```I see that installing the driver has created a new blacklist file, so here are my blacklists now:

$ cat /etc/modprobe.d/blacklist-bcm43.conf
```
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
```$ cat /etc/modprobe.d/blacklist.conf 
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

blacklist b43

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```
$ lspci -vnn | grep -C 10 road
```
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81f8]
    Flags: bus master, fast devsel, latency 0, IRQ 75
    Memory at fbdfc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at d800 [size=256]
    Expansion ROM at fbdc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

07:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Linksys Device [1737:0060]
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
    Kernel modules: wl, ssb

07:02.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. M4A series motherboard [1043:81fe]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fbefb000 (32-bit, non-prefetchable) [size=2K]

```$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 48:5b:39:7e:02:d6  
          inet addr:192.168.0.186  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5b:39ff:fe7e:2d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2492679 (2.4 MB)  TX bytes:289086 (289.0 KB)
          Interrupt:18 

eth3      Link encap:Ethernet  HWaddr 00:18:39:15:8a:72  
          inet6 addr: fe80::218:39ff:fe15:8a72/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:686
          TX packets:0 errors:15 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23134 (23.1 KB)  TX bytes:23134 (23.1 KB)
```$ iwconfig
```
eth3      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lo        no wireless extensions.

eth0      no wireless extensions.
```$ lsmod
```
Module                  Size  Used by
wl                   2568210  0 
lib80211_crypt_tkip    17390  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
hidp                   22628  2 
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  0 
btusb                  18288  6 
bluetooth             180104  32 hidp,rfcomm,bnep,btusb
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
mxm_wmi                12979  0 
snd_hda_intel          33773  5 
snd_seq_midi           13324  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_rawmidi            30748  1 snd_seq_midi
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
asus_atk0110           18078  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
psmouse                87603  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
radeon                804372  3 
i7core_edac            28102  0 
wmi                    19256  1 mxm_wmi
serio_raw              13211  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53746  3 i7core_edac
snd_timer              29990  2 snd_pcm,snd_seq
ttm                    76949  1 radeon
mac_hid                13253  0 
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
i2c_algo_bit           13423  1 radeon
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  2 hidp,usbhid
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   59043  0
```$ dmesg | tail -n 23
```
[  567.020150] b43-pci-bridge 0000:07:01.0: PCI INT A disabled
[  669.184728] lib80211: common routines for IEEE802.11 drivers
[  669.184735] lib80211_crypt: registered algorithm 'NULL'
[  669.186817] wl: module license 'MIXED/Proprietary' taints kernel.
[  669.186820] Disabling lock debugging due to kernel taint
[  669.191190] wl 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  669.214118] lib80211_crypt: registered algorithm 'TKIP'
[  669.240075] eth3: Broadcom BCM4329 802.11 Hybrid Wireless Controller 5.100.82.38
[  669.269296] udevd[2626]: renamed network interface eth1 to eth3
[  669.299667] wl 0000:07:01.0: PCI INT A disabled
[  669.299782] wl 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  669.347445] eth3: Broadcom BCM4329 802.11 Hybrid Wireless Controller 5.100.82.38
[  669.368946] udevd[2626]: renamed network interface eth1 to eth3
[  680.047676] sky2 0000:05:00.0: eth0: disabling interface
[  681.249885] sky2 0000:05:00.0: eth0: enabling interface
[  681.251695] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  694.478790] sky2 0000:05:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[  694.480635] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  704.702423] eth0: no IPv6 routers present
[  765.564388] wl 0000:07:01.0: PCI INT A disabled
[  772.774671] wl 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  772.821813] eth3: Broadcom BCM4329 802.11 Hybrid Wireless Controller 5.100.82.38
[  772.863592] udevd[8675]: renamed network interface eth1 to eth3
```$ sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 48:5b:39:7e:02:d6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.186 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:75 memory:fbdfc000-fbdfffff ioport:d800(size=256) memory:fbdc0000-fbddffff
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:07:01.0
       logical name: eth3
       version: 01
       serial: 00:18:39:15:8a:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=64 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbefc000-fbefffff
```$ iwlist scan
```
eth3      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by chili555 on 2012-06-10
Network Manager will default to wired if you have it available and you do:> eth0      Link encap:Ethernet  HWaddr 48:5b:39:7e:02:d6  
          [COLOR="Red"]inet addr:192.168.0.186 [/COLOR] Bcast:192.168.0.255  Mask:255.255.255.0If you detach the ethernet cable and wait for NM to notice the change in state, can you click on your network and try to connect? Does it ask for a WPA2 password? Does it try to connect?

Any interesting messages here?```
sudo cat /var/log/syslog | grep -e wl -e eth3 | tail -n20
```

---

### Post by RagingDoug on 2012-06-10
Still no networks listed, Wireless networks: disconnected is grayed out

$ sudo cat /var/log/syslog | grep -e wl -e eth3 | tail -n20
```
Jun 10 16:38:59 desktop NetworkManager[1045]: <info> (eth3): cleaning up...
Jun 10 16:39:01 desktop NetworkManager[1045]: <info> (eth3): now managed
Jun 10 16:39:01 desktop NetworkManager[1045]: <info> (eth3): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 16:39:01 desktop NetworkManager[1045]: <info> (eth3): bringing up device.
Jun 10 16:39:01 desktop NetworkManager[1045]: <info> (eth3): deactivating device (reason 'managed') [2]
Jun 10 16:39:03 desktop NetworkManager[1045]: <info> (eth3): bringing up device.
Jun 10 16:39:03 desktop NetworkManager[1045]: <info> (eth3): supplicant interface state: starting -> ready
Jun 10 16:39:03 desktop NetworkManager[1045]: <info> (eth3): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 10 16:39:03 desktop NetworkManager[1045]: <info> (eth3): supplicant interface state: ready -> inactive
Jun 10 16:40:40 desktop NetworkManager[1045]: <info> (eth3): now unmanaged
Jun 10 16:40:40 desktop NetworkManager[1045]: <info> (eth3): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Jun 10 16:40:40 desktop NetworkManager[1045]: <info> (eth3): taking down device.
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): now managed
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): bringing up device.
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): preparing device.
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): deactivating device (reason 'managed') [2]
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): supplicant interface state: starting -> ready
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 10 16:40:42 desktop NetworkManager[1045]: <info> (eth3): supplicant interface state: ready -> inactive
```

---

### Post by chili555 on 2012-06-10
Please do:```
sudo gedit /etc/network/interfaces
```Make sure no more than this appears:```
auto lo
iface lo inet loopback
```If there is more, please remove it. Also check here:```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```If it's not already, change managed to true. In both cases, proofread carefully, save and close the text editor. Now restart NM:```
sudo service network-manager restart
```Are networks now available?

I will be away for the evening; see you tomorrow.

---

### Post by RagingDoug on 2012-06-10
Hi, thanks for your time so far. Unfortunately I still can not see any networks listed.

/etc/networks/interfaces

```

auto lo
iface lo inet loopback

```

/etc/NetworkManager/NetworkManager.con

```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

I changed managed to true and then restared network manager, still no networks listed.

---

### Post by chili555 on 2012-06-11
> udevd[8675]: renamed network interface eth1 to eth3I'm not sure this has much to do with our problem, but let's fix it as we run some other diagnostic tests and see if there is any change. Please do:```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```You should find four listings. eth0 is your wired ethernet device; leave it unchanged. There will be a listing for eth3 with the driver wl, or it might show wl0. Change it to eth1; the Broadcom STA driver uses eth1, typically, not wlan0.

Comment out the other entries, eth1 and eth2, thus:```
# PCI device 0x8086:0x109a (whatever)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:16:41:e6:cb:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```The hashmark will tell the system that these are comments and not to act on them. Proofread carefully, save and close gedit. Reboot immediately with the ethernet cable detached. Then run this command:```
dmesg > doug.txt
```Find the file doug.txt in your user directory and paste it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Please give us the link in your reply.

---

### Post by RagingDoug on 2012-06-13
Hey, sorry for the delay in response, I was out of town for work.
I made those changes and then posted my dmesg after a reboot

[http://paste.ubuntu.com/1038439/](http://paste.ubuntu.com/1038439/)

---

### Post by chili555 on 2012-06-13
> **RagingDoug said:**
> Hey, sorry for the delay in response, I was out of town for work.
I made those changes and then posted my dmesg after a reboot

[http://paste.ubuntu.com/1038439/](http://paste.ubuntu.com/1038439/)WORK?!? That's a dirty word at my house. Seriously, I completely understand and no problems.

I feel like the old days, in my garage: "It has gas, air and spark but it just won't start." I can see nothing wrong in *dmesg* to fix. I think I'd like to explore this:> ^ I notice that most things appear to have 64 bit drivers here, but not the card, I'm not sure we know that explicitly from your readings, however, Broadcom has a STA driver marked for 64-bit here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I suggest you download it to your desktop. Right-click it and select *Extract Here*. Now open the folder it extracted and drill down to src/wl/sys and open the file wl_linux.c with a text editor. Find the line containing *.ndo_set_multicast_list = wl_set_multicast_list,* and change it to *.ndo_set_rx_mode = wl_set_multicast_list,*  Please see attached.

In the file I downloaded for a 32-bit system, it was at line 388. Be very careful about spacing, indentation, punctuation, etc. Proofread carefully, save and close the text editor. Now open a terminal and do:```
cd Desktop/hybrid
```Now we'll use a trick. Press Tab and the remainder will fill in automagically! Press Enter. Now do:```
sudo su
make clean
make
make install
modprobe -r wl
modprobe wl
exit
```Any improvement?

---

### Post by GouZi on 2012-09-16
Hi,
 I have the same chip set, BCM4321 14e4:4329, running Ubuntu 12.04 64 bits.

I tried all the steps mentioned in this thread, including recompiling the sta driver provided by Broadcom.

But no luck, Wireless Networks: disconnected is still grayed out.

By chance is there anything else I can try?

---

### Post by chili555 on 2012-09-16
> **GouZi said:**
> Hi,
 I have the same chip set, BCM4321 14e4:4329, running Ubuntu 12.04 64 bits.

I tried all the steps mentioned in this thread, including recompiling the sta driver provided by Broadcom.

But no luck, Wireless Networks: disconnected is still grayed out.

By chance is there anything else I can try?Please run and post:```
sudo modprobe wl
dmesg | grep -e wl -e eth1
```Thanks.

---

