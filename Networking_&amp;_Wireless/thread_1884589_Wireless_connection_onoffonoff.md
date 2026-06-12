---
title: "Wireless connection on/off/on/off"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by keayz on 2011-11-21
I'm running Oneiric on a Sony Vaio NS11J as a dual boot with Windows 7 64-bit. Wireless connection is made for a few seconds after boot but then is disconnected, reconnected disconnected, etc. WPA Personal PSK security, Laptop is authorised to connect to router and does so fine under Windows. I've read and followed the instructions in the Sticky on Ndiswrapper but it is not installed on my machine. Likewise the Sticky on 'How to post a Wireless issue', and I have 7 pages of details - here they are:
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
04:00.0 Network controller: Intel Corporation WiFi Link 5100
05:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:18b3 Ricoh Co., Ltd Sony Vaio Integrated Webcam

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
05:03.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
05:03.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
05:03.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)

sudo lshw -C Network
[sudo] password for keayz: 
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:87:f2:54
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d2d20000-d2d23fff ioport:d000(size=256) memory:d2d00000-d2d1ffff
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:b7:b0:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:d0500000-d0501fff

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:87:f2:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:b7:b0:f8  
          inet6 addr: fe80::221:5dff:feb7:b0f8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6535 (6.5 KB)  TX bytes:62534 (62.5 KB)

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
uvcvideo               72711  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
videodev               93004  1 uvcvideo
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17083  1 videodev
snd_rawmidi            30547  1 snd_seq_midi
joydev                 17693  0 
iwlagn                314213  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  566711  3 
mac80211              310872  1 iwlagn
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
psmouse                73882  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
serio_raw              13166  0 
drm_kms_helper         42558  1 i915
sony_laptop            45393  0 
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  1 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
libahci                26861  1 ahci
sky2                   58674  0
sudo lshw -C network

[sudo] password for keayz: 
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:87:f2:54
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d2d20000-d2d23fff ioport:d000(size=256) memory:d2d00000-d2d1ffff
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:b7:b0:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:d0500000-d0501fff

iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:22:3F:55:E8:10
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"KANDANG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004787e7da616
                    Extra: Last beacon: 2948ms ago
                    IE: Unknown: 00074B414E44414E47
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16070D1600000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34070D1600000000000000000000000000000000000000
          Cell 02 - Address: 00:23:4E:95:F6:2F
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-QPZC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012fdbafe816
                    Extra: Last beacon: 6056ms ago
                    IE: Unknown: 000F4254486F6D65487562322D51505A43
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:26:44:ED:C8:61
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"O2wirelessEDC861"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a2b02b0f99
                    Extra: Last beacon: 5976ms ago
                    IE: Unknown: 00104F32776972656C657373454443383631
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: DD09001018020000050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000

lsb_release -d
Description:	Ubuntu 11.10

uname -mr
3.0.0-12-generic x86_64

sudo /etc/init.d/networking restart
Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
Reconfiguring network interfaces...

The only one I have left out is the output from dmesg, which runs to 21 pages.

Would appreciate some assistance, many thanks.
keayz

---

### Post by praseodym on 2011-11-21
Hi,

