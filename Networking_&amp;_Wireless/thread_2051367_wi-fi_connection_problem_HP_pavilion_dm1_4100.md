---
title: "wi-fi connection problem HP pavilion dm1 4100"
date: 2012-09-01
forum: Networking &amp; Wireless
---

### Post by ravenkrane on 2012-09-01
Hi everyone! 

After numerous years on Mac, I've just bought a HP Pavilion dm 1 4175sa laptop. And since, the horror of Microsoft had made me go for Apple in the first place all those years ago, the (nearly) first thing I did after starting the computer for the first time was installing Ubuntu.
And from what I saw it's working fine. Except for the wireless connection.

At home we have a BE Box, and when in my room on my MacBook the wireless connection is quite spectacular (after having a connection with BT that logged me on and off every few minutes). I went a bit on the internet with IE after the first start on the new laptop too, so I know it worked perfectly well when Windows was running instead of Ubuntu.
And when I go downstairs, next to where the BE Box is, I get only a two bar signal...

I saw quite a few threads about this similar problem on other laptops, but quite frankly, I don't know anything about computers and all the solutions given looked like Chinese to me... ^^"

So if someone had a solution and could baby step me though its completion, I would be ever so grateful as the reason I bought a new laptop is that my dear old Mac (six years of services) will be dying at any moment...

If you need any information on the machine I'd of course give them as quick as possible, as long as you can tell where I can find it. 

Cheers,
Raven.

---

### Post by ravenkrane on 2012-09-03
Here is all the information asked in the Howto post, hope it will help to resolve my problem.  :)

**1 ) Machine Brand and Model (PC/Laptop):**
```
HP Pavilion dm1 4175sa 
```**2 ) Wireless Brand, Model and Wireless Chipset:**
```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
``````

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c8:032b Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 006 Device 002: ID 0a5c:21e3 Broadcom Corp.
```**3 ) check interface:**
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr a0:b3:cc:71:0b:ff  
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
          RX packets:251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27595 (27.5 KB)  TX bytes:27595 (27.5 KB)

wlan0     Link encap:Ethernet  HWaddr 08:ed:b9:0d:2f:6f  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aed:b9ff:fe0d:2f6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3234970 (3.2 MB)  TX bytes:473186 (473.1 KB)
``````
$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"PISTACHIO"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:5D:4C:FA:0A:9A   
          Bit Rate=21.7 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:445  Invalid misc:759   Missed beacon:0

