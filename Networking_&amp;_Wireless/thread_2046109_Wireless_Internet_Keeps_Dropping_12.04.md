---
title: "Wireless Internet Keeps Dropping 12.04"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by RKyle on 2012-08-22
Hi, I've had this problem on Ubuntu and kUbuntu with multiple devices but every so often at random times the wireless internet on my devices disconnects and prompts me for my WPA2 passcode then waits about 30 seconds and prompts me again. This only started happening with the last three releases I believe but would really like to get this fixed. I tried to include as much information as possible, just let me know if anymoreinformation is needed to determine the problem. Any help is appreciated, thanks in advance.

lspci
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4250]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
02:00.1 IDE interface: VIA Technologies, Inc. VT6415 PATA IDE Host Controller (rev a0)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```
sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 10
       serial: 00:08:54:a2:c0:fd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:d800(size=256) memory:febf8000-febfbfff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:61:b2:e6
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:52 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff

```
rfkill list
```

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```
iwconfig
```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"essid"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: E0:91:F5:AB:69:1E   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

eth0      no wireless extensions.

```
lsmod
```

Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18139  2 
rfcomm                 46621  0 
bluetooth             185573  10 bnep,rfcomm
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
psmouse                87692  0 
snd_usb_audio         122982  1 
rtl8192se              93800  0 
rtlwifi               105727  1 rtl8192se
joydev                 17693  0 
mac80211              514621  2 rtl8192se,rtlwifi
k10temp                13166  0 
edac_core              53746  0 
snd_usbmidi_lib        25395  1 snd_usb_audio
edac_mce_amd           23709  0 
serio_raw              13211  0 
fam15h_power           13115  0 
uvcvideo               72627  0 
cfg80211              209821  2 rtlwifi,mac80211
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
fglrx                3263886  53 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110           18078  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
shpchp                 37277  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
uas                    18180  0 
usb_storage            49198  0 
r8169                  62099  0 
pata_atiixp            13204  3 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
pata_via               13701  0 
crc_itu_t              12707  1 firewire_core
wmi                    19256  0 

```
iwlist scan
```

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E0:91:F5:AB:69:1E
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"essid"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a90fad80
                    Extra: Last beacon: 84812ms ago
                    IE: Unknown: 000C6C697A73206E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B0001031047001000000000000010000000E091F5AB691E102100074E65746765617210230008574E445233373030102400025631104200046E6F6E651054000800060050F204000110110008574E445233373030100800020086103C000103

eth0      Interface doesn't support scanning.

```

---

### Post by Kirk Schnable on 2012-08-22
Whenever I see networking act up like this, it's not been a driver issue, but rather a network manager issue.

I'd try deleting your network from network manager, and recreating it from scratch.

Right click network manager icon > Edit Connections
Delete everything related to your home WiFi connection from the Wireless tab.
Use network manager to connect to the WiFi fresh. Enter your network authentication key.

Then see if the problem reoccurs.

Kirk

---

### Post by RKyle on 2012-08-26
That didn't work, I still have to restart my computer to get wireless to work. My wireless card does have Linux drivers but they require an older kernel and development for the drivers has ceased. I tried using ndiswrapper but that also failed. I just don't understand why it connects for awhile, then drops. Even ifconfig wlan0 up/down does nothing.

---

### Post by Kirk Schnable on 2012-08-27
> **RKyle said:**
> That didn't work, I still have to restart my computer to get wireless to work. My wireless card does have Linux drivers but they require an older kernel and development for the drivers has ceased. I tried using ndiswrapper but that also failed. I just don't understand why it connects for awhile, then drops. Even ifconfig wlan0 up/down does nothing.

Can you give me an output of:
```
sudo iwconfig
```

After your network connection has dropped?

This seems like a similar issue I'm helping someone else with at the moment, and I'd like to see if there's any retransmitted packets.

Kirk

---

### Post by wnhtr2011 on 2012-08-28
I am having the exact same problem.  This has been happening for the past few releases and is getting VERRY ANNOYING.

