---
title: "PCI Realtek RTL-8185 &quot;wireless disabled by hardware&quot;"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by macdo on 2011-08-21
Hello all,

For reasons of "soon to arrive baby taking over my office" :D I have had to install a wifi PCI card in my PC. It's a TrendNet TEW423PI and the chip is a Realtek rtl-8185.

Unfortunately, the card will not connect  and if I hover on the network manager widget, it says "wireless disabled by hardware". 

I have run a few commands to try to understand what is going on but I can't see anything wrong.

```
 ------------------------------------------------------------------------------
macdo@McMachine:~$ sudo lshw -C network
[sudo] password for macdo: 
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: wlan0
       version: 20
       serial: 00:14:d1:e3:52:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180
driverversion=2.6.38-11-generic-pae firmware=N/A latency=32 link=no
maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 ioport:cc00(size=256) memory:fdefe000-fdefe3ff
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:23:54:84:a8:7c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt
10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth
driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes
port=MII
       resources: irq:41 memory:fe02b000-fe02bfff ioport:d800(size=8)
memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
macdo@McMachine:~$ 
--------------------------------------------------------------------------------
--------


macdo@McMachine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:84:a8:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x2000                                      
                  
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0                             
          RX bytes:2840 (2.8 KB)  TX bytes:2840 (2.8 KB)        
		  
wlan0     Link encap:Ethernet  HWaddr 00:14:d1:e3:52:84
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                  
          collisions:0 txqueuelen:1000                                          
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           
macdo@McMachine:~$ 
--------------------------------------------------------------------------------
---------

macdo@McMachine:~$ lsmod
Module                  Size  Used by                                           
                                                                                
                  
nls_iso8859_1          12617  1                                                 
nls_cp437              12751  1                                                 
vfat                   17335  1                                                 
fat                    55505  1 vfat                                            
parport_pc             32111  0                                                 
ppdev                  12849  0                                                 
dm_crypt               22463  0                                                 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  5 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
nvidia               9766978  39 
rtl8180                35687  0 
mac80211              257001  1 rtl8180
eeprom_93cx6           12653  1 rtl8180
snd_hda_intel          28209  2 
cfg80211              156212  2 rtl8180,mac80211
snd_hda_codec          90901  3
snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14
snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,
snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
k10temp                12951  0 
i2c_nforce2            12906  0 
asus_atk0110           17664  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
joydev                 17322  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
firewire_ohci          31504  0 
ahci                   21591  3 
firewire_core          56138  1 firewire_ohci
floppy                 60032  0 
crc_itu_t              12627  1 firewire_core
video                  18951  0 
forcedeth              58190  0 
libahci                25548  1 ahci
pata_amd               13762  0 
macdo@McMachine:~$ 
--------------------------------------------------------------------------------
----------------

macdo@McMachine:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: wlan0
       version: 20
       serial: 00:14:d1:e3:52:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180
driverversion=2.6.38-11-generic-pae firmware=N/A latency=32 link=no
maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 ioport:cc00(size=256) memory:fdefe000-fdefe3ff
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:23:54:84:a8:7c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt
10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth
driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes
port=MII
       resources: irq:41 memory:fe02b000-fe02bfff ioport:d800(size=8)
memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
macdo@McMachine:~$ 
--------------------------------------------------------------------------------
----------------

macdo@McMachine:~$ lsb_release -d
Description:    Ubuntu 11.04
macdo@McMachine:~$ 
--------------------------------------------------------------------------------
----------------

macdo@McMachine:~$ uname -mr
2.6.38-11-generic-pae i686
macdo@McMachine:~$ 
--------------------------------------------------------------------------------
----------------

macdo@McMachine:~$ rfkill list all
0: phy0 : Wireless LAN
		Soft blocked: no
		Hard blocked: no
macdo@McMachine:~$
---------------------------------------------------------------------------------


dmesg 

(...)
  4.524054] ACPI: resource nForce2_smbus [io  0x1c40-0x1c7f] conflicts with ACPI
region SM00 [io 0x1c40-0x1c7f]
[    4.524059] ACPI: If an ACPI driver is available for this device, you should
use it instead of the native driver
[    4.553953] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring
disabled
[    5.014712] cfg80211: Calling CRDA to update world regulatory domain
[    5.026090] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[    5.026099] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level,
low) -> IRQ 21
[    5.026103] hda_intel: Disable MSI for Nvidia chipset
[    5.026133] HDA Intel 0000:00:07.0: setting latency timer to 64
[    5.257964] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    5.257986] rtl8180 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level,
low) -> IRQ 18
[    5.376053] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376061] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376064] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376068] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376070] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376073] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376075] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376078] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376080] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376083] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376087] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376089] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376092] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376094] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376096] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376099] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376101] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376104] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376106] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376109] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376111] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376114] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376116] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376119] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376121] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376124] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.376126] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz
width channel with regulatory rule:
[    5.376129] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[    5.414445] nvidia: module license 'NVIDIA' taints kernel.
[    5.414449] Disabling lock debugging due to kernel taint
[    5.939298] nvidia 0000:02:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level,
low) -> IRQ 16
[    5.939309] nvidia 0000:02:00.0: setting latency timer to 64
[    5.939314] vgaarb: device changed decodes:
PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    5.939478] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr
18 14:54:25 PDT 2011
[    5.972854] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    5.973445] ieee80211 phy0: hwaddr 0014d1e35284, RTL8185vD + rtl8225z2
[    6.155977] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz
width channel with regulatory rule:
[    6.155982] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.155986] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz
width channel with regulatory rule:
[    6.155989] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.155991] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz
width channel with regulatory rule:
[    6.155994] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.155996] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz
width channel with regulatory rule:
[    6.155999] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156015] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156019] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156021] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156024] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156026] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156029] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156031] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156034] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156036] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156039] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156041] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156044] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156046] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156049] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156051] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156054] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156056] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156059] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156061] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz
width channel with regulatory rule:
[    6.156064] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[    6.156069] cfg80211: World regulatory domain updated:
[    6.156071] cfg80211:     (start_freq - end_freq @ bandwidth),
(max_antenna_gain, max_eirp)
[    6.156074] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,
2000 mBm)
[    6.156076] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi,
2000 mBm)
[    6.156079] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi,
2000 mBm)
[    6.156082] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,
2000 mBm)
[    6.156084] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi,
2000 mBm)
[    6.244775] ACPI: PCI Interrupt Link [AE0B] enabled at IRQ 16
[    6.244784] HDA Intel 0000:02:00.1: PCI INT B -> Link[AE0B] -> GSI 16 (level,
low) -> IRQ 16
[    6.244788] hda_intel: Disable MSI for Nvidia chipset
[    6.244842] HDA Intel 0000:02:00.1: setting latency timer to 64
[    6.294900] type=1400 audit(1313931335.635:2): apparmor="STATUS"
operation="profile_load" name="/sbin/dhclient" pid=691 comm="apparmor_parser"
[    6.295281] type=1400 audit(1313931335.635:3): apparmor="STATUS"
operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=691 comm="apparmor_parser"
[    6.295528] type=1400 audit(1313931335.635:4): apparmor="STATUS"
operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=691
comm="apparmor_parser"
[    6.296132] type=1400 audit(1313931335.639:5): apparmor="STATUS"
operation="profile_replace" name="/sbin/dhclient" pid=677 comm="apparmor_parser"
[    6.296154] type=1400 audit(1313931335.639:6): apparmor="STATUS"
operation="profile_replace" name="/sbin/dhclient" pid=971 comm="apparmor_parser"
[    6.296510] type=1400 audit(1313931335.639:7): apparmor="STATUS"
operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=677 comm="apparmor_parser"
[    6.296538] type=1400 audit(1313931335.639:8): apparmor="STATUS"
operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=971 comm="apparmor_parser"
[    6.296752] type=1400 audit(1313931335.639:9): apparmor="STATUS"
operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script"
pid=677 comm="apparmor_parser"
[    6.296786] type=1400 audit(1313931335.639:10): apparmor="STATUS"
operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script"
pid=971 comm="apparmor_parser"
[    7.252581] vesafb: framebuffer at 0xe7000000, mapped to 0xfbc80000, using
1216k, total 1216k
[    7.252586] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    7.252589] vesafb: scrolling: redraw
[    7.252592] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    7.252740] Console: switching to colour frame buffer device 80x30
[    7.256443] fb0: VESA VGA frame buffer device
[    7.256921] EXT3-fs (sda2): using internal journal
[    7.632832] EXT3-fs: barriers not enabled
[    7.633111] kjournald starting.  Commit interval 5 seconds
[    7.633717] EXT3-fs (sda5): using internal journal
[    7.633723] EXT3-fs (sda5): mounted filesystem with ordered data mode
[    8.085918] ppdev: user-space parallel port driver
[    8.179049] type=1400 audit(1313931337.519:11): apparmor="STATUS"
operation="profile_replace" name="/sbin/dhclient" pid=1173
comm="apparmor_parser"
[   13.628308] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.630936] forcedeth 0000:00:0a.0: irq 41 for MSI/MSI-X
[   13.631134] forcedeth 0000:00:0a.0: eth0: no link during initialization
[   13.631804] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.010414] hda-intel: IRQ timing workaround is activated for card #1.
Suggest a bigger bdl_pos_adj.
[  215.210681] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[  695.307803] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0


```