eth0      no wireless extensions.
```**4 ) Check for modules:**
```
$ lsmod
Module                  Size  Used by
bcma                   26696  0 
arc4                   12529  2 
parport_pc             32866  0 
rfcomm                 47604  12 
ppdev                  17113  0 
bnep                   18281  2 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hp_wmi                 18092  0 
joydev                 17693  0 
sparse_keymap          13890  1 hp_wmi
radeon                804372  3 
ums_realtek            18248  0 
uas                    18180  0 
snd_hda_codec_idt      70795  1 
brcmsmac              570874  0 
snd_hda_codec_hdmi     32474  1 
snd_seq_midi           13324  0 
mac80211              506816  1 brcmsmac
snd_rawmidi            30748  1 snd_seq_midi
btusb                  18288  2 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
bluetooth             180104  23 rfcomm,bnep,btusb
ttm                    76949  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
brcmutil               15139  1 brcmsmac
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              205544  2 brcmsmac,mac80211
k10temp                13166  0 
crc8                   12893  1 brcmsmac
drm_kms_helper         46978  1 radeon
v4l2_compat_ioctl32    17128  1 videodev
cordic                 12535  1 brcmsmac
drm                   242038  5 radeon,ttm,drm_kms_helper
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13423  1 radeon
snd                    78855  20 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 hp_wmi
video                  19596  0 
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13253  0 
usb_storage            49198  1 ums_realtek
r8169                  62099  0 
```**5 ) Kernel boot messages**
```
$ dmesg
[  326.916478] ieee80211 phy0: AMPDU status: BA Timeout, seq 2329, in_transit 8
[  326.916497] ieee80211 phy0: AMPDU status: BA Timeout, seq 2332, in_transit 5
[  326.916510] ieee80211 phy0: AMPDU status: BA Timeout, seq 2335, in_transit 2
[  326.916520] ieee80211 phy0: AMPDU status: BA Timeout, seq 2337, in_transit 0
[  326.929216] ieee80211 phy0: AMPDU status: BA Timeout, seq 2330, in_transit 4
[  326.929230] ieee80211 phy0: AMPDU status: BA Timeout, seq 2331, in_transit 3
[  326.929237] ieee80211 phy0: AMPDU status: BA Timeout, seq 2333, in_transit 2
[  326.929243] ieee80211 phy0: AMPDU status: BA Timeout, seq 2334, in_transit 1
[  326.929249] ieee80211 phy0: AMPDU status: BA Timeout, seq 2336, in_transit 0
[  332.997902] ieee80211 phy0: AMPDU status: BA Timeout, seq 2393, in_transit 0
[  340.314761] ieee80211 phy0: AMPDU status: BA Timeout, seq 2395, in_transit 0
[  340.728580] ieee80211 phy0: AMPDU status: BA Timeout, seq 2398, in_transit 0
[  341.298989] ieee80211 phy0: AMPDU status: BA Timeout, seq 2403, in_transit 0
[  341.812906] ieee80211 phy0: AMPDU status: BA Timeout, seq 2404, in_transit 0
[  343.538105] ieee80211 phy0: AMPDU status: BA Timeout, seq 2437, in_transit 16
[  343.558850] ieee80211 phy0: AMPDU status: BA Timeout, seq 2438, in_transit 15
[  343.558871] ieee80211 phy0: AMPDU status: BA Timeout, seq 2439, in_transit 14
[  343.558883] ieee80211 phy0: AMPDU status: BA Timeout, seq 2440, in_transit 13
[  343.558895] ieee80211 phy0: AMPDU status: BA Timeout, seq 2441, in_transit 12
[  343.558907] ieee80211 phy0: AMPDU status: BA Timeout, seq 2442, in_transit 11
[  343.558918] ieee80211 phy0: AMPDU status: BA Timeout, seq 2443, in_transit 10
[  343.558930] ieee80211 phy0: AMPDU status: BA Timeout, seq 2444, in_transit 9
[  343.558941] ieee80211 phy0: AMPDU status: BA Timeout, seq 2445, in_transit 8
[  343.558952] ieee80211 phy0: AMPDU status: BA Timeout, seq 2446, in_transit 7
[  343.558963] ieee80211 phy0: AMPDU status: BA Timeout, seq 2447, in_transit 6
[  343.558973] ieee80211 phy0: AMPDU status: BA Timeout, seq 2448, in_transit 5
[  343.558984] ieee80211 phy0: AMPDU status: BA Timeout, seq 2449, in_transit 4
[  343.558995] ieee80211 phy0: AMPDU status: BA Timeout, seq 2450, in_transit 3
[  343.559005] ieee80211 phy0: AMPDU status: BA Timeout, seq 2451, in_transit 2
[  343.559016] ieee80211 phy0: AMPDU status: BA Timeout, seq 2452, in_transit 1
[  343.559027] ieee80211 phy0: AMPDU status: BA Timeout, seq 2453, in_transit 0
[  343.610800] ieee80211 phy0: AMPDU status: BA Timeout, seq 2454, in_transit 0
[  343.612783] ieee80211 phy0: AMPDU status: BA Timeout, seq 2457, in_transit 0
[  343.808434] ieee80211 phy0: AMPDU status: BA Timeout, seq 2459, in_transit 2
[  343.917756] ieee80211 phy0: AMPDU status: BA Timeout, seq 2462, in_transit 9
[  343.917778] ieee80211 phy0: AMPDU status: BA Timeout, seq 2467, in_transit 4
[  343.917785] ieee80211 phy0: AMPDU status: BA Timeout, seq 2468, in_transit 3
[  343.932716] ieee80211 phy0: AMPDU status: BA Timeout, seq 2463, in_transit 6
[  343.932729] ieee80211 phy0: AMPDU status: BA Timeout, seq 2464, in_transit 5
[  343.932735] ieee80211 phy0: AMPDU status: BA Timeout, seq 2465, in_transit 4
[  343.932742] ieee80211 phy0: AMPDU status: BA Timeout, seq 2466, in_transit 3
[  343.932748] ieee80211 phy0: AMPDU status: BA Timeout, seq 2469, in_transit 2
[  343.932755] ieee80211 phy0: AMPDU status: BA Timeout, seq 2470, in_transit 1
[  343.932761] ieee80211 phy0: AMPDU status: BA Timeout, seq 2471, in_transit 0
[  343.947104] ieee80211 phy0: AMPDU status: BA Timeout, seq 2472, in_transit 0
[  343.968868] ieee80211 phy0: AMPDU status: BA Timeout, seq 2473, in_transit 0
[  344.273442] ieee80211 phy0: AMPDU status: BA Timeout, seq 2482, in_transit 0
[  344.808139] ieee80211 phy0: AMPDU status: BA Timeout, seq 2484, in_transit 0
[  346.082550] ieee80211 phy0: AMPDU status: BA Timeout, seq 2501, in_transit 0
[  346.088867] ieee80211 phy0: AMPDU status: BA Timeout, seq 2502, in_transit 0
[  346.171280] ieee80211 phy0: AMPDU status: BA Timeout, seq 2505, in_transit 0
[  346.498020] ieee80211 phy0: AMPDU status: BA Timeout, seq 2516, in_transit 0
[  346.765956] ieee80211 phy0: AMPDU status: BA Timeout, seq 2526, in_transit 0
[  346.804430] ieee80211 phy0: AMPDU status: BA Timeout, seq 2527, in_transit 0
[  346.817744] ieee80211 phy0: AMPDU status: BA Timeout, seq 2528, in_transit 1
[  346.817758] ieee80211 phy0: AMPDU status: BA Timeout, seq 2529, in_transit 0
[  346.878760] ieee80211 phy0: AMPDU status: BA Timeout, seq 2530, in_transit 0
[  346.978487] ieee80211 phy0: AMPDU status: BA Timeout, seq 2531, in_transit 0
[  347.003517] ieee80211 phy0: AMPDU status: BA Timeout, seq 2532, in_transit 3
[  347.003530] ieee80211 phy0: AMPDU status: BA Timeout, seq 2533, in_transit 2
[  347.003537] ieee80211 phy0: AMPDU status: BA Timeout, seq 2534, in_transit 1
[  347.003543] ieee80211 phy0: AMPDU status: BA Timeout, seq 2535, in_transit 0
[  347.142152] ieee80211 phy0: AMPDU status: BA Timeout, seq 2536, in_transit 0
[  347.192444] ieee80211 phy0: AMPDU status: BA Timeout, seq 2537, in_transit 5
[  347.476523] ieee80211 phy0: AMPDU status: BA Timeout, seq 2546, in_transit 4
[  347.476549] ieee80211 phy0: AMPDU status: BA Timeout, seq 2548, in_transit 2
[  347.863902] ieee80211 phy0: AMPDU status: BA Timeout, seq 2565, in_transit 0
[  347.902807] ieee80211 phy0: AMPDU status: BA Timeout, seq 2566, in_transit 0
[  348.728459] ieee80211 phy0: AMPDU status: BA Timeout, seq 2599, in_transit 0
[  348.736186] ieee80211 phy0: AMPDU status: BA Timeout, seq 2601, in_transit 0
[  350.848259] ieee80211 phy0: AMPDU status: BA Timeout, seq 2615, in_transit 0
[  351.293988] ieee80211 phy0: AMPDU status: BA Timeout, seq 2629, in_transit 0
[  356.950886] ieee80211 phy0: AMPDU status: BA Timeout, seq 2664, in_transit 0
[  413.182464] ieee80211 phy0: AMPDU status: BA Timeout, seq 2693, in_transit 0
[  413.884599] ieee80211 phy0: AMPDU status: BA Timeout, seq 2728, in_transit 3
[  684.329293] r8169 0000:07:00.0: PME# enabled
[  684.721677] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  684.723847] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  684.723873] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  684.723887] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  684.723899] wlan0: deauthenticating from d8:5d:4c:fa:0a:9a by local choice (reason=3)
[  684.732561] cfg80211: All devices are disconnected, going to restore regulatory settings
[  684.732581] cfg80211: Restoring regulatory settings
[  684.734271] cfg80211: Calling CRDA to update world regulatory domain
[  684.751201] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  684.751211] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751216] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  684.751221] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751225] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  684.751230] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751234] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  684.751238] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751242] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  684.751246] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751250] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  684.751255] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751259] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  684.751263] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751267] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  684.751271] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751275] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  684.751279] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751283] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  684.751288] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751291] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  684.751296] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751300] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  684.751304] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  684.751308] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  684.751312] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  684.751316] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  684.751321] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  684.751326] cfg80211: World regulatory domain updated:
[  684.751329] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  684.751334] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751338] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  684.751342] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  684.751346] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  684.751350] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  685.788435] r8169 0000:07:00.0: PME# disabled
[  687.366683] init: anacron main process (2339) killed by TERM signal
[  687.990841] PM: Syncing filesystems ... done.
[  688.002844] PM: Preparing system for mem sleep
[  688.384108] Freezing user space processes ... (elapsed 0.01 seconds) done.
[  688.400330] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[  688.416339] PM: Entering mem sleep
[  688.416506] Suspending console(s) (use no_console_suspend to debug)
[  688.417129] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  688.417629] sd 0:0:0:0: [sda] Stopping disk
[  688.471507] i8042 aux 00:08: wake-up capability disabled by ACPI
[  688.471540] i8042 kbd 00:07: wake-up capability enabled by ACPI
[  688.472516] brcmsmac 0000:03:00.0: PCI INT A disabled
[  688.472580] ohci_hcd 0000:00:16.0: PCI INT A disabled
[  688.473200] pciehp 0000:00:04.0:pcie04: pciehp_suspend ENTRY
[  688.473250] snd_hda_intel 0000:00:01.1: PCI INT B disabled
[  688.473292] ACPI handle has no context!
[  688.512383] ehci_hcd 0000:00:13.2: PCI INT B disabled
[  688.516385] ehci_hcd 0000:00:12.2: PCI INT B disabled
[  688.536298] ehci_hcd 0000:00:16.2: PCI INT B disabled
[  688.548433] ohci_hcd 0000:00:13.0: PCI INT A disabled
[  688.548480] ohci_hcd 0000:00:12.0: PCI INT A disabled
[  688.577044] snd_hda_intel 0000:00:14.2: PCI INT A disabled
[  688.592117] PM: suspend of drv:snd_hda_intel dev:0000:00:14.2 complete after 119.427 msecs
[  689.037557] PM: suspend of drv:sd dev:0:0:0:0 complete after 620.434 msecs
[  689.037588] PM: suspend of drv:scsi dev:target0:0:0 complete after 619.965 msecs
[  689.037599] PM: suspend of drv:scsi dev:host0 complete after 565.308 msecs
[  689.037776] ahci 0000:00:11.0: PCI INT A disabled
[  689.037786] PM: suspend of drv:ahci dev:0000:00:11.0 complete after 564.640 msecs
[  689.880319] PM: suspend of drv:radeon dev:0000:00:01.0 complete after 1406.937 msecs
[  689.880492] PM: suspend of drv: dev:pci0000:00 complete after 1406.985 msecs
[  689.880513] PM: suspend of devices complete after 1463.770 msecs
[  689.880517] PM: suspend devices took 1.464 seconds
[  689.880890] r8169 0000:07:00.0: PME# enabled
[  689.880932] pcieport 0000:00:15.1: wake-up capability enabled by ACPI
[  689.896892] ehci_hcd 0000:00:16.2: PME# enabled
[  689.912541] ehci_hcd 0000:00:13.2: PME# enabled
[  689.912566] ehci_hcd 0000:00:13.2: wake-up capability enabled by ACPI
[  689.928434] ohci_hcd 0000:00:13.0: wake-up capability enabled by ACPI
[  689.928482] ehci_hcd 0000:00:12.2: PME# enabled
[  689.928490] ehci_hcd 0000:00:12.2: wake-up capability enabled by ACPI
[  689.944433] ohci_hcd 0000:00:12.0: wake-up capability enabled by ACPI
[  689.944508] PM: late suspend of devices complete after 63.986 msecs
[  689.944545] ACPI: Preparing to enter system sleep state S3
[  690.050532] PM: Saving platform NVS memory
[  690.055855] Disabling non-boot CPUs ...
[  690.057341] Broke affinity for irq 18
[  690.057356] Broke affinity for irq 43
[  690.160306] CPU 1 is now offline
[  690.160924] ACPI: Low-level resume complete
[  690.160924] PM: Restoring platform NVS memory
[  690.160924] Enabling non-boot CPUs ...
[  690.160924] Booting Node 0 Processor 1 APIC 0x1
[  690.160924] smpboot cpu 1: start_ip = 9a000
[  690.172463] Calibrating delay loop (skipped) already calibrated this CPU
[  690.193339] NMI watchdog enabled, takes one hw-pmu counter.
[  690.194101] CPU1 is up
[  690.195148] ACPI: Waking up from system sleep state S3
[  691.296636] radeon 0000:00:01.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100407)
[  691.296723] pcieport 0000:00:04.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[  691.296732] pcieport 0000:00:04.0: restoring config space at offset 0xc (was 0xffff, writing 0x0)
[  691.296739] pcieport 0000:00:04.0: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[  691.296755] pcieport 0000:00:04.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  691.296891] ahci 0000:00:11.0: restoring config space at offset 0x1 (was 0x2300003, writing 0x2300007)
[  691.296933] ohci_hcd 0000:00:12.0: restoring config space at offset 0x1 (was 0x2a00011, writing 0x2a00013)
[  691.296951] ohci_hcd 0000:00:12.0: wake-up capability disabled by ACPI
[  691.312393] ehci_hcd 0000:00:12.2: BAR 0: set to [mem 0xf034c000-0xf034c0ff] (PCI address [0xf034c000-0xf034c0ff])
[  691.312437] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[  691.312475] ehci_hcd 0000:00:12.2: wake-up capability disabled by ACPI
[  691.312483] ehci_hcd 0000:00:12.2: PME# disabled
[  691.312516] ohci_hcd 0000:00:13.0: restoring config space at offset 0x1 (was 0x2a00011, writing 0x2a00013)
[  691.312530] ohci_hcd 0000:00:13.0: wake-up capability disabled by ACPI
[  691.328393] ehci_hcd 0000:00:13.2: BAR 0: set to [mem 0xf034a000-0xf034a0ff] (PCI address [0xf034a000-0xf034a0ff])
[  691.328437] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[  691.328475] ehci_hcd 0000:00:13.2: wake-up capability disabled by ACPI
[  691.328483] ehci_hcd 0000:00:13.2: PME# disabled
[  691.328550] snd_hda_intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100000, writing 0x4100002)
[  691.328654] pcieport 0000:00:15.0: restoring config space at offset 0x7 (was 0x20003131, writing 0x3131)
[  691.328664] pcieport 0000:00:15.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  691.328727] pcieport 0000:00:15.1: restoring config space at offset 0x7 (was 0x20002121, writing 0x2121)
[  691.328738] pcieport 0000:00:15.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  691.344394] ehci_hcd 0000:00:16.2: BAR 0: set to [mem 0xf0348000-0xf03480ff] (PCI address [0xf0348000-0xf03480ff])
[  691.344438] ehci_hcd 0000:00:16.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[  691.344462] ehci_hcd 0000:00:16.2: PME# disabled
[  691.344765] brcmsmac 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[  691.360455] r8169 0000:07:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  691.360688] PM: early resume of devices complete after 64.160 msecs
[  691.360937] radeon 0000:00:01.0: setting latency timer to 64
[  691.360952] snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  691.360964] snd_hda_intel 0000:00:01.1: setting latency timer to 64
[  691.361036] snd_hda_intel 0000:00:01.1: irq 42 for MSI/MSI-X
[  691.361089] pciehp 0000:00:04.0:pcie04: pciehp_resume ENTRY
[  691.361174] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  691.361229] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  691.361273] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  691.361341] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  691.361372] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  691.361404] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  691.361457] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  691.361486] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  691.361540] brcmsmac 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  691.361548] brcmsmac 0000:03:00.0: setting latency timer to 64
[  691.361599] pcieport 0000:00:15.1: wake-up capability disabled by ACPI
[  691.361677] r8169 0000:07:00.0: PME# disabled
[  691.375791] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[  691.376203] radeon 0000:00:01.0: WB enabled
[  691.392482] [drm] ring test succeeded in 1 usecs
[  691.392513] [drm] ib test succeeded in 0 usecs
[  691.400143] sd 0:0:0:0: [sda] Starting disk
[  691.424100] usb usb4: root hub lost power or was reset
[  691.429774] usb usb5: root hub lost power or was reset
[  691.552359] PM: resume of drv:hub dev:3-0:1.0 complete after 152.922 msecs
[  691.552374] PM: resume of drv: dev:ep_00 complete after 152.914 msecs
[  691.552382] PM: resume of drv: dev:ep_81 complete after 152.939 msecs
[  691.556356] PM: resume of drv:hub dev:1-0:1.0 complete after 157.493 msecs
[  691.556370] PM: resume of drv: dev:ep_00 complete after 157.012 msecs
[  691.556410] PM: resume of drv: dev:ep_81 complete after 157.533 msecs
[  691.556431] PM: resume of drv:ac dev:ACPI0003:00 complete after 116.218 msecs
[  691.620402] PM: resume of drv: dev:ep_00 complete after 220.702 msecs
[  691.620424] PM: resume of drv:hub dev:4-0:1.0 complete after 220.825 msecs
[  691.620570] PM: resume of drv: dev:ep_81 complete after 220.918 msecs
[  691.624409] PM: resume of drv: dev:ep_00 complete after 224.545 msecs
[  691.624456] PM: resume of drv:hub dev:5-0:1.0 complete after 224.676 msecs
[  691.624542] PM: resume of drv: dev:ep_81 complete after 224.726 msecs
[  691.668347] usb 1-3: reset high-speed USB device number 2 using ehci_hcd
[  691.767883] PM: resume of drv:battery dev:PNP0C0A:00 complete after 211.427 msecs
[  691.769766] i8042 kbd 00:07: wake-up capability disabled by ACPI
[  691.930049] PM: resume of drv: dev:ep_00 complete after 529.581 msecs
[  691.930073] PM: resume of drv:uvcvideo dev:1-3:1.1 complete after 529.660 msecs
[  691.930082] PM: resume of drv:uvcvideo dev:1-3:1.0 complete after 529.752 msecs
[  691.930113] PM: resume of drv: dev:ep_83 complete after 529.734 msecs
[  692.016382] usb 6-1: reset full-speed USB device number 2 using ohci_hcd
[  692.181376] btusb 6-1:1.0: no reset_resume for driver btusb?
[  692.181390] btusb 6-1:1.1: no reset_resume for driver btusb?
[  692.432446] PM: resume of drv:usb dev:6-1:1.0 complete after 1031.908 msecs
[  692.432502] PM: resume of drv:usb dev:6-1:1.1 complete after 1031.807 msecs
[  692.432516] PM: resume of drv: dev:ep_00 complete after 1031.533 msecs
[  692.432526] PM: resume of drv:usb dev:6-1:1.2 complete after 1031.702 msecs
[  692.432539] PM: resume of drv:usb dev:6-1:1.3 complete after 1031.602 msecs
[  692.432548] PM: resume of drv: dev:ep_83 complete after 1031.805 msecs
[  692.432553] PM: resume of drv: dev:ep_02 complete after 1031.897 msecs
[  692.432560] PM: resume of drv: dev:ep_03 complete after 1031.785 msecs
[  692.432565] PM: resume of drv: dev:ep_82 complete after 1031.951 msecs
[  692.432570] PM: resume of drv: dev:ep_84 complete after 1031.714 msecs
[  692.432574] PM: resume of drv: dev:ep_81 complete after 1031.999 msecs
[  692.432615] PM: resume of drv: dev:ep_04 complete after 1031.720 msecs
[  692.824202] PM: resume of drv:radeon dev:0000:00:01.0 complete after 1463.272 msecs
[  693.000258] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  693.159039] ata1.00: configured for UDMA/133
[  693.200930] PM: resume of drv:sd dev:0:0:0:0 complete after 1800.785 msecs
[  693.200958] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1429.860 msecs
[  693.201079] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1800.844 msecs
[  693.207791] PM: resume of devices complete after 1846.996 msecs
[  693.208721] PM: resume devices took 1.848 seconds
[  693.208786] PM: Finishing wakeup.
[  693.208788] Restarting tasks ... done.
[  693.270502] video LNXVIDEO:00: Restoring backlight state
[  693.278101] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -35!
[  693.320123] usb 3-4: new high-speed USB device number 4 using ehci_hcd
[  693.744533] scsi2 : usb-storage 3-4:1.0
[  693.744873] usb 3-4: USB disconnect, device number 4
[  694.523408] init: anacron main process (2793) killed by TERM signal
[  694.742546] r8169 0000:07:00.0: PME# enabled
[  694.940241] r8169 0000:07:00.0: PME# disabled
[  695.051452] r8169 0000:07:00.0: eth0: link down
[  695.052841] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  695.111108] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[  695.111121] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[  695.112406] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  695.113293] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  697.718880] wlan0: authenticate with d8:5d:4c:fa:0a:9a (try 1)
[  697.916118] wlan0: authenticate with d8:5d:4c:fa:0a:9a (try 2)
[  697.977296] wlan0: authenticated
[  697.984522] wlan0: associate with d8:5d:4c:fa:0a:9a (try 1)
[  698.184156] wlan0: associate with d8:5d:4c:fa:0a:9a (try 2)
[  698.192064] wlan0: RX AssocResp from d8:5d:4c:fa:0a:9a (capab=0x401 status=0 aid=5)
[  698.192079] wlan0: associated
[  698.192731] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  698.192757] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  698.192770] ieee80211 phy0: changing basic rates failed: -22
[  698.192781] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  698.194489] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  698.843455] ieee80211 phy0: AMPDU status: BA Timeout, seq 3, in_transit 0
[  698.982926] ieee80211 phy0: AMPDU status: BA Timeout, seq 4, in_transit 0
[  699.983568] ieee80211 phy0: AMPDU status: BA Timeout, seq 5, in_transit 0
[  700.002940] ieee80211 phy0: AMPDU status: BA Timeout, seq 6, in_transit 0
[  700.075221] ieee80211 phy0: AMPDU status: BA Timeout, seq 7, in_transit 0
[  700.248382] ieee80211 phy0: AMPDU status: BA Timeout, seq 8, in_transit 0
[  700.306433] ieee80211 phy0: AMPDU status: BA Timeout, seq 9, in_transit 0
[  700.499647] ieee80211 phy0: AMPDU status: BA Timeout, seq 10, in_transit 0
[  700.757371] ieee80211 phy0: AMPDU status: BA Timeout, seq 11, in_transit 0
[  700.958893] ieee80211 phy0: AMPDU status: BA Timeout, seq 12, in_transit 0
[  701.063444] ieee80211 phy0: AMPDU status: BA Timeout, seq 13, in_transit 0
[  701.084802] ieee80211 phy0: AMPDU status: BA Timeout, seq 14, in_transit 0
[  701.539766] ieee80211 phy0: AMPDU status: BA Timeout, seq 15, in_transit 0
[  701.839498] ieee80211 phy0: AMPDU status: BA Timeout, seq 16, in_transit 0
[  702.197207] ieee80211 phy0: AMPDU status: BA Timeout, seq 17, in_transit 0
[  703.087128] ieee80211 phy0: AMPDU status: BA Timeout, seq 18, in_transit 0
[  703.759608] ieee80211 phy0: AMPDU status: BA Timeout, seq 19, in_transit 0
[  703.998805] ieee80211 phy0: AMPDU status: BA Timeout, seq 20, in_transit 0
[  704.411433] ieee80211 phy0: AMPDU status: BA Timeout, seq 21, in_transit 0
[  705.482145] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  705.594949] ieee80211 phy0: AMPDU status: BA Timeout, seq 23, in_transit 0
[  705.766132] ieee80211 phy0: AMPDU status: BA Timeout, seq 24, in_transit 0
[  705.826284] ieee80211 phy0: AMPDU status: BA Timeout, seq 25, in_transit 0
[  706.029828] ieee80211 phy0: AMPDU status: BA Timeout, seq 26, in_transit 0
[  706.462730] ieee80211 phy0: AMPDU status: BA Timeout, seq 28, in_transit 0
[  708.123787] ieee80211 phy0: AMPDU status: BA Timeout, seq 48, in_transit 0
[  708.590449] ieee80211 phy0: AMPDU status: BA Timeout, seq 49, in_transit 0
[  708.992046] wlan0: no IPv6 routers present
[  709.251644] ieee80211 phy0: AMPDU status: BA Timeout, seq 50, in_transit 0
[  709.292610] ieee80211 phy0: AMPDU status: BA Timeout, seq 51, in_transit 0
[  709.889147] ieee80211 phy0: AMPDU status: BA Timeout, seq 52, in_transit 0
[  709.919679] ieee80211 phy0: AMPDU status: BA Timeout, seq 53, in_transit 0
[  711.387375] ieee80211 phy0: AMPDU status: BA Timeout, seq 54, in_transit 0
[  711.682510] ieee80211 phy0: AMPDU status: BA Timeout, seq 55, in_transit 0
[  712.607191] ieee80211 phy0: AMPDU status: BA Timeout, seq 56, in_transit 0
[  713.135615] ieee80211 phy0: AMPDU status: BA Timeout, seq 57, in_transit 0
[  713.292260] ieee80211 phy0: AMPDU status: BA Timeout, seq 58, in_transit 0
[  713.943347] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  713.943374] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  713.943387] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[  713.948648] cfg80211: All devices are disconnected, going to restore regulatory settings
[  713.948668] cfg80211: Restoring regulatory settings
[  713.948680] cfg80211: Calling CRDA to update world regulatory domain
[  713.961992] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  713.962008] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962017] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  713.962027] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962035] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  713.962044] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962052] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  713.962061] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962069] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  713.962078] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962085] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  713.962094] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962102] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  713.962110] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962118] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  713.962127] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962134] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  713.962143] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962150] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  713.962159] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962167] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  713.962175] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962183] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  713.962192] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  713.962200] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  713.962208] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  713.962216] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  713.962225] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  713.962235] cfg80211: World regulatory domain updated:
[  713.962241] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  713.962249] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962257] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  713.962265] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  713.962273] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  713.962281] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  720.839197] wlan0: authenticate with d8:5d:4c:fa:0a:9a (try 1)
[  720.840874] wlan0: authenticated
[  720.841451] wlan0: associate with d8:5d:4c:fa:0a:9a (try 1)
[  720.845232] wlan0: RX ReassocResp from d8:5d:4c:fa:0a:9a (capab=0x401 status=0 aid=5)
[  720.845247] wlan0: associated
[  720.845846] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  720.845870] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  720.845884] ieee80211 phy0: changing basic rates failed: -22
[  720.845894] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  722.096365] ieee80211 phy0: AMPDU status: BA Timeout, seq 3, in_transit 0

```**6 ) Network configuration**
```
$ sudo lshw -C network
PCI (sysfs)  


  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 08:ed:b9:0d:2f:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.124 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: a0:b3:cc:71:0b:ff
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:f0104000-f0104fff memory:f0100000-f0103fff
```**7 ) Scan for networks:**
```
$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: D8:5D:4C:FA:0A:9A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"PISTACHIO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000027e1ea2f183
                    Extra: Last beacon: 2796ms ago
                    IE: Unknown: 000950495354414348494F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B000103104700106212728FE778F514E1A1165EF72AAD131021000754502D4C494E4B1023000754502D4C494E4B1024000631323334353610420004313233341054000800060050F20400011011000954442D57383936304E100800020088
                    IE: Unknown: DD090010180207F4050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080400000000000000000000000000000000000000

eth0      Interface doesn't support scanning.
```**8 ) Ubuntu Version:**
```
$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS

```**9 ) Kernel/architecture (including 32 vs. 64 bit):**
```
$ uname -mr
3.2.0-29-generic x86_64
```**10 ) Restarting the network:**
```
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...


```

---

