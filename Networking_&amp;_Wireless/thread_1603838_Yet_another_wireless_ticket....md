---
title: "Yet another wireless ticket..."
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by Bludkill on 2010-10-23
Howdy linux gurus!

I made the switch! I've been encouraging others to do so, also, and.just got my girlfriend to install Linux Mint 9 (based off Ubuntu 10.04) on her new netbook. Unfortunately, I'm having some trouble getting the wireless to work. That is, the wireless was working for a while, but recently stopped and I can't figure out why (or how to fix it). Ethernet cables still work fine. In any case, as per the "How to post a wirelss issue" thread at [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681), here are the details about the computer:

[B]
1) Machine Brand and Model (PC/Laptop)[/B]:

Dell m101z 12" netbook

**2 ) Wireless Brand, Model and Wireless Chipset:**
          
[I]$ lspci
[/I] 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Dell Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

[I]$ lsusb
[/I] Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 174f:1410 Syntek 
Bus 002 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 [B]3 ) Check interface:

[/B]          [I]$ ifconfig
[/I]eth5      Link encap:Ethernet  HWaddr 00:26:b9:dd:a2:3c  
          inet addr:192.168.1.53  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fedd:a23c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1871 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2030811 (2.0 MB)  TX bytes:316214 (316.2 KB)
          Interrupt:27 

eth6      Link encap:Ethernet  HWaddr f0:7b:cb:5a:74:64  
          inet6 addr: fe80::f27b:cbff:fe5a:7464/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

[I]$ iwconfig
[/I] lo        no wireless extensions.

eth6      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth5      no wireless extensions.

vboxnet0  no wireless extensions.

**4 ) Check for modules:**

[I]$ lmsmod
[/I]Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6326  0 
vboxnetflt             15280  0 
vboxdrv               190626  2 vboxnetadp,vboxnetflt
joydev                  8708  0 
dm_crypt               11331  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203374  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7596  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57054  0 
fglrx                2092908  32 
dell_wmi                1793  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5422  0 
atl1c                  28083  0 
agpgart                31724  1 fglrx
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
psmouse                63245  0 
serio_raw               3978  0 
shpchp                 28820  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
lp                      7060  0 
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
usb_storage            39553  0 
video                  17375  0 
output                  1871  1 video
vga16fb                11385  1 
vgastate                8961  1 vga16fb
ahci                   32200  2 

[B]5 ) Kernel boot messages

[/B](really long - is there something specific or should I post it all?)

**6 ) Network configuration**     

[I]$ sudo lshw -C network
[/I]  *-network               
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth5
       version: c0
       serial: 00:26:b9:dd:a2:3c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=192.168.1.53 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:d0200000-d023ffff ioport:a000(size=128 )
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth6
       version: 01
       serial: f0:7b:cb:5a:74:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0300000-d0303fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

[B]7 ) Scan for networks:
[/B][FONT=monospace]
[/FONT]*$ iwlist scan*
lo        Interface doesn't support scanning.

eth6      Interface doesn't support scanning.

eth5      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.
**8 ) Ubuntu Version: **
     
[I]$ lsb_release -d
[/I]Description:    Linux Mint 9 Isadora

[B]9 ) Kernel/architecture (including 32 vs. 64 bit):

[/B]*$ uname -mr*
2.6.32-25-generic i686

[B]10 ) Restarting the network:
[/B]
(when plugged in: )

[I]$ sudo /etc/init.d/networking restart
[/I]* Reconfiguring network interfaces...
Ignoring unknown interface eth5=eth5.
                                                                         [ OK ]

(When not plugged in: )
[I]
$ sudo /etc/init.d/networking restart
[/I]* Reconfiguring network interfaces...                                   [ OK ] 

(has no effect)



Other than that, I've tried reinstalling network-manager and network-manager-gnome. I've also removed the dell-laptop mod ("sudo rmmod -f dell-laptop") and added it to the bottom of blacklist.conf. If there's anything else I can do to make your job easier, please let me know. Thanks again for the help - if I can get this working quickly, I should have a much better chance of convincing my girlfriend to stick with linux!

Cheers!

---

### Post by Bludkill on 2010-10-25
(Shameless self-bump...)

Is there anything I can do to help or clarify the question? I tried to include everything the first time around, which might've scared people away due to its length.  But I'd still be grateful if anyone could give me a hand!

Thanks again, eh?

---

### Post by jdkchem on 2010-11-17
There is/should be a additional/restricted drivers "app" in the system menu.  Just install the Broadcomm STA and you should be good.  You will have to hook-up to the internet through the ethernet port.

---

