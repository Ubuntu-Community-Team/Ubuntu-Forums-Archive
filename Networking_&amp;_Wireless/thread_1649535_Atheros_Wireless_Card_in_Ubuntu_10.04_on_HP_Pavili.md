---
title: "Atheros Wireless Card in Ubuntu 10.04 on HP Pavilion dv7 laptop: &quot;Device Not Ready&quot;"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by Silverevilchao on 2010-12-20
Ever since I got the laptop nearly two years ago, I would periodically have problems with the wireless; namely, I would wake the computer up after sleep mode sometimes and for some reason not have any networks listed, and this would oddly be fixed by shutting down the computer (restarting it wouldn't work) and turning it back on again. This persisted through Windows Vista (the original OS this computer came with), Windows 7, and finally Ubuntu Linux 10.04, where it says "device not ready" instead of acting like all wireless networks in the area spontaneously disappeared. It is really annoying, and I want to see what I can do about it instead of buying a new card entirely.

Here's the basic info, per the sticky on posting topics about wireless problems:

**1.) Machine Brand and Model**: HP Pavilion dv7. Laptop. Huge monster with a 17-inch screen (really hard to find laptop cases for).

**2.) Wireless Brand, Model, and Wireless Chipset:**
```

eien@Angel:~$ sudo lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

```

eien@Angel:~$ sudo lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 106c:240a Curitel Communications, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 090c:c371 Feiya Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**3.) Interface:**
```

eien@Angel:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:f5:51:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3408 (3.4 KB)  TX bytes:3408 (3.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:2b:3b:4a  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe2b:3b4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6975 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7131348 (7.1 MB)  TX bytes:1216160 (1.2 MB)

```

```

eien@Angel:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"BigDog"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:0E:1B:84   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:48B8-CF6B-5AB9-194D-3E79-144C-C7
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**4.) Modules:**
```

eien@Angel:~$ sudo lsmod
Module                  Size  Used by
aes_i586                7268  414 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
arc4                    1153  2 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_idt      51978  1 
snd_hda_intel          22005  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
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
ath5k                 121632  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57054  0 
cdc_acm                14658  0 
jmb38x_ms               7311  0 
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
joydev                  8708  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2092908  32 
agpgart                31724  1 fglrx
psmouse                63245  0 
serio_raw               3978  0 
memstick                8237  1 jmb38x_ms
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
cfg80211              126528  3 ath5k,mac80211,ath
i2c_piix4               8335  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
shpchp                 28820  0 
hp_accel               11144  0 
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  3 ath5k,sdhci,hp_accel
lirc_ene0100            6536  0 
lirc_dev                8884  1 lirc_ene0100
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
r8169                  34108  0 
vga16fb                11385  1 
usbhid                 36110  0 
hid                    67032  1 usbhid
mii                     4381  1 r8169
vgastate                8961  1 vga16fb
ahci                   32200  1 
video                  17375  0 
pata_atiixp             3148  0 
output                  1871  1 video

```

**5.) Kernel Boot Messages:**
```

eien@Angel:~$ dmesg | grep wlan0
[   19.920147] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.670789] wlan0: deauthenticating from 00:14:bf:0e:1b:84 by local choice (reason=3)
[   50.676468] wlan0: direct probe to AP 00:14:bf:0e:1b:84 (try 1)
[   50.695172] wlan0: direct probe responded
[   50.695178] wlan0: authenticate with AP 00:14:bf:0e:1b:84 (try 1)
[   50.696896] wlan0: authenticated
[   50.696918] wlan0: associate with AP 00:14:bf:0e:1b:84 (try 1)
[   50.699058] wlan0: RX AssocResp from 00:14:bf:0e:1b:84 (capab=0x411 status=0 aid=1)
[   50.699061] wlan0: associated
[   50.699769] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.580059] wlan0: no IPv6 routers present

```

**6.) Network Configuration:**
```

*-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:2b:3b:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.105 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:f5:51:cb
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)

```

This is what it looked like this morning when I was told that the device wasn't ready:
```

*-generic DISABLED      
       description: Wireless interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: ff
       serial: 00:23:4d:2b:3b:4a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=255 maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:f5:51:cb
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)

```

**7.) Scan for Networks:**
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:0E:1B:84
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"BigDog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cda25a37e
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0006426967446F67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020204

```

**8.) Ubuntu Version:**
```

Description:	Ubuntu 10.04.1 LTS

```

**9.) Kernel/Architecture:**
```

2.6.32-26-generic i686

```

**10.) Restarting the Network:**
```

eien@Angel:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```

---