deactivate the N-mode of the driver (which is buggy):
```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
I recommend pure WPA2-AES encryption if possible.

---

### Post by keayz on 2011-11-22
Hi Praseodym
Thank you for your advice, which I followed and all went well until the last, when I received this message:

sudo modprobe -v iwlagn
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko lln_disable+1
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

This is the latter part of dmesg:
[  436.237144] wlan0: authenticate with 00:22:3f:55:e8:10 (try 1)
[  436.241905] wlan0: authenticated
[  436.248869] wlan0: associate with 00:22:3f:55:e8:10 (try 1)
[  436.253209] wlan0: RX ReassocResp from 00:22:3f:55:e8:10 (capab=0x411 status=0 aid=4)
[  436.253217] wlan0: associated
[  438.294568] iwlagn 0000:04:00.0: Aggregation not enabled for tid 0 because load = 3
[  447.312037] wlan0: no IPv6 routers present
[  457.223879] wlan0: deauthenticating from 00:22:3f:55:e8:10 by local choice (reason=3)
[  457.260994] cfg80211: All devices are disconnected, going to restore regulatory settings
[  457.261002] cfg80211: Restoring regulatory settings
[  457.261009] cfg80211: Calling CRDA to update world regulatory domain
[  457.267754] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  457.267761] cfg80211: World regulatory domain updated:
[  457.267765] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  457.267770] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  457.267775] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  457.267780] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  457.267785] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  457.267790] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  463.312939] wlan0: authenticate with 00:22:3f:55:e8:10 (try 1)
[  463.315100] wlan0: authenticated
[  463.316249] wlan0: associate with 00:22:3f:55:e8:10 (try 1)
[  463.320367] wlan0: RX ReassocResp from 00:22:3f:55:e8:10 (capab=0x411 status=0 aid=4)
[  463.320377] wlan0: associated
[  466.395301] iwlagn 0000:04:00.0: Aggregation not enabled for tid 0 because load = 3
[  475.312065] wlan0: no IPv6 routers present
[  481.402077] iwlagn 0000:04:00.0: Aggregation not enabled for tid 0 because load = 1
[  485.228046] wlan0: deauthenticating from 00:22:3f:55:e8:10 by local choice (reason=3)
[  485.264436] cfg80211: All devices are disconnected, going to restore regulatory settings
[  485.264449] cfg80211: Restoring regulatory settings
[  485.264459] cfg80211: Calling CRDA to update world regulatory domain
[  485.275170] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  485.275180] cfg80211: World regulatory domain updated:
[  485.275185] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  485.275193] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  485.275201] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  485.275208] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  485.275215] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  485.275222] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  491.288281] wlan0: authenticate with 00:22:3f:55:e8:10 (try 1)
[  491.291455] wlan0: authenticated
[  491.294838] wlan0: associate with 00:22:3f:55:e8:10 (try 1)
[  491.298939] wlan0: RX ReassocResp from 00:22:3f:55:e8:10 (capab=0x411 status=0 aid=4)
[  491.298948] wlan0: associated
[  495.338564] iwlagn 0000:04:00.0: Aggregation not enabled for tid 0 because load = 2
[  502.672047] wlan0: no IPv6 routers present
[  508.765455] iwlagn 0000:04:00.0: Aggregation not enabled for tid 0 because load = 0
[  513.228295] wlan0: deauthenticating from 00:22:3f:55:e8:10 by local choice (reason=3)
[  513.253053] cfg80211: All devices are disconnected, going to restore regulatory settings
[  513.253062] cfg80211: Restoring regulatory settings
[  513.253069] cfg80211: Calling CRDA to update world regulatory domain
[  513.259103] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  513.259112] cfg80211: World regulatory domain updated:
[  513.259115] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  513.259120] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  513.259126] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  513.259130] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  513.259140] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  513.259145] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  519.257906] wlan0: authenticate with 00:22:3f:55:e8:10 (try 1)
[  519.260165] wlan0: authenticated
[  519.261310] wlan0: associate with 00:22:3f:55:e8:10 (try 1)
[  519.265629] wlan0: RX ReassocResp from 00:22:3f:55:e8:10 (capab=0x411 status=0 aid=4)
[  519.265640] wlan0: associated
[  530.160057] wlan0: no IPv6 routers present
[  540.224721] wlan0: deauthenticating from 00:22:3f:55:e8:10 by local choice (reason=3)
[  540.261099] cfg80211: All devices are disconnected, going to restore regulatory settings
[  540.261133] cfg80211: Restoring regulatory settings
[  540.261143] cfg80211: Calling CRDA to update world regulatory domain
[  540.272964] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  540.272974] cfg80211: World regulatory domain updated:
[  540.272979] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  540.272987] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  540.272995] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  540.273002] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  540.273009] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  540.273016] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  541.870063] iwlagn 0000:04:00.0: PCI INT A disabled
[  563.001411] cfg80211: Calling CRDA to update world regulatory domain
[  563.025794] iwlagn: Unknown parameter `lln_disable+1'
[  563.032565] cfg80211: World regulatory domain updated:
[  563.032572] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  563.032578] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  563.032583] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  563.032588] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  563.032592] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  563.032597] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

