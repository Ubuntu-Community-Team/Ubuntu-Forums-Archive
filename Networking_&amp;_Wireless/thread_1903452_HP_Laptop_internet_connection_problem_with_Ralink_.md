---
title: "HP Laptop internet connection problem with Ralink RT5390... Connects occasionally."
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by Expert Novice on 2012-01-02
Hi there,  
 

 I installed Ubuntu alongside my existing Windows 7 installation on my HP Pavilion g6 1180sa laptop. It has an Intel core i5 2410 2.3ghz processor with New Mobile Intel HM65 Express chipset. The istallation seemed to go ok but I am immediately experiencing difficulty connecting to the internet, most of the time that is. I boot the machine and it attempts to connect automatically but I am given repeated notifications saying ''Wireless network disconnected. You are currently offline''. This notification appears several times and then stops but the machine is still not connected and I'm unable to download anything.
 

 Clicking on the wireless icon at top right of screen shows my wireless network is available and also that wireless is enabled. If I click on the available network I get the same result, but only one notification. The machine has been able to connect a couple of times, once yesterday, the day after I installed the o/s and once earlier today. Both times after shutting down and rebooting the machine was once more unable to connect. The laptop connects to the wireless network perfectly from Windows as does my other Windows based machine (Dell desktop). I am able to connect the laptop in Unbuntu easily with my mobile phone but that's not really a long term solution so I'd love to get this issue sorted as soon as possible.
 

 I took the time to read and follow the instrctions posted in [this thread]("http://ubuntuforums.org/showthread.php?p=6183681") which has made my post here rather long so I hope the information I've put in is relavent. I can post up any more information as required but bear in mind I'm a total newbie where Ubuntu is concerned (I have just installed it two days ago, more or less got the hang of the terminal window and that's about it) so please bear with me :-)
 

 Any help with this will be most appreciated.
 

 Below are the outputs given from the various commands in the instruction thread I mentioned above.
 

 Here goes...
 

 Lspci gives...
 

 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)  
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)  
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)  
 00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)  
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)  
 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)  
 00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)  
 00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)  
 00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)  
 00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)  
 00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)  
 00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)  
 01:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe  
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)  
 03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)  
 

 

 lsusb gives...
 

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 002 Device 003: ID 058f:a001 Alcor Micro Corp.  
 Bus 001 Device 003: ID 0421:0070 Nokia Mobile Phones N95 (PC Suite mode)  
 

 

 lspci -nn | grep 'Ralink' gives...
  01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]  
 

 

 Ifconfig gives …
 

 eth0      Link encap:Ethernet  HWaddr 2c:27:d7:e6:c5:91   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:40 Base address:0xe000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:960 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:960 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:78656 (78.6 KB)  TX bytes:78656 (78.6 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr cc:af:78:14:4d:9a   
           inet6 addr: fe80::ceaf:78ff:fe14:4d9a/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:100 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:109 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:33336 (33.3 KB)  TX bytes:25089 (25.0 KB)  
 

 
iwconfig gives...
 

 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
            
 usbpn0    no wireless extensions.  
 

 
iwconfig wlan0 gives... 

 wlan0     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
 

 

 lsmod gives...

  Module                  Size  Used by  
 ppp_deflate            12878  0  
 zlib_deflate           26622  1 ppp_deflate  
 bsd_comp               12842  0  
 ppp_async              17307  0  
 rndis_wlan             28472  0  
 rndis_host             13560  1 rndis_wlan  
 cdc_ether              13312  1 rndis_host  
 cdc_acm                22305  2  
 usbnet                 25214  3 rndis_wlan,rndis_host,cdc_ether  
 cdc_phonet             12853  0  
 phonet                 29356  1 cdc_phonet  
 bnep                   17923  2  
 rfcomm                 38408  0  
 bluetooth             148839  10 bnep,rfcomm  
 parport_pc             32114  0  
 ppdev                  12849  0  
 binfmt_misc            17292  1  
 joydev                 17393  0  
 snd_hda_codec_hdmi     31426  1  
 snd_hda_codec_idt      60049  1  
 iptable_nat            13016  0  
 nf_nat                 24958  1 iptable_nat  
 nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat  
 nf_conntrack           70103  3 iptable_nat,nf_nat,nf_conntrack_ipv4  
 nf_defrag_ipv4         12649  1 nf_conntrack_ipv4  
 iptable_mangle         12646  0  
 hp_wmi                 13652  0  
 sparse_keymap          13658  1 hp_wmi  
 iptable_filter         12706  0  
 ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter  
 x_tables               21975  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables  
 uvcvideo               67271  0  
 videodev               85626  1 uvcvideo  
 snd_hda_intel          24262  2  
 snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep              13276  1 snd_hda_codec  
 snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec  
 arc4                   12473  2  
 snd_seq_midi           13132  0  
 rt2800pci              18340  0  
 snd_rawmidi            25241  1 snd_seq_midi  
 rt2800lib              48909  1 rt2800pci  
 crc_ccitt              12595  2 ppp_async,rt2800lib  
 rt2x00pci              14202  1 rt2800pci  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 psmouse                73673  0  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event  
 serio_raw              12990  0  
 rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci  
 mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib  
 rts_pstor             353227  0  
 i915                  505159  3  
 wmi                    18744  1 hp_wmi  
 snd_timer              28932  2 snd_pcm,snd_seq  
 cfg80211              172392  3 rndis_wlan,rt2x00lib,mac80211  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq  
 eeprom_93cx6           12653  1 rt2800pci  
 drm_kms_helper         32889  1 i915  
 snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm                   192194  4 i915,drm_kms_helper  
 mei                    36466  0  
 soundcore              12600  1 snd  
 snd_page_alloc         14115  2 snd_hda_intel,snd_pcm  
 i2c_algo_bit           13199  1 i915  
 video                  18908  1 i915  
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp  
 ahci                   21634  1  
 libahci                25727  1 ahci  
 r8169                  43104  0  
 

 
lsmod | grep "wlan0" gives...
 

 No output. Not sure if I'm using the right name here though.
 

 
Dmesg gives...
 

 [   14.151635] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151644] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151652] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151662] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151670] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151679] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151687] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151696] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151704] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151713] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151721] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151729] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151737] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151747] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151755] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151765] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151772] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151781] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151788] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151797] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151805] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151815] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151823] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151832] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.151840] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.151849] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)  
 [   14.177898] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'  
 [   14.179944] Registered led device: rt2800pci-phy0::radio  
 [   14.180023] Registered led device: rt2800pci-phy0::assoc  
 [   14.180089] Registered led device: rt2800pci-phy0::quality  
 [   14.250852] rts_pstor: waiting for device to settle before scanning  
 [   14.251358] Linux video capture interface: v2.00  
 [   14.293106] uvcvideo: Found UVC 1.00 device HP Webcam-101 (058f:a001)  
 [   14.326353] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input4 
 [   14.326548] usbcore: registered new interface driver uvcvideo  
 [   14.326557] USB Video Class driver (v1.1.0)  
 [   14.447118] fbcon: inteldrmfb (fb0) is primary device  
 [   14.447385] Console: switching to colour frame buffer device 170x48  
 [   14.447490] fb0: inteldrmfb frame buffer device  
 [   14.447496] drm: registered panic notifier  
 [   14.490645] acpi device:1f: registered as cooling_device4  
 [   14.491911] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5  
 [   14.492116] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)  
 [   14.492257] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0  
 [   14.492393] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22  
 [   14.492563] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X  
 [   14.492672] HDA Intel 0000:00:1b.0: setting latency timer to 64  
 [   14.584109] ip_tables: (C) 2000-2006 Netfilter Core Team  
 [   14.597405] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110413/dsopcode-236) 
 [   14.597431] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f3c2a948), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.597468] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f3c2ab58), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.598125] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110413/dsopcode-236) 
 [   14.598147] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f3c2a948), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.598178] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f3c2ab58), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.598532] input: HP WMI hotkeys as /devices/virtual/input/input6  
 [   14.599211] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110413/dsopcode-236) 
 [   14.599233] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f3c2a948), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.599267] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f3c2ab58), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.599432] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110413/dsopcode-236) 
 [   14.599450] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f3c2a948), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.599478] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f3c2ab58), AE_AML_BUFFER_LIMIT (20110413/psparse-536)  
 [   14.612190] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612204] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612213] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612223] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612232] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612242] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612250] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612260] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612268] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612277] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612285] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612295] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612303] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612312] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612320] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612329] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612337] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612346] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612354] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612363] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612371] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612380] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612387] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612396] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612404] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612412] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612419] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:  
 [   14.612428] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   14.612437] cfg80211: World regulatory domain updated:  
 [   14.612442] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   14.612451] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   14.612459] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   14.612467] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   14.612475] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   14.612483] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   14.626856] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)  
 [   14.981757] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400  
 [   15.035386] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7  
 [   15.065984] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0  
 [   15.066351] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8  
 [   15.066609] input: HDA Intel PCH Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9  
 [   15.066820] input: HDA Intel PCH HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10  
 [   15.249665] rts_pstor: device scan complete  
 [   15.249881] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS  
 [   15.249955] Bad LUN (0:1)  
 [   15.249989] scsi: killing requests for dead queue  
 [   15.261708] Bad target number (1:0)  
 [   15.261746] scsi: killing requests for dead queue  
 [   15.277699] Bad target number (2:0)  
 [   15.277736] scsi: killing requests for dead queue  
 [   15.293690] Bad target number (3:0)  
 [   15.293728] scsi: killing requests for dead queue  
 [   15.345656] Bad target number (4:0)  
 [   15.345694] scsi: killing requests for dead queue  
 [   15.377644] Bad target number (5:0)  
 [   15.377681] scsi: killing requests for dead queue  
 [   15.413628] Bad target number (6:0)  
 [   15.413668] scsi: killing requests for dead queue  
 [   15.449604] Bad target number (7:0)  
 [   15.449641] scsi: killing requests for dead queue  
 [   15.485969] sd 6:0:0:0: Attached scsi generic sg2 type 0  
 [   15.486989] sd 6:0:0:0: [sdb] Attached SCSI removable disk  
 [   16.743002] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k  
 [   16.797531] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro  
 [   17.037098] type=1400 audit(1325521612.028:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=935 comm="apparmor_parser"  
 [   17.039065] type=1400 audit(1325521612.028:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=935 comm="apparmor_parser"  
 [   17.039917] ppdev: user-space parallel port driver  
 [   17.040004] type=1400 audit(1325521612.028:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=935 comm="apparmor_parser"  
 [   17.044739] type=1400 audit(1325521612.036:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=934 comm="apparmor_parser"  
 [   17.061821] type=1400 audit(1325521612.052:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=936 comm="apparmor_parser"  
 [   17.071726] type=1400 audit(1325521612.060:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=946 comm="apparmor_parser"  
 [   17.073616] type=1400 audit(1325521612.064:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=946 comm="apparmor_parser"  
 [   17.423439] init: failsafe main process (875) killed by TERM signal  
 [   17.427088] init: apport pre-start process (1022) terminated with status 1  
 [   17.468502] init: apport post-stop process (1055) terminated with status 1  
 [   17.652577] Bluetooth: Core ver 2.16 
 [   17.652643] NET: Registered protocol family 31  
 [   17.652650] Bluetooth: HCI device and connection manager initialized  
 [   17.652657] Bluetooth: HCI socket layer initialized  
 [   17.652663] Bluetooth: L2CAP socket layer initialized  
 [   17.652846] Bluetooth: SCO socket layer initialized  
 [   17.659740] Bluetooth: RFCOMM TTY layer initialized  
 [   17.659754] Bluetooth: RFCOMM socket layer initialized  
 [   17.659761] Bluetooth: RFCOMM ver 1.11  
 [   17.661259] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   17.661268] Bluetooth: BNEP filters: protocol multicast  
 [   17.664958] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware  
 [   17.705606] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [   17.911086] r8169 0000:02:00.0: eth0: link down  
 [   17.911696] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   18.716405] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0  
 [   19.022100] init: plymouth-stop pre-start process (1337) terminated with status 1  
 [   20.725253] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0  
 [   20.963118] wlan0: authenticate with 00:24:17:94:74:19 (try 1)  
 [   20.964866] wlan0: authenticated  
 [   20.982790] wlan0: associate with 00:24:17:94:74:19 (try 1)  
 [   20.985014] wlan0: RX AssocResp from 00:24:17:94:74:19 (capab=0x411 status=0 aid=1)  
 [   20.985021] wlan0: associated  
 [   20.985442] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 [   31.429282] wlan0: no IPv6 routers present  
 [   41.372572] wlan0: deauthenticating from 00:24:17:94:74:19 by local choice (reason=3)  
 [   41.496410] cfg80211: All devices are disconnected, going to restore regulatory settings  
 [   41.496414] cfg80211: Restoring regulatory settings  
 [   41.496428] cfg80211: Calling CRDA to update world regulatory domain  
 [   41.499110] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499114] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499115] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499117] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499119] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499120] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499122] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499123] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499125] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499126] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499128] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499130] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499131] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499133] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499134] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499136] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499137] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499139] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499140] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499142] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499143] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499145] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499146] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499148] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499149] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499151] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499152] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:  
 [   41.499154] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   41.499156] cfg80211: World regulatory domain updated:  
 [   41.499158] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   41.499159] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   41.499161] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   41.499162] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   41.499164] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   41.499166] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   45.319109] wlan0: authenticate with 00:24:17:94:74:19 (try 1)  
 [   45.320909] wlan0: authenticated  
 [   45.321433] wlan0: associate with 00:24:17:94:74:19 (try 1)  
 [   45.323763] wlan0: RX ReassocResp from 00:24:17:94:74:19 (capab=0x411 status=0 aid=1)  
 [   45.323772] wlan0: associated  
 [   55.432974] wlan0: no IPv6 routers present  
 [   59.974788] usb 1-1.1: new full speed USB device number 3 using ehci_hcd  
 [   60.207270] NET: Registered protocol family 35  
 [   60.263566] usbcore: registered new interface driver cdc_phonet  
 [   60.305305] cdc_acm 1-1.1:1.10: ttyACM0: USB ACM device  
 [   60.306015] cdc_acm 1-1.1:1.12: ttyACM1: USB ACM device  
 [   60.306090] usbcore: registered new interface driver cdc_ether  
 [   60.306468] usbcore: registered new interface driver cdc_acm  
 [   60.306471] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters  
 [   60.317931] usbcore: registered new interface driver rndis_host  
 [   60.329943] usbcore: registered new interface driver rndis_wlan  
 [   65.350972] wlan0: deauthenticating from 00:24:17:94:74:19 by local choice (reason=3)  
 [   65.544041] cfg80211: All devices are disconnected, going to restore regulatory settings  
 [   65.544046] cfg80211: Restoring regulatory settings  
 [   65.544060] cfg80211: Calling CRDA to update world regulatory domain  
 [   65.546801] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546804] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546806] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546808] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546809] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546811] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546812] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546814] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546815] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546817] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546819] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546821] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546822] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546824] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546825] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546827] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546828] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546830] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546832] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546833] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546835] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546836] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546838] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546839] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546841] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546842] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546844] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:  
 [   65.546845] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   65.546848] cfg80211: World regulatory domain updated:  
 [   65.546849] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   65.546851] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   65.546852] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   65.546854] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   65.546856] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   65.546857] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   70.038410] wlan0: authenticate with 00:24:17:94:74:19 (try 1)  
 [   70.040219] wlan0: authenticated  
 [   70.040838] wlan0: associate with 00:24:17:94:74:19 (try 1)  
 [   70.043171] wlan0: RX ReassocResp from 00:24:17:94:74:19 (capab=0x411 status=0 aid=1)  
 [   70.043180] wlan0: associated  
 [   81.003851] wlan0: no IPv6 routers present  
 [   87.675968] PPP BSD Compression module registered  
 [   87.705901] PPP Deflate Compression module registered  
 [   91.101690] wlan0: deauthenticating from 00:24:17:94:74:19 by local choice (reason=3)  
 [   91.207028] cfg80211: All devices are disconnected, going to restore regulatory settings  
 [   91.207034] cfg80211: Restoring regulatory settings  
 [   91.207041] cfg80211: Calling CRDA to update world regulatory domain  
 [   91.210079] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210082] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210084] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210086] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210088] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210090] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210091] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210093] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210094] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210096] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210098] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210099] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210101] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210103] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210106] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210108] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210111] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210113] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210116] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210118] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210120] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210123] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210125] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210127] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210129] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210132] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210134] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:  
 [   91.210136] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [   91.210140] cfg80211: World regulatory domain updated:  
 [   91.210141] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   91.210144] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   91.210146] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   91.210149] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   91.210151] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   91.210153] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   95.309088] wlan0: authenticate with 00:24:17:94:74:19 (try 1)  
 [   95.310943] wlan0: authenticated  
 [   95.311542] wlan0: associate with 00:24:17:94:74:19 (try 1)  
 [   95.313874] wlan0: RX ReassocResp from 00:24:17:94:74:19 (capab=0x411 status=0 aid=1)  
 [   95.313883] wlan0: associated  
 [  105.631215] wlan0: no IPv6 routers present  
 [  115.327730] wlan0: deauthenticating from 00:24:17:94:74:19 by local choice (reason=3)  
 [  115.490759] cfg80211: All devices are disconnected, going to restore regulatory settings  
 [  115.490774] cfg80211: Restoring regulatory settings  
 [  115.490819] cfg80211: Calling CRDA to update world regulatory domain  
 [  115.500105] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500116] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500122] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500128] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500134] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500140] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500145] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500151] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500156] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500162] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500167] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500173] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500178] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500184] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500189] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500195] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500200] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500206] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500211] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500217] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500222] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500228] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500233] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500239] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500244] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500250] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500255] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:  
 [  115.500262] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)  
 [  115.500269] cfg80211: World regulatory domain updated:  
 [  115.500273] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [  115.500279] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [  115.500285] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [  115.500291] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [  115.500297] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [  115.500302] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [  163.455828] show_signal_msg: 21 callbacks suppressed  
 [  163.455834] gksu[2184]: segfault at 67617373 ip 00756bcf sp bfb036a0 error 4 in libgdk-x11-2.0.so.0.2400.6[6e7000+ab000]
 

 
