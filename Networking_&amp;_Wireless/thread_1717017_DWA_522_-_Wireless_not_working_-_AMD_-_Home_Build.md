---
title: "DWA 522 - Wireless not working - AMD - Home Build"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by sirtah on 2011-03-29
Hello, 

I'm running Ubuntu 10.10 - 2.6.35-28-generic-pae i686 on a home build machine. The wireless has not been working for several months but I "duck taped" the problem by connecting my eee to my machine and using the internet that way. I'm finally getting to fixing the issue but I can't seem to figure out what the issue is. I think there might be a driver conflict because the wireless was detecting networks last night, but inconsistently - they would appear and then leave. Also, the green light on the wireless card does not work. Here is all the information I could provide:


**Wireless Card** 
DWA 522

Using Ath9k 

**lspci output:**

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:06.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)

**lspci -nn | grep 'Wireless Brand' output: **

03:06.0 Network controller [0280]: Atheros Communications Inc. AR922X Wireless Network Adapter [168c:0029] (rev 01)

**ifconfig output**
eth2      Link encap:Ethernet  HWaddr 48:5b:39:88:ff:d6  
          inet addr:10.42.43.99  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5b:39ff:fe88:ffd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1819054 (1.8 MB)  TX bytes:320389 (320.3 KB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2120 (2.1 KB)  TX bytes:2120 (2.1 KB)

wlan1     Link encap:Ethernet  HWaddr 00:18:e7:d6:1a:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**iwconfig output**
lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

**lsmod output**
arc4                    1165  2 
ath9k                  90317  0 
binfmt_misc             6599  1 
snd_hda_codec_via      51755  1 
snd_hda_intel          22299  2 
snd_hda_codec          87552  2 snd_hda_codec_via,snd_hda_intel
radeon                855860  3 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
ath9k_htc              41780  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
mac80211              235189  2 ath9k,ath9k_htc
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56825  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath9k_common            4396  2 ath9k,ath9k_htc
ath9k_hw              291798  3 ath9k,ath9k_htc,ath9k_common
snd_timer              19067  2 snd_pcm,snd_seq
led_class               2633  2 ath9k,ath9k_htc
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30200  1 radeon
ath                     8053  3 ath9k,ath9k_htc,ath9k_hw
cfg80211              142680  4 ath9k,ath9k_htc,mac80211,ath
snd                    49038  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5556  0 
sbp2                   19716  0 
parport_pc             26378  1 
drm                   168732  5 radeon,ttm,drm_kms_helper
asus_atk0110           11423  0 
psmouse                59033  0 
serio_raw               4022  0 
i2c_piix4               8795  0 
k10temp                 2607  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
ieee1394               81101  1 sbp2
agpgart                32075  2 ttm,drm
i2c_algo_bit            5168  1 radeon
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
ahci                   19198  0 
libahci                21792  1 ahci
pata_atiixp             3288  2 
r8169                  36777  0 
mii                     4425  1 r8169

**ending of dmesg**
[   31.018067] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   31.018071] apm: disabled - APM is not SMP safe.
[   31.058011] r8169 0000:02:00.0: eth2: link up
[   31.058023] r8169 0000:02:00.0: eth2: link up
[   33.483658]   alloc irq_desc for 21 on node -1
[   33.483661]   alloc kstat_irqs on node -1
[   33.483669] ath9k 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   35.042799] ath: EEPROM regdomain: 0x10
[   35.042802] ath: EEPROM indicates we should expect a direct regpair map
[   35.042804] ath: Country alpha2 being used: CO
[   35.042805] ath: Regpair used: 0x10
[   35.050341] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   35.050816] cfg80211: Calling CRDA for country: CO
[   35.050842] Registered led device: ath9k-phy0::radio
[   35.050854] Registered led device: ath9k-phy0::assoc
[   35.050865] Registered led device: ath9k-phy0::tx
[   35.050876] Registered led device: ath9k-phy0::rx
[   35.050879] phy0: Atheros AR9280 Rev:2 mem=0xf8820000, irq=21
[   35.054847] cfg80211: Regulatory domain changed to country: CO
[   35.054850]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   35.054852]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   35.054854]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   35.054856]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   35.054857]     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   35.088764] udev[379]: renamed network interface wlan0 to wlan1
[   35.110837] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   41.568020] eth2: no IPv6 routers present
[  542.159425] lo: Disabled Privacy Extensions

**sudo lshw -C network output:**
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 03
       serial: 48:5b:39:88:ff:d6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.42.43.99 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feaf0000-feafffff
  *-network
       description: Wireless interface
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan1
       version: 01
       serial: 00:18:e7:d6:1a:cc
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic-pae firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:21 memory:febf0000-febfffff

**iwlist scan output**
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

wlan1     No scan results

Thanks for reading.

---

### Post by sirtah on 2011-04-13
Help anyone?

---

### Post by josephmills on 2011-04-13
could I see a ```
rfkill list
```please

---

### Post by sirtah on 2011-04-13
josephmills, 

rfkill list returns: 

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Thanks for your response

---

### Post by josephmills on 2011-04-13
what repos do you have ticked (see pic)in software sources?

---

### Post by sirtah on 2011-04-13
Same as your screenshot - main, universe, restricted, multiverse

---

### Post by josephmills on 2011-04-13
> **sirtah said:**
> Same as your screenshot - main, universe, restricted, multiverse

what about the options tab?

---

### Post by sirtah on 2011-04-13
I just activated the unsupported updates and "http://archive ... " (and Source Code for both)

I'm updating and restarting.

---

### Post by josephmills on 2011-04-13
> **sirtah said:**
> I just activated the unsupported updates and "http://archive ... " (and Source Code for both)

I'm updating and restarting.

don't forget to ```
sudo apt-get upgrade
``` too.

---

### Post by sirtah on 2011-04-13
did the upgrade too, still nothing.

---

### Post by josephmills on 2011-04-13
at this point I dont know (above my pay grade ;) )In your lsmod I see a number of drivers that could have something to do with it but I am not sure.

---

### Post by sirtah on 2011-04-13
Thanks for your help. I think I'm going to try to get it to work with ndiswrapper.

It would be nice if there was a way to "start over" and remove all the wireless drivers that I have installed and undo all the edits I've made trying to make this work. 

With all the posts I've seen about people having issues with the DWA 552, it really should not be listed as working "out of the box." 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

Thanks again.

---

