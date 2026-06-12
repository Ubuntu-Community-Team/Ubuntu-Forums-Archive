---
title: "Linksys WMP54GS 14E4:4318 BCM4318 not working"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by Zaelyx on 2010-02-20
I've been attempting over the past week to get this card working, to no avail. I've tried using ndiswrapper and b43; the card is said to be supported on b43 but for some reason with the pci id of 14e4:4320 instead of mine which is 14e4:4318

I am running Ubuntu 9.10 64 bit on a HP Pavilion a1314n (with XP pre-installed)
Any help would be appreciated.

Below is some information:

```

ekly@server:~$ lspci -vnn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
	Expansion ROM at fdf80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil

00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (prog-if 01)
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS480 [Radeon Xpress 200G Series] [1002:5954]
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at ee00 [size=256]
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon

02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at dc00 [size=256]
	Memory at fddff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp

02:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Linksys Device [1737:0042]
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at fdd00000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

```

```

ekly@server:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:15:f2:9e:53:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:dc00(size=256) memory:fddff000-fddff0ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:fdd00000-fdd01fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0e:3b:1e:d0:9e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.123 multicast=yes wireless=IEEE 802.11bg


```

*** Why does it not have a logical name? Wlan0 is my usb dongle and eth0 is my wired connection, so why does the 14E4:4318 display that it loads the driver b43-pci-bridge and load ssb?

```

ekly@server:~$ dmesg | grep ssb
[   13.842230] ssb: WARNING: Invalid SPROM CRC (corrupt SPROM)
[   13.842238] ssb: Unsupported SPROM  revision 255 detected. Will extract v1
[   13.880058] ssb: Backplane Revision 0x30000000
[   13.880077] WARNING: at /build/buildd/linux-2.6.31/drivers/ssb/main.c:1041 ssb_tmslow_reject_bitmask+0x5a/0x90 [ssb]()
[   13.880082] Modules linked in: x_tables(+) ppdev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device shpchp parport_pc parport ssb(+) serio_raw snd soundcore snd_page_alloc i2c_piix4 amd64_edac_mod edac_core k8temp usb_storage hid_microsoft usbhid ohci1394 8139too ieee1394 8139cp mii radeon ttm drm i2c_algo_bit
[   13.880131]  [<ffffffffa01a751a>] ssb_tmslow_reject_bitmask+0x5a/0x90 [ssb]
[   13.880137]  [<ffffffffa01a7569>] ssb_device_is_enabled+0x19/0x50 [ssb]
[   13.880143]  [<ffffffffa01aabc4>] ssb_pcicore_init+0x24/0x70 [ssb]
[   13.880149]  [<ffffffffa01a70a7>] ssb_attach_queued_buses+0xb7/0x120 [ssb]
[   13.880156]  [<ffffffffa01a8c20>] ? ssb_pci_get_invariants+0x0/0x90 [ssb]
[   13.880162]  [<ffffffffa01a72e2>] ssb_bus_register+0x1d2/0x240 [ssb]
[   13.880174]  [<ffffffffa01a73e5>] ssb_bus_pcibus_register+0x35/0x70 [ssb]
[   13.880180]  [<ffffffffa01a960b>] ssb_pcihost_probe+0xcb/0x130 [ssb]
[   13.880279] ssb: Sonics Silicon Backplane found on PCI device 0000:02:09.0


```

```

ekly@server:~$ dmesg | grep b43
[   13.755842] b43-pci-bridge 0000:02:09.0: enabling device (0000 -> 0002)
[   13.755854] b43-pci-bridge 0000:02:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17


```