sudo lshw -C network gives...
 

 [sudo] password for david:  
   *-network                
        description: Wireless interface  
        product: RT5390 Wireless 802.11n 1T/1R PCIe  
        vendor: Ralink corp.  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        logical name: wlan0  
        version: 00  
        serial: cc:af:78:14:4d:9a  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-14-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn  
        resources: irq:16 memory:c2500000-c250ffff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 05  
        serial: 2c:27:d7:e6:c5:91  
        size: 10Mbit/s  
        capacity: 100Mbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s  
        resources: irq:40 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
 

 
iwlist scan gives...
 

 

 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wlan0     No scan results  
 

 usbpn0    Interface doesn't support scanning.  
 

 

 iwlist scan wlan0 gives...
 

 iwlist: unknown command `wlan0' (check 'iwlist –help').  
 

 
lsb_release -d gives...  
 

 Description:    Ubuntu 11.10  
 

 
uname -mr gives...
 

 3.0.0-14-generic i686  
 

 
sudo /etc/init.d/networking restart gives...
 
Running /etc/init.d/networking restart     is deprecated because it may not enable again some interfaces     Reconfiguring network interfaces... 

 Thanks for reading through all that :-)

---

### Post by Expert Novice on 2012-01-02
Ok, I've been using windows to get online for a while this evening seeing as Ubuntu would still not connect. Was just about to go to bed but out of curiosity booted into Ubuntu again, walked away from the laptop for a minute or two and when I came back it had connected automatically.

I have not altered anything since earlier when it was refusing to connect.

Does anyone have any suggestions as to where I can look for a solution to my intermittent yet persistent connection difficulties please?

---

### Post by Expert Novice on 2012-01-03
Since my last post all I have done is shut down the machine and go to bed. I got up, booted windows and got online. I shut down and immediately rebooted into Ubuntu which is now once again refusing to connect, except through my phone. Is there a terminal command I can use to find out what has changed since last night?

Thanks

---

### Post by hardisty on 2012-01-03
sounds like the problem I had over here [http://ubuntuforums.org/showthread.php?t=1846928](http://ubuntuforums.org/showthread.php?t=1846928)

---

### Post by Expert Novice on 2012-01-03
Hello Hardisty, thanks for your reply.

I presume you were having similar issues. I have d/l the driver and will see about installing it when I have a little more time to play with. Do I just follow the instructions in post 58 of this thread [http://ubuntuforums.org/showthread.php?t=1779005&page=6](http://ubuntuforums.org/showthread.php?t=1779005&page=6)

Still learning  here but will see how I go.

Interestingly when I booted the laptop earlier it connected automatically again without any trouble. I'm wondering if your comments re the physical wireless button on your keyboard might be relevant to my issues. Will bear that in mind.

Thanks again :D

---

### Post by Expert Novice on 2012-01-08
Just as an update, my connection issues appear to have sorted themselves out after a re install. Sadly still no idea what the problem was.

---