I now seem to have no wireless connection at all.
Keaygz

---

### Post by praseodym on 2011-11-22
Typo:

> [ 563.025794] iwlagn: Unknown parameter `lln_disable+1'

not "llndisable+1" but "[COLOR="Red"]11[/COLOR]n[COLOR="Red"]_[/COLOR]disable[COLOR="Red"]=[/COLOR]1" in Red is eleven not double-L[COLOR="Red"][/COLOR]
Modify the file with
```
gksu gedit /etc/modprobe.d/iwlagn.conf
```

---

### Post by keayz on 2011-11-22
Hi
Many thanks, it seems to have worked partially as I now get connected for about 16-19 seconds before being disconnected, which is an improvement.
Can't seem to change to WPA2-AES encryption as the router does not have it as an option.
Do you need any further information?
Keayz

---

### Post by praseodym on 2011-11-22
I recommend using Wicd with Add-On (different encryption templates) instead of the NM with mixed encryption:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver.

---

### Post by keayz on 2011-11-22
Thank you, done, but now no network manager at all. How do I start wicd and select 'wlan0' and 'wext'?

The following is the output of some of the commands:

/wicd-1.6.x_addon0144$ sudo ./install_wicd_addon
prüfe Wicd 1.6.x Installation...
/etc/wicd/encryption/templates/active
prüfe Installation
find: ‘active.bak’: No such file or directory
Installiere Wicd AddOn ...
sichere Originaldateien...
Kopiere neue Templates...
Installation abgeschlossen


keayz@ubuntu:~/wicd-1.6.x_addon0144$ sudo service wicd restart
Restarting Network connection manager wicd                            [ OK ]


sudo apt-get remove --purge network-manager network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  network-manager* network-manager-gnome*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 3,731 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146419 files and directories currently installed.)
Removing network-manager-gnome ...
Purging configuration files for network-manager-gnome ...
Removing network-manager ...
network-manager stop/waiting
Purging configuration files for network-manager ...
dpkg: warning: while removing network-manager, directory '/etc/NetworkManager/system-connections' not empty so not removed.
dpkg: warning: while removing network-manager, directory '/var/lib/NetworkManager' not empty so not removed.
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

Many thanks again
Keayz

---

### Post by praseodym on 2011-11-22
gksu wicd?

---

### Post by keayz on 2011-11-22
Hi Praseodym, I tried that but still no wireless icon in the system tray and no connection. I then looked at 'Network' in 'System Settings' and got this message "The System network services are not compatible with this version."
Keayz

---

### Post by praseodym on 2011-11-22
32 or 64 bit system? You can download both NM packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and uninstall wicd.

---

### Post by keayz on 2011-11-23
Hi, forgive me for what may be a silly question, but do I uninstall wicd first then download NM (which I assume is network manager) afterwards or the other way round?

---

### Post by praseodym on 2011-11-23
If you downloaded the packaged to "Downloads":

```
sudo apt-get remove --purge wicd
sudo apt-get autoremove
sudo dpkg -i ~/Downloads/network*.deb
```

---

### Post by keayz on 2011-11-23
We're now back to square one, with intermittent wireless connection. Have I done something wrong?

---

### Post by praseodym on 2011-11-23
Try now to install Wicd and the Add-On again, but this time remove the checkbox(es) in the Networkmanager reading "available to all users" and "connect automatically" (if any) and login again after "sudo service network-manager stop". Try it again with Wicd.

---

### Post by keayz on 2011-11-25
Hi Praseodym
Thanks for your patience and continued support. I've tried to reinstall wicd as you said but this is the outcome:

wget [http://elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
--2011-11-25 11:01:23--  [http://elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
Resolving elektronenblitz63.de... 82.165.83.231
Connecting to elektronenblitz63.de|82.165.83.231|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4063 (4.0K) [application/x-tar]
Saving to: `wicd-1.6.x_addon0144.tar.gz.1'
100%[======================================>] 4,063       --.-K/s   in 0.03s   
2011-11-25 11:01:23 (115 KB/s) - `wicd-1.6.x_addon0144.tar.gz.1' saved [4063/4063]

keayz@ubuntu:~$ sudo apt-get install --reinstall wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-wicd wicd-daemon wicd-gtk
The following NEW packages will be installed
  python-wicd wicd wicd-daemon wicd-gtk
0 upgraded, 4 newly installed, 0 to remove and 83 not upgraded.
Need to get 0 B/413 kB of archives.
After this operation, 2,863 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package python-wicd.
(Reading database ... 157582 files and directories currently installed.)
Unpacking python-wicd (from .../python-wicd_1.7.0+ds1-6_all.deb) ...
Selecting previously deselected package wicd-daemon.
Unpacking wicd-daemon (from .../wicd-daemon_1.7.0+ds1-6_all.deb) ...
Selecting previously deselected package wicd-gtk.
Unpacking wicd-gtk (from .../wicd-gtk_1.7.0+ds1-6_all.deb) ...
Selecting previously deselected package wicd.
Unpacking wicd (from .../wicd_1.7.0+ds1-6_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Setting up python-wicd (1.7.0+ds1-6) ...
Setting up wicd-daemon (1.7.0+ds1-6) ...
 * Restarting Network connection manager wicd                            [fail] 
Setting up wicd-gtk (1.7.0+ds1-6) ...
Setting up wicd (1.7.0+ds1-6) ...
Processing triggers for python-support ...
keayz@ubuntu:~$ tar xvf wicd-i.6.x_addon0144.tar.gz
tar: wicd-i.6.x_addon0144.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

I don't know how to proceed.
Keayz

---

### Post by praseodym on 2011-11-25
Typo:

> keayz@ubuntu:~$ tar xvf wicd-i.6.x_addon0144.tar.gz

You mean:

```
tar xvf wicd-[COLOR="Red"]1[/COLOR].6.x_addon0144.tar.gz
```
its a one

---

### Post by keayz on 2011-11-25
Thank you, I hang my head...
I've reinstalled wicd as per your instructions but am now back to the message 'The system network services are not compatible with this version.'
I've done it all correctly, I think, what now?

---

### Post by keayz on 2011-11-27
Hi Praseodym, I've tried going through all your steps and got to 'sudo service wicd restart'. After that you said to 'choose wlan0 as interface and wext as driver' but I can't see how to do this. Also, if I check in 'Network' in 'System Settings' I get this message again "The System network services are not compatible with this version."
You said to download the 64 bit file and gave me the URL, but I'm not sure how to find the one I need.
Can you please help me again with these?

---

### Post by praseodym on 2011-11-27
> **keayz said:**
> Hi Praseodym, I've tried going through all your steps and got to 'sudo service wicd restart'. After that you said to 'choose wlan0 as interface and wext as driver' but I can't see how to do this. 

See picture.
> 
Also, if I check in 'Network' in 'System Settings' I get this message again "The System network services are not compatible with this version."
You said to download the 64 bit file and gave me the URL, but I'm not sure how to find the one I need.
Can you please help me again with these?

Files:

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.1.90-0ubuntu3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.1.90-0ubuntu3_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.1.90-0ubuntu6_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.1.90-0ubuntu6_amd64.deb)

---

### Post by larascal on 2011-11-27
I suffered a similar problem to you, where the wifi would connect and then disconnect and connect again on infinite loop. I just this minute went to edit network connect and disabled 'Require IPv6 addressing for this connection to complete'. Amazingly it worked. Happy days!

---

### Post by keayz on 2011-11-28
Hi Praseodym
Thanks you for the URLs, I've downloaded the files to the desktop but don't know how to install them from there. Can you advise me please.
Thanks larascal, I tried that some time ago but no joy here.
Keayz

---

### Post by praseodym on 2011-11-28
Install them by double clicking or via

```
sudo dpkg -i ~/Desktop/*.deb
```

---

### Post by keayz on 2011-11-28
Thank you Praseodym, it installed but kept on breaking off so I tried larascal's idea again and now the wireless remains connected. I have not been able to change the parameters as shown in your screenshot, however, how do I do that and is it now necessary?

---

### Post by keayz on 2011-11-29
Hi Praseodym
Thank you again for all your help and patience, I now have a fully functional wireless connection and am very happy.
Thank you too larascal for your suggestion which also helped.
keayz

---