I have also run sudo rfkill unblock all, with no joy. Annoyingly, the card connects just fine using a Live CD. 

Has anybody got any ideas? I'm stumped. And I cannot get a wired connexion either without some pretty major furniture moving. So anything I need to install, I have to download on my wife's Windows laptop and transfer by USB. 

This feels like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040) but the workaround there does not apply to my situation.


Thanks, 


macdo

---

### Post by praseodym on 2011-08-21
Are there options in your BIOS to activate your wireless?

Is there an option to reset the BIOS?

---

### Post by macdo on 2011-08-21
Nope. I checked that first ;-)
bios reset didn't help either.

Thanks

macdo

---

### Post by praseodym on 2011-08-21
What computer do you use?

---

### Post by macdo on 2011-08-21
What do you mean? It's a desktop with an athlon processor. I can't remember what the motherboad and graphics card are. Does that change anything?

---

### Post by praseodym on 2011-08-21
Ok, with a notebook there could have been a different module. Please show

```
lspci -nnk | grep -iA2 net
iwconfig
```

---

### Post by macdo on 2011-08-21
Sorry, I had to go out.

```
macdo@McMachine:~$ lspci -nnk |grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device [1043:82e2]
        Kernel driver in use: forcedeth
--
01:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185]
        Kernel driver in use: rtl8180

```
And 
```

macdo@McMachine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
macdo@McMachine:~$ 
```

