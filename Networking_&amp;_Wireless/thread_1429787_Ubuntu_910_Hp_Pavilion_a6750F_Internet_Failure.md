---
title: "Ubuntu 910 Hp Pavilion a6750F Internet Failure"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by jgiesler on 2010-03-14
Hey everyone. I just installed that latest version of Ubuntu on to my HP *a6750f Pavilion PC. I am using my wireless card on it. When i use the internet sometimes it will work for awhile but then it won't. So my internet keeps cutting in and out. I am not being diconnected from my router though. Internet is working prefectly fine on my other computers running windows seven and ubuntu.

Here is my information

------------lspci code returned

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
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
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:00.0 Multimedia controller: Philips Semiconductors Device 7160 (rev 03)


-----------lsusb code returned

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 005: ID 0a5c:2148 Broadcom Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15a9:0004  
Bus 002 Device 002: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 03f0:2a12 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

----------ifconfig returned

eth0      Link encap:Ethernet  HWaddr 00:24:21:23:7a:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:474323 (474.3 KB)  TX bytes:474323 (474.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:76:82:39  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe76:8239/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58028002 (58.0 MB)  TX bytes:14350399 (14.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-76-82-39-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-----------iwconfig returned

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"GHOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:4D:7F:42:AA   
          Bit Rate=54 Mb/s   Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


----------lsmod returned


Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
arc4                    2144  2 
snd_hda_codec_realtek   277860  1 
ecb                     3296  2 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
rt73usb                29092  0 
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
crc_itu_t               2336  1 rt73usb
rt2x00usb              13600  1 rt73usb
rt2x00lib              34624  2 rt73usb,rt2x00usb
snd_mixer_oss          18976  1 snd_pcm_oss
usblp                  15136  0 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
led_class               5256  1 rt2x00lib
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
input_polldev           4720  1 rt2x00lib
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
mac80211              210040  2 rt2x00usb,rt2x00lib
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2234552  32 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              109144  2 rt2x00lib,mac80211
soundcore               9088  1 snd
iptable_filter          3872  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
ip_tables              21200  1 iptable_filter
psmouse                57124  0 
lp                     11908  0 
x_tables               25832  1 ip_tables
shpchp                 37756  0 
parport                40528  2 ppdev,lp
serio_raw               6596  0 
joydev                 13088  0 
btusb                  14260  4 
i2c_piix4              11728  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
hid_microsoft           4292  0 
usbhid                 43968  0 
usb_storage            66304  1 
r8169                  38884  0 
mii                     6368  1 r8169
ohci1394               33780  0 
ieee1394              100896  1 ohci1394



-------sudo lshw -C network


 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:23:7a:91
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:ee00(size=256) memory:fdeff000-fdefffff memory:fddf0000-fddfffff(prefetchable) memory:fdd00000-fdd1ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:76:82:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11bg




------------iwlist scan



lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:7F:42:AA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"GHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f55fb3845
                    Extra: Last beacon: 53460ms ago
                    IE: Unknown: 000547484F4D45
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001FFF7F
                    IE: Unknown: DD1A00037F030100000000184D7F42AA02184D7F42AA64002C011F08

pan0      Interface doesn't support scanning.


-----------sudo /etc/init.d/networking restart


 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.







I hope this infromation is helpful.

Any help would be grateful.

---

### Post by jgiesler on 2010-03-14
Does anyone had this problem before at all?

---