```

ekly@server:~$ lsmod
Module                  Size  Used by
b43                   136584  0 
cryptd                  8008  0 
aes_x86_64              8992  3 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
lp                     11908  0 
arc4                    2144  2 
ecb                     3296  2 
rt73usb                29092  0 
crc_itu_t               2336  1 rt73usb
rt2500usb              23364  0 
rt2x00usb              13600  2 rt73usb,rt2500usb
rt2x00lib              34624  3 rt73usb,rt2500usb,rt2x00usb
led_class               5256  2 b43,rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210008  3 b43,rt2x00usb,rt2x00lib
cfg80211              109144  3 b43,rt2x00lib,mac80211
snd_atiixp             19284  2 
snd_ac97_codec        125720  1 snd_atiixp
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
joydev                 13088  0 
snd_seq_dummy           3460  0 
iptable_filter          3872  0 
snd_seq_oss            33440  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
ppdev                   8232  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 37756  0 
parport_pc             37352  1 
parport                40528  3 lp,ppdev,parport_pc
ssb                    40944  1 b43
serio_raw               6596  0 
snd                    77096  14 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_atiixp,snd_pcm
i2c_piix4              11728  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
k8temp                  5504  0 
usb_storage            66016  0 
hid_microsoft           4292  0 
usbhid                 43968  0 
ohci1394               33780  0 
8139too                27360  0 
ieee1394              100896  1 ohci1394
8139cp                 23200  0 
mii                     6368  2 8139too,8139cp
radeon                684512  2 
ttm                    43056  1 radeon
drm                   193856  4 radeon,ttm
i2c_algo_bit            7076  1 radeon



```

The computer is running apache2 and openssh, if that makes any difference.

---

### Post by pdc on 2010-02-20
I suspect you need the Broadcom STA driver;

but happy to be shot down in flames if I am wrong;

this guide

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

talks about how to install the STA for similar cards

if you have tried nsdiswrapper and b43 they will need to be blacklisted surely;

if my comment on the STA were indeed to prove correct

---

### Post by northd_tech on 2010-02-21
> **Zaelyx said:**
> 

02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2a26]
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at dc00 [size=256]
    Memory at fddff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