macdo

---

### Post by praseodym on 2011-08-21
The card is "on":

> ```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="Red"]20 dBm[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

There is something else wrong. Please show:

```
iwlist chan
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/udev/rules.d/70-persistent-net.rules
```
and name the network you want to connect to.

---

### Post by macdo on 2011-08-21
Cool. Thanks. I attach a screenshot of the network manager message.  
My network is "domandericaGB" (Cell 04 below).


```

macdo@McMachine:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
macdo@McMachine:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: DE:31:80:18:06:15
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/100  Signal level=60/100  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000140f78d0b27
                    Extra: Last beacon: 1052ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: DE:31:80:18:06:16
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/100  Signal level=58/100  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000140f78d103f
                    Extra: Last beacon: 1052ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: DE:31:80:18:06:17
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/100  Signal level=58/100  
                    Encryption key:on
                    ESSID:"freephonie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000140f78d1484
                    Extra: Last beacon: 1048ms ago
                    IE: Unknown: 000A6672656570686F6E6965
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:24:D4:5B:45:98
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/100  Signal level=66/100  
                    Encryption key:on
                    ESSID:"domandericaGB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000001757160
                    Extra: Last beacon: 172ms ago
                    IE: Unknown: 000C646F6D657465726963614652
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000052435D0072322E00
          Cell 05 - Address: DE:31:80:18:06:14
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/100  Signal level=60/100  
                    Encryption key:on
                    ESSID:"sandrine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000140f78d06e9
                    Extra: Last beacon: 1052ms ago
                    IE: Unknown: 000873616E6472696E65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
   
macdo@McMachine:~$ cat /var/lib/NetworkManager/NetworkManager.state 

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
macdo@McMachine:~$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:54:84:a8:7c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8185 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:d1:e3:52:84", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
macdo@McMachine:~$ ^C
macdo@McMachine:~$ 