Here is a syslog messages when the disconnect happens (usually during a file download):

Aug 28 16:21:49 Kubuntu-Laptop kernel: [113524.548057] ieee80211 phy0: wlan0: No probe response from AP f4:ec:38:dd:ad:6c after 500ms, disconnecting.
Aug 28 16:21:49 Kubuntu-Laptop kernel: [113524.559861] cfg80211: All devices are disconnected, going to restore regulatory settings
Aug 28 16:21:49 Kubuntu-Laptop kernel: [113524.559873] cfg80211: Restoring regulatory settings
Aug 28 16:21:49 Kubuntu-Laptop kernel: [113524.559882] cfg80211: Calling CRDA to update world regulatory domain
Aug 28 16:21:50 Kubuntu-Laptop wpa_supplicant[2792]: CTRL-EVENT-DISCONNECTED bssid=f4:ec:38:dd:ad:6c reason=4
Aug 28 16:21:50 Kubuntu-Laptop NetworkManager[2762]: <info> (wlan0): supplicant interface state: completed -> scanning
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826708] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826712] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826715] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826718] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826721] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826724] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826726] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826729] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826731] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826734] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826736] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826739] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826742] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826745] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826747] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826750] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826752] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826755] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826757] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826760] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826763] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826765] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826768] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826770] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826773] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826776] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826778] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826781] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826784] cfg80211: World regulatory domain updated:
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826786] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826789] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826791] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826794] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826797] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:50 Kubuntu-Laptop kernel: [113524.826799] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 28 16:21:51 Kubuntu-Laptop wpa_supplicant[2792]: Trying to authenticate with f4:ec:38:dd:ad:6c (SSID='TP-LINK_Home' freq=2462 MHz)
Aug 28 16:21:51 Kubuntu-Laptop NetworkManager[2762]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 28 16:21:51 Kubuntu-Laptop kernel: [113526.036570] wlan0: authenticate with f4:ec:38:dd:ad:6c (try 1)
Aug 28 16:21:51 Kubuntu-Laptop kernel: [113526.236069] wlan0: authenticate with f4:ec:38:dd:ad:6c (try 2)
Aug 28 16:21:51 Kubuntu-Laptop kernel: [113526.436142] wlan0: authenticate with f4:ec:38:dd:ad:6c (try 3)
Aug 28 16:21:52 Kubuntu-Laptop kernel: [113526.636117] wlan0: authentication with f4:ec:38:dd:ad:6c timed out
Aug 28 16:21:54 Kubuntu-Laptop NetworkManager[2762]: <info> (wlan0): roamed from BSSID F4:EC:38:DD:AD:6C (TP-LINK_Home) to (none) ((none))
Aug 28 16:22:23 Kubuntu-Laptop NetworkManager[2762]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 28 16:22:26 Kubuntu-Laptop NetworkManager[2762]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 28 16:22:26 Kubuntu-Laptop NetworkManager[2762]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.

sudo iwconfig
gre0      no wireless extensions.

lo        no wireless extensions.

ham0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TP-LINK_Home"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: F4:EC:38:DD:AD:6C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-15 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:427   Missed beacon:0

eth0      no wireless extensions.

To recover from this state, in Network Manager, just uncheck "Enable Wireless", and then check it to re-enable.  After this, then the connection will start working again for a while.

---

### Post by OneLongPee on 2012-10-28
I have the same problem with dropping the broadband connection using kubuntu12.04 and the interfaces widget

Bus 002 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem


Recently a second problem is added the Enable Mobile Broadband checkbox cannot be set. Only thing to do is to restart the computer.

I wonder if there is a terminal code to set the whole shooting match
enable networking > enable mobile broadband > connection name > number > APN

---

### Post by CorleyKinnane on 2013-04-11
I just had to tell me router to only use "20MHz", not "Auto 20/40 Mhz."

My rtl8192cu wireless no longer de-authenticates itself.

---