02:09.0 Network controller [0280]: **Broadcom** Corporation BCM**4318** [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Linksys Device [1737:0042]
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at fdd00000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: **b43-pci-bridge**
    Kernel modules: **ssb**
[/CODE]```

ekly@server:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:15:f2:9e:53:02
       width: **32 bits**
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:dc00(size=256) memory:fddff000-fddff0ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 02
       width: **32 bits**
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:fdd00000-fdd01fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0e:3b:1e:d0:9e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.123 multicast=yes wireless=IEEE 802.11bg

lsmod
Module                  Size  Used by
b43                   136584  0 
[COLOR=DarkGreen]
rt73usb                29092  0 
crc_itu_t               2336  1 rt73usb
rt2500usb              23364  0 
rt2x00usb              13600  2 rt73usb,rt2500usb
rt2x00lib              34624  3 rt73usb,rt2500usb,rt2x00usb[/COLOR]
led_class               5256  2 **b43**,rt2x00lib
[COLOR=DarkGreen]input_polldev           4720  1 rt2x00lib[/COLOR]
mac80211              210008  3 **b43**,rt2x00usb,rt2x00lib
cfg80211              109144  3 **b43**,rt2x00lib,mac80211

ssb                    40944  1** b43**

8139too                27360  0 
8139cp                 23200  0 
mii                     6368  2 8139too,8139cp

Are you sure that's 64-bit?  Can you run this in a terminal?** uname -a**

It almost looks like you've got 32 bit modules loaded to me, and I'm not sure that all that "usb" stuff that I highlighted in green even needs to be there, but it appears to be related to the 802.11 wireless modules somehow.

You also might have a conflict with those Realtek 8139 modules (I saw another one of those earlier this week):

http://ubuntuforums.org/showthread.php?t=1406907

There are many threads here about the Broadcom 4318 (and it doesn't look like one of the easier ones like my Broadcom "4328" that uses the proprietary STA driver mentioned above).

http://ubuntuforums.org/tags.php?tag=broadcom+4318

Can you also post the results of these terminal commands?

[CODE]less /etc/modules 

less /etc/modprobe.d/blacklist

less /etc/modprobe.d/blacklist.conf 			 		
```

---

### Post by Zaelyx on 2010-02-21
I tried the STA drivers, still saw nothing in the hardware drivers menu

I think the USB modules are loaded because I am using a usb wireless card in the meantime (unfortunately it can't be a permanent solution).

Wired internet works...

When I run less on /etc/modules and /etc/modprobe.d/blacklist , they return (END)...the files exist but are empty. 
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

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

```

ekly@server:~$ uname -a
Linux server 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux


```

---

### Post by northd_tech on 2010-02-21
> **Zaelyx said:**
> 
# replaced by b43 and ssb.
blacklist bcm43xx

It looks like the "legacy" b43 module is blacklisted in 

/etc/modprobe.d/blacklist.conf

That is a 64-bit Linux, but both network modules show 32 bit.  This may not be a problem- my NVIDIA nForce ethernet works and shows to be 32-bit while my Broadcom "4328" shows to be 64-bit in **sudo lshw -C network**.

According to this website (search the page for "ubuntu"):

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

all you need to do is run this command under ubuntu or Debian:

```
sudo apt-get install b43-fwcutter

```

The Broadcom 4318 does show to be one of the working/supported chipsets there, but it mentions the following message under "not working yet":

> AP mode using 4318 because of packet loss in high transmission rates.  Hard to debug & fix. 

I'm wondering if you should remove the b43 and ssb modules and try starting over from scratch with that apt-get command.  It is possible that the USB or Realtek ethernet configurations had messed up the wireless Broadcom 4318 somehow, or else the configuration just never worked.

If you want to try that, run this command sequence with a working network connection (and verify that the lsmod commands come up empty- that the b43 and ssb modules were actually removed):

```

sudo rmmod ssb

sudo rmmod b43

lsmod | grep b43

lsmod | grep ssb

sudo apt-get install b43-fwcutter

```

Other people have mentioned needing to disconnect the ethernet cable (and possibly your "[COLOR=DarkGreen]rt73usb" [/COLOR]USB WiFi) before restarting the computer after that command sequence to "force" wireless connection with some Broadcoms.  I'm not sure why that would work but others have said it did work to get Broadcom wireless, so it is worth a shot.

Of course, check the wireless switch (I've heard of someone's cat hitting that and disabling wireless before, but maybe they were just blaming the cat ;) ).

Are you sure that all traces of that Broadcom STA driver are gone?  Your 4318 does not show to be one of the supported ones under STA (while it works great with my 4321AG that lspci identifies as "4328" and worked "out of the box" with Jaunty 9.04 after I activated the STA driver).

This command should come up empty if the STA driver is not installed:

```
lsmod | grep wl
```

If you do get it working, can you post some details on the working configuration?  The 4318 has been a "problem child" lately, and documentation is a little scarce on it.  It seems to fall in that "not a 4311/12 not a 432x Broadcom" gap that won't work with the STA driver.

---

### Post by Zaelyx on 2010-03-03
Magically, it works!
I literally did almost nothing...a related error brought to my attention that it worked again.
I have my suspicions (though not sure if update manager keeps logs of my updates) though. I blacklisted the B43 and SSB modules and reinstalled ndiswrapper with the BCMWL5 64 bit driver. It did not work initially so I left that alone and used my USB dongle. However, for some odd reason the IP address I statically set for my device would randomly stop being pingable and locatable on the network map from my Windows PC. I investigated this issue and it turned out that it was the drivers conflicting: ndiswrapper and the one loading my wireless USB card.
I suspect that Ndiswrapper was upgraded to the newest version and somehow that made it work. Honestly at a loss...not sure what all happened just happy that it works now. If anybody could tell me how to confirm my suspicions that a Ndiswrapper upgrade fixed the issue, i'd like to know!

---

### Post by bkratz on 2010-03-03
It would be interesting to see the outputs again for the following

lsmod
sudo lshw -C network
iwconfig

The earlier listing of lsmod did not show the ndiswrapper module ( unless my bifocals fogged). The second command should show the ndiswrapper module next to the driver also along with the actual driver name. Just curious no real need.

---

### Post by Zaelyx on 2010-03-05
and again the thing stopped working, sometime randomly last night. seriously considering that the chip is faulty, it randomly works and then doesnt...the light comes on when it works and i dont even touch it and it goes off. idk what to do =/

---

### Post by Zaelyx on 2010-03-07
I've given up on the card...after trying it in a different computer running ubuntu and one running windows, the card failed on all three. It is a faulty device, I have concluded. 
Luckily, I found an old Linksys router in my basement. After some research, i converted it into a wireless bridge and have the ubuntu system connected to it without a flaw. Sorry to have wasted some of your time ^^;

---