```

---

### Post by praseodym on 2011-08-21
Maybe reinstalling the network-manager:

```
sudo apt-get install --reinstall network-manager plasma-widget-networkmanagement
```
After that, give yourself _all_ rights in "Users&Groups" and login again. Delete the connection in the NM and setup a new one.

---

### Post by macdo on 2011-08-21
I can't reinstall as I don't have internet.
```
Reinstallation of plasma-widget-networkmanagement is not possible, it cannot be downloaded.
Reinstallation of network-manager is not possible, it cannot be downloaded. 
```
Should I uninstall the installed version and reinstall from the CD? 

What do you mean by "all permissions"?

---

### Post by praseodym on 2011-08-21
Yes, first check if the needed packages are on CD. Uninstall it and reinstall the packages by double-clicking. You need at least all network-based permissions (best:all, **not** groups).

---

### Post by fdrake on 2011-08-21
can you post:

```

dmesg | grep iwl

```

---

### Post by macdo on 2011-08-22
@praseodym: I've done that, but with no success. 

@fdrake: there is no output. 

Thanks, 

macdo

---

### Post by praseodym on 2011-08-22
Ok,

is that Natty? In that case you can try to compile the Realtek-driver r8185b, Download [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true#352"):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) dkms build-essential
```
Unpack the driver into your /home directory, change the directory:

```
cd nameoffolder/
make
sudo make install
sudo depmod -a
echo "blacklist rtl8180" | sudo tee /etc/modprobe.d/blacklist-rtl8180.conf
```
Reboot. Check:
```
lsmod
lspci -nnk | grep -iA2 net
iwconfig
sudo iwlist scan
dmesg | grep r8
```

If you are using Lucid or Maverick you can update the driver rtl8180 via the "backport-modules":

```
sudo apt-get install --reinstall linux-backports-modules-wireless-$(uname -r)
```
and reboot. Check:
The first 4 commands plus
```
dmesg | grep rtl
modinfo rtl8180
```

You may first check:

```
modinfo rtl8180
```
and save the output for comparison, if you try the backport-modules.

---

### Post by macdo on 2011-08-22
I can't do that without internet, can I?

But I have tried to use a USB wireless adapter (Netgear wn111v2 with an Atheros chip) and that has given me the exact same errors. I don't know if that helps... 


macdo

---

### Post by praseodym on 2011-08-22
Ok, you are using Natty with -PAE-Kernel. There are no Backport-Modules for this kernel yet.

Direct links to the kernel header files:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11-generic-pae_2.6.38-11.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11-generic-pae_2.6.38-11.48_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11_2.6.38-11.48_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11_2.6.38-11.48_all.deb)

and dkms

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb)

Save the packages on your desktop and install them via:

```
sudo dpkg -i ~/Desktop/*.deb
```

The package **build-essential** can be installed from CD/DVD.

---

### Post by macdo on 2011-08-27
I'm sorry that I didn't get back to you, but I do have a valid excuse: my daughter decided to be born :-D

I have "solved" the problem by reinstalling 10.04 LTS and that works. I'm afraid that at the moment I have no time to dedicate to trying to understand why it doesn't work with 11.04. But thank you for your kind and knowledgeable help which I sincerely appreciate.

macdo

---

### Post by praseodym on 2011-08-27
> **macdo said:**
> I'm sorry that I didn't get back to you, but I do have a valid excuse: my daughter decided to be born :-D


:popcorn: :guitar: =D>

sadly no :beer:-moticon ;-)

Congratulations to you and your wife/gf

---

### Post by sasukeskapa on 2012-12-30
For me this method worked for nearly the same problem:

Solution to ‘Wireless disabled by Hardware switch’
Posted July 12, 2011 by Sunil kumar in Uncategorized.	 10 Comments
Ohhh … Suddenly my wifi goes off( a combination of DELL with Ubuntu natty) and got a display – wireless disabled by hardware switch. Got down to googling and finally got this.
To get back your wifi to start working, type in the following:
$:  sudo rfkill list
You will get back something like this.
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
As you could see (0,2) the Wireless Lan has been soft blocked.  We need to unblock it to get it up and working properly.
$: sudo rfkill unblock 0
$: sudo rfkill unblock 2
 
Restart your networking
$: sudo /etc/init.d/networking restart
 
and yup! the wifi should be back now.

Found here:
[http://sunilkumarn.wordpress.com/2011/07/12/solution-to-wireless-disabled-by-hardware-switch/](http://sunilkumarn.wordpress.com/2011/07/12/solution-to-wireless-disabled-by-hardware-switch/)

---

