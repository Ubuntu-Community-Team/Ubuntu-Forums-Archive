---
title: "D-Link DWA-556|Ubuntu 12.04 - No Wireless Connections"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by murderous mouse on 2012-08-22
Hi Guys,

My Computer died recently at an incredibly inconvenient time and I've decided that this would be the best time to move myself over to 100% ubuntu. I have encountered a problem though: My wireless card in my desktop is largely ignored by Ubuntu and thus I cannot connect to the internet.

I don't have access to wired internet (not just because I'm lazy but because my building has a wireless signal and I have no router/switch access). While trying to fix this I have been simply pulling the system disk out of my computer and chucking it into a laptop so that I can apt-get things I may need, however this doesn't work particularly well in that it's very time consuming but the only other way I can do it is to "apt-get download -d <Package>" and put it on a USB to install it later.

I have been trying to fix this for the last 3 days or so without taking nearly enough breaks so if I sound a little confused it's the sleep deprivation kicking in so bear with me.

Bellow is attached all the information I would imagine is relevant, if you need any more information about the system environment or the hardware feel free to ask, as far as what has been done on this fresh install of ubuntu, all I know is that the wireless never worked and to try and fix it I followed along with a few guides about installing things called "backports" and running a few packages which, based on reading the prompts, looked like they were messing with the kernel etc, everything I've done was followed word for word so hopefully I didn't do to much harm, and if I did then I can just format again and it's not a problem :)


**lspci**

```
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:05.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cypress XT [Radeon HD 5870]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cypress HDMI Audio [Radeon HD 5800 Series]
04:00.0 Network controller: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev ff)
06:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
07:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
07:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0a:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
```

**lspci -nn | grep 'Atheros'**

```
04:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) [168c:0024] (rev ff)

```

**ifconfig**

```
eth0      Link encap:Ethernet  HWaddr 00:1f:bc:01:f1:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1f:bc:01:f1:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87712 (87.7 KB)  TX bytes:87712 (87.7 KB)
```

**iwconfig**

```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.
```

**iwconfig wlan0**

```
wlan0     No such device
```

**lsmod**

```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
dm_crypt               23125  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
snd_usb_audio         122982  1 
bnep                   18139  2 
snd_usbmidi_lib        25395  1 snd_usb_audio
serio_raw              13211  0 
rfcomm                 46621  0 
parport_pc             32866  0 
bluetooth             185573  10 bnep,rfcomm
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
ppdev                  17113  0 
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
ath9k                 130564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              514621  1 ath9k
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
uvcvideo               72627  0 
snd_timer              29990  2 snd_pcm,snd_seq
videodev               98259  1 uvcvideo
ath9k_common           14053  1 ath9k
snd_seq_device         14540  3 snd_seq_midi,snd_seq,snd_rawmidi
ath9k_hw              400326  2 ath9k,ath9k_common
v4l2_compat_ioctl32    17128  1 videodev
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              209821  3 ath9k,mac80211,ath
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
i7core_edac            28102  0 
soundcore              15091  1 snd
edac_core              53746  3 i7core_edac
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
hid_microsoft          12888  0 
mxm_wmi                12979  0 
radeon                804372  3 
crc_itu_t              12707  1 firewire_core
ttm                    76949  1 radeon
usbhid                 47199  0 
drm_kms_helper         46978  1 radeon
hid                    99559  2 hid_microsoft,usbhid
drm                   242038  5 radeon,ttm,drm_kms_helper
r8169                  62099  0 
pata_jmicron           12747  0 
i2c_algo_bit           13423  1 radeon
wmi                    19256  1 mxm_wmi
usb_storage            49198  1 
```

**dmesg | grep "ath"**

```
[   12.221973] ath9k 0000:04:00.0: Refused to change power state, currently in D3
[   12.221982] ath9k 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.323483] ath: Couldn't reset chip
[   12.323486] ath: Unable to initialize hardware; initialization status: -5
[   12.323490] ath9k 0000:04:00.0: Failed to initialize device
[   12.323545] ath9k 0000:04:00.0: PCI INT A disabled
[   12.323552] ath9k: probe of 0000:04:00.0 failed with error -5
[   33.001088] type=1400 audit(1345765759.906:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2274 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```


**sudo lshw -C network**

```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:1f:bc:01:f1:1c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:ae00(size=256) memory:f3dff000-f3dfffff memory:f3df8000-f3dfbfff memory:f3ee0000-f3efffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 03
       serial: 00:1f:bc:01:f1:1d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:9e00(size=256) memory:f3bff000-f3bfffff memory:f3bf8000-f3bfbfff memory:f3ce0000-f3cfffff
```

**iwlist scan**

```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

**lsb_release -d**

```
Description:	Ubuntu 12.04.1 LTS
```

**uname -mr**

```
3.2.0-29-generic x86_64
```

**sudo /etc/init.d/networking restart**

```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 
```

Post the mass of stuff something I noticed as I was copying this stuff across is that the end of the line about the network card which is like (rev ff) has been (rev 1) in most other stuff I've seen where someone is demonstrating with a working machine.

Cheers,
MM


EDIT

Sorry, I forgot to mention:

I had a look at madwifi and, while I would love to be proven wrong, it looks like it's completely depreciated and isn't really a feasible solution.

Also, there is a wrapper for windows drivers (I can't remember the name because my brain is shutting down sorry!) but you would also need to use a 32x OS, my RAM is quite important to me so once again I would love to be proven wrong (and that's entirely likely) but it just seems like a massive drawback.

Cheers Again,
MM

---

### Post by chili555 on 2012-08-22
> ath: Unable to initialize hardware; initialization status: -5That's the tell-tale. Please see: [http://ubuntuforums.org/showthread.php?t=1960174](http://ubuntuforums.org/showthread.php?t=1960174)> Yes, indeed! The native driver ath9k wouldn't drive your card so you installed the Windows driver with ndiswrapper. It refuses to drive your card, too! Also see: [http://www.digipedia.pl/usenet/thread/19131/2152/](http://www.digipedia.pl/usenet/thread/19131/2152/)> Looks like a hardware issue to me. Try removing the card and plugging it back in.A Google search will yield many complaints and no operating system or driver fixes that I can find.

---

### Post by murderous mouse on 2012-08-22
I don't think it could be anything to do with broken hardware, it's been working perfectly for the last few years on Windows 7 so I don't see why it would stop being ok now.

I thought it may have to do with the way that the driver is interfacing with the card, I can't remember where I read this but at one point someone mentioned that the error code of -5 means that there is invalid data being returned. Not to mention that the card still declares that it's there when I check all PCI slots.

---

