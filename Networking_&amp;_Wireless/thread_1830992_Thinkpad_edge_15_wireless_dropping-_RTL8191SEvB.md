---
title: "Thinkpad edge 15 wireless dropping- RTL8191SEvB"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by lemeiux1 on 2011-08-22
Hello, I am relatively new to ubuntu and linux for that matter but I was wondering if someone can help me with a wireless issue.  I have a Lenovo thinkpad edge 15 running an amd processor and I have installed ubuntu 11.04 via wubi.  Everything is working great except my wireless connection drops after a about 10-15 minutes of use and the only way to get it back is disconnecting and then reconnecting through network manger

here are some things that might be useful and please tell me if you need any more info

-_**Network controller:**_ Realtek RTL8191SEvB wireless LAN controller

_**iwconfig wlan0**_

```
wlan0     802.11bgn  ESSID:"dlink"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:1E:58:38:A3:01   
          Bit Rate=135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

_**lsmod**_

```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
joydev                 17606  0 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
thinkpad_acpi          81587  0 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
r8192se_pci           524220  0 
uvcvideo               72195  0 
btusb                  18600  2 
fglrx                2739144  51 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               82052  1 uvcvideo
psmouse                73535  0 
cfg80211              178528  1 r8192se_pci
v4l2_compat_ioctl32    17078  1 videodev
serio_raw              13166  0 
soundcore              12680  1 snd
edac_core              53845  0 
edac_mce_amd           23464  0 
k10temp                13119  0 
sp5100_tco             13744  0 
nvram                  14419  1 thinkpad_acpi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13303  0 
video                  19438  0 
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  1 
libahci                26642  1 ahci
r8169                  48022  0 

```

_**dmesg**_

```
[   15.941101] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.941104] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941106] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.941109] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941110] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.941113] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941115] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.941117] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941119] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.941121] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941123] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.941125] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941127] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.941129] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941131] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.941134] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941136] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.941139] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941141] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.941143] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941145] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.941147] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941149] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.941151] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941153] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.941155] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.941157] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.941160] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.958540] rtl8192: wireless switch is on
[   16.016192] [fglrx] Maximum main memory to use for locked dma buffers: 3550 MBytes.
[   16.016256] [fglrx]   vendor: 1002 device: 9712 count: 1
[   16.016646] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   16.016659] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.016663] pci 0000:01:05.0: setting latency timer to 64
[   16.017026] [fglrx] Kernel PAT support is enabled
[   16.017045] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   16.074211] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   16.074214] thinkpad_acpi: http://ibm-acpi.sf.net/
[   16.074216] thinkpad_acpi: ThinkPad BIOS 82ET61WW (2.02 ), EC 82HT26WW-1.172000
[   16.074218] thinkpad_acpi: Lenovo ThinkPad Edge, model 0302CTO
[   16.076195] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   16.076521] thinkpad_acpi: radio switch found; radios are enabled
[   16.076528] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   16.077794] thinkpad_acpi: asked for hotkey mask 0x04018070, but firmware forced it to 0x00018070
[   16.078728] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.082359] Registered led device: tpacpi::thinklight
[   16.082876] Registered led device: tpacpi::power
[   16.083348] Registered led device: tpacpi::standby
[   16.083793] Registered led device: tpacpi::thinkvantage
[   16.093485] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   16.093594] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   16.097589] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   16.150149] hda-intel: Enable sync_write for AMD chipset
[   16.178842] hda_codec: ALC269: BIOS auto-probing.
[   16.184998] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   16.185054] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   16.185346] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.185408] HDA Intel 0000:01:05.1: setting latency timer to 64
[   16.220116] hda-intel: Enable sync_write for AMD chipset
[   16.243274] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   16.308677] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   16.675532] type=1400 audit(1314048455.574:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=854 comm="apparmor_parser"
[   16.677123] type=1400 audit(1314048455.574:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=853 comm="apparmor_parser"
[   16.679373] type=1400 audit(1314048455.574:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=854 comm="apparmor_parser"
[   16.679591] type=1400 audit(1314048455.574:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=854 comm="apparmor_parser"
[   16.699275] type=1400 audit(1314048455.594:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=855 comm="apparmor_parser"
[   16.707671] type=1400 audit(1314048455.604:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=855 comm="apparmor_parser"
[   16.723207] type=1400 audit(1314048455.624:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=857 comm="apparmor_parser"
[   16.739107] ppdev: user-space parallel port driver
[   16.835218] r8169 0000:08:00.0: eth0: link down
[   16.835893] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.842638] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd047b3/0xb40000/0xa0400
[   16.842645] serio: Synaptics pass-through port at isa0060/serio4/input0
[   16.905101] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   16.976501] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   16.976507] ===>rtllib_start_scan()
[   16.976516] =====>rtl8192_set_chan()====ch:2
[   17.000505] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.080084] =====>rtl8192_set_chan()====ch:3
[   17.088372] [fglrx] ATIF platform detected with notification ID: 0x81
[   17.093731] =====>rtl8192_set_chan()====ch:1
[   17.215412] [fglrx] GART Table is not in FRAME_BUFFER range 
[   17.216475] [fglrx] Could not enable MSI; System prevented initialization
[   17.216983] [fglrx] Firegl kernel thread PID: 1054
[   17.217026] [fglrx] Firegl kernel thread PID: 1055
[   17.217070] [fglrx] Firegl kernel thread PID: 1056
[   17.217343] [fglrx] IRQ 18 Enabled
[   17.220040] =====>rtl8192_set_chan()====ch:2
[   17.331471] Bluetooth: L2CAP ver 2.15
[   17.331474] Bluetooth: L2CAP socket layer initialized
[   17.340027] =====>rtl8192_set_chan()====ch:3
[   17.355206] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.355209] Bluetooth: BNEP filters: protocol multicast
[   17.371231] Bluetooth: SCO (Voice Link) ver 0.6
[   17.371235] Bluetooth: SCO socket layer initialized
[   17.460064] =====>rtl8192_set_chan()====ch:4
[   17.540866] [fglrx] Gart USWC size:1160 M.
[   17.540869] [fglrx] Gart cacheable size:459 M.
[   17.540874] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.540876] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   17.557018] Bluetooth: RFCOMM TTY layer initialized
[   17.557023] Bluetooth: RFCOMM socket layer initialized
[   17.557025] Bluetooth: RFCOMM ver 1.11
[   17.580022] =====>rtl8192_set_chan()====ch:5
[   17.610615] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
[   17.700050] =====>rtl8192_set_chan()====ch:6
[   17.821407] =====>rtl8192_set_chan()====ch:7
[   17.940044] =====>rtl8192_set_chan()====ch:8
[   18.060037] =====>rtl8192_set_chan()====ch:9
[   18.181395] =====>rtl8192_set_chan()====ch:10
[   18.300066] =====>rtl8192_set_chan()====ch:11
[   18.420967] =====>rtl8192_set_chan()====ch:12
[   18.540032] =====>rtl8192_set_chan()====ch:13
[   18.665615] =====>rtl8192_set_chan()====ch:1
[   18.790043] =====>rtl8192_set_chan()====ch:2
[   18.910049] =====>rtl8192_set_chan()====ch:3
[   19.030034] =====>rtl8192_set_chan()====ch:4
[   19.150215] =====>rtl8192_set_chan()====ch:5
[   19.234594] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
[   19.280035] =====>rtl8192_set_chan()====ch:6
[   19.400083] =====>rtl8192_set_chan()====ch:7
[   19.520024] =====>rtl8192_set_chan()====ch:8
[   19.640065] =====>rtl8192_set_chan()====ch:9
[   19.760046] =====>rtl8192_set_chan()====ch:10
[   19.880058] =====>rtl8192_set_chan()====ch:11
[   20.000064] =====>rtl8192_set_chan()====ch:12
[   20.120055] =====>rtl8192_set_chan()====ch:13
[   21.375495] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   23.159703] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   23.159953] =====>rtl8192_set_chan()====ch:1
[   23.280063] =====>rtl8192_set_chan()====ch:2
[   23.400059] =====>rtl8192_set_chan()====ch:3
[   23.520055] =====>rtl8192_set_chan()====ch:4
[   23.640045] =====>rtl8192_set_chan()====ch:5
[   23.760041] =====>rtl8192_set_chan()====ch:6
[   23.880039] =====>rtl8192_set_chan()====ch:7
[   24.000052] =====>rtl8192_set_chan()====ch:8
[   24.120052] =====>rtl8192_set_chan()====ch:9
[   24.240063] =====>rtl8192_set_chan()====ch:10
[   24.360055] =====>rtl8192_set_chan()====ch:11
[   24.448508] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   24.480054] =====>rtl8192_set_chan()====ch:12
[   24.600056] =====>rtl8192_set_chan()====ch:13
[   24.741406] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input10
[   28.156249] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   28.156497] =====>rtl8192_set_chan()====ch:1
[   28.270060] =====>rtl8192_set_chan()====ch:2
[   28.390052] =====>rtl8192_set_chan()====ch:3
[   28.510056] =====>rtl8192_set_chan()====ch:4
[   28.630051] =====>rtl8192_set_chan()====ch:5
[   28.750050] =====>rtl8192_set_chan()====ch:6
[   28.870054] =====>rtl8192_set_chan()====ch:7
[   28.990051] =====>rtl8192_set_chan()====ch:8
[   29.110062] =====>rtl8192_set_chan()====ch:9
[   29.230030] =====>rtl8192_set_chan()====ch:10
[   29.350044] =====>rtl8192_set_chan()====ch:11
[   29.470110] =====>rtl8192_set_chan()====ch:12
[   29.590057] =====>rtl8192_set_chan()====ch:13
[   30.682946] =====>rtl8192_set_chan()====ch:1
[   30.800047] =====>rtl8192_set_chan()====ch:2
[   30.920027] =====>rtl8192_set_chan()====ch:3
[   31.040036] =====>rtl8192_set_chan()====ch:4
[   31.160036] =====>rtl8192_set_chan()====ch:5
[   31.280044] =====>rtl8192_set_chan()====ch:6
[   31.400032] =====>rtl8192_set_chan()====ch:7
[   31.520055] =====>rtl8192_set_chan()====ch:8
[   31.640026] =====>rtl8192_set_chan()====ch:9
[   31.760053] =====>rtl8192_set_chan()====ch:10
[   31.880066] =====>rtl8192_set_chan()====ch:11
[   32.000110] =====>rtl8192_set_chan()====ch:12
[   32.120070] =====>rtl8192_set_chan()====ch:13
[   32.241255] ===>rtllib_start_scan()
[   32.241280] Linking with dlink,channel:3, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x416
[   32.241287] Linking with dlink,channel:3, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x416
[   32.241331] ===>rtllib_associate_procedure_wq(), chan:3
[   32.241333] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   32.241335] =====>rtl8192_set_chan()====ch:3
[   32.253490] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   32.258663] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[   32.258665] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[   32.258667] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[   32.258669] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[   32.258671] Associated successfully
[   32.258672] normal associate
[   32.258678] Using G rates:108
[   32.258680] Successfully associated, ht enabled
[   32.258682] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   32.258683] =====>rtl8192_set_chan()====ch:3
[   32.268795] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   32.268798] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[   32.282835] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.300334] DHCP pkt src port:68, dest port:67!!
[   32.970284] dm_check_edca_turbo():iot peer is unknown, bssid:00:1e:58:38:a3:01
[   33.030843] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   33.090643] =====>rtl8192_set_chan()====ch:1
[   33.210070] =====>rtl8192_set_chan()====ch:2
[   33.330077] =====>rtl8192_set_chan()====ch:3
[   33.450127] =====>rtl8192_set_chan()====ch:4
[   33.570093] =====>rtl8192_set_chan()====ch:5
[   33.690079] =====>rtl8192_set_chan()====ch:6
[   33.810067] =====>rtl8192_set_chan()====ch:7
[   33.930066] =====>rtl8192_set_chan()====ch:8
[   34.050069] =====>rtl8192_set_chan()====ch:9
[   34.170066] =====>rtl8192_set_chan()====ch:10
[   34.290076] =====>rtl8192_set_chan()====ch:11
[   34.410091] =====>rtl8192_set_chan()====ch:12
[   34.530100] =====>rtl8192_set_chan()====ch:13
[   34.650060] =====>rtl8192_set_chan()====ch:3
[   34.660264] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   34.660269] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[   35.039940] rtllib: TsStartAddBaProcess()==>BA timer is already added
[   35.075841] rtllib: TsStartAddBaProcess()==>BA timer is already added
[   35.092520] rtllib: TsStartAddBaProcess()==>BA timer is already added
[   35.100034] ====>to send ADDBAREQ!!!!!
[   35.102125] ====>rx ADDBARSP from :00:1e:58:38:a3:01
[   35.130024] ====>to send ADDBAREQ!!!!!
[   35.132043] ====>rx ADDBARSP from :00:1e:58:38:a3:01
[   37.000480] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   37.060200] =====>rtl8192_set_chan()====ch:1
[   37.180060] =====>rtl8192_set_chan()====ch:2
[   37.300052] =====>rtl8192_set_chan()====ch:3
[   37.420059] =====>rtl8192_set_chan()====ch:4
[   37.540056] =====>rtl8192_set_chan()====ch:5
[   37.660047] =====>rtl8192_set_chan()====ch:6
[   37.780040] =====>rtl8192_set_chan()====ch:7
[   37.900053] =====>rtl8192_set_chan()====ch:8
[   38.020060] =====>rtl8192_set_chan()====ch:9
[   38.140031] =====>rtl8192_set_chan()====ch:10
[   38.260060] =====>rtl8192_set_chan()====ch:11
[   38.380059] =====>rtl8192_set_chan()====ch:12
[   38.500069] =====>rtl8192_set_chan()====ch:13
[   38.620058] =====>rtl8192_set_chan()====ch:3
[   38.630264] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   38.630268] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[   42.700041] wlan0: no IPv6 routers present
[   77.006939] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   77.060185] =====>rtl8192_set_chan()====ch:1
[   77.180069] =====>rtl8192_set_chan()====ch:2
[   77.300055] =====>rtl8192_set_chan()====ch:3
[   77.420078] =====>rtl8192_set_chan()====ch:4
[   77.540065] =====>rtl8192_set_chan()====ch:5
[   77.660076] =====>rtl8192_set_chan()====ch:6
[   77.780059] =====>rtl8192_set_chan()====ch:7
[   77.910073] =====>rtl8192_set_chan()====ch:8
[   78.040059] =====>rtl8192_set_chan()====ch:9
[   78.160057] =====>rtl8192_set_chan()====ch:10
[   78.280065] =====>rtl8192_set_chan()====ch:11
[   78.403216] =====>rtl8192_set_chan()====ch:12
[   78.520054] =====>rtl8192_set_chan()====ch:13
[   78.640084] =====>rtl8192_set_chan()====ch:3
[   78.650290] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   78.650295] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  128.487316] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  137.007180] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  137.007420] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  137.060566] =====>rtl8192_set_chan()====ch:1
[  137.180159] =====>rtl8192_set_chan()====ch:2
[  137.300091] =====>rtl8192_set_chan()====ch:3
[  137.420170] =====>rtl8192_set_chan()====ch:4
[  137.540206] =====>rtl8192_set_chan()====ch:5
[  137.660215] =====>rtl8192_set_chan()====ch:6
[  137.780091] =====>rtl8192_set_chan()====ch:7
[  137.900098] =====>rtl8192_set_chan()====ch:8
[  138.020104] =====>rtl8192_set_chan()====ch:9
[  138.140096] =====>rtl8192_set_chan()====ch:10
[  138.260100] =====>rtl8192_set_chan()====ch:11
[  138.384664] =====>rtl8192_set_chan()====ch:12
[  138.500150] =====>rtl8192_set_chan()====ch:13
[  138.620162] =====>rtl8192_set_chan()====ch:3
[  138.630463] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  138.630473] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  149.079250] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  178.585664] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  184.323820] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  188.829339] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  208.398367] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  217.002872] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  217.060192] =====>rtl8192_set_chan()====ch:1
[  217.180220] =====>rtl8192_set_chan()====ch:2
[  217.300111] =====>rtl8192_set_chan()====ch:3
[  217.420156] =====>rtl8192_set_chan()====ch:4
[  217.540231] =====>rtl8192_set_chan()====ch:5
[  217.660126] =====>rtl8192_set_chan()====ch:6
[  217.780164] =====>rtl8192_set_chan()====ch:7
[  217.900123] =====>rtl8192_set_chan()====ch:8
[  218.020145] =====>rtl8192_set_chan()====ch:9
[  218.140156] =====>rtl8192_set_chan()====ch:10
[  218.260143] =====>rtl8192_set_chan()====ch:11
[  218.380145] =====>rtl8192_set_chan()====ch:12
[  218.500072] =====>rtl8192_set_chan()====ch:13
[  218.620068] =====>rtl8192_set_chan()====ch:3
[  218.630248] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  218.630253] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  258.495665] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  261.875147] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  308.574918] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  317.007355] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  317.060212] =====>rtl8192_set_chan()====ch:1
[  317.180135] =====>rtl8192_set_chan()====ch:2
[  317.300108] =====>rtl8192_set_chan()====ch:3
[  317.420142] =====>rtl8192_set_chan()====ch:4
[  317.540082] =====>rtl8192_set_chan()====ch:5
[  317.660144] =====>rtl8192_set_chan()====ch:6
[  317.780060] =====>rtl8192_set_chan()====ch:7
[  317.900076] =====>rtl8192_set_chan()====ch:8
[  318.030060] =====>rtl8192_set_chan()====ch:9
[  318.150066] =====>rtl8192_set_chan()====ch:10
[  318.270091] =====>rtl8192_set_chan()====ch:11
[  318.390090] =====>rtl8192_set_chan()====ch:12
[  318.510145] =====>rtl8192_set_chan()====ch:13
[  318.630147] =====>rtl8192_set_chan()====ch:3
[  318.640359] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  318.640369] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  321.270062] too short to sleep::854, 84f, 5
[  338.885311] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  358.134974] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  368.887943] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  378.717193] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  388.956982] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  398.991043] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  419.162823] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  429.199955] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  437.007193] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  437.007432] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  437.060198] =====>rtl8192_set_chan()====ch:1
[  437.180226] =====>rtl8192_set_chan()====ch:2
[  437.300138] =====>rtl8192_set_chan()====ch:3
[  437.420165] =====>rtl8192_set_chan()====ch:4
[  437.540066] =====>rtl8192_set_chan()====ch:5
[  437.660473] =====>rtl8192_set_chan()====ch:6
[  437.780156] =====>rtl8192_set_chan()====ch:7
[  437.900146] =====>rtl8192_set_chan()====ch:8
[  438.020099] =====>rtl8192_set_chan()====ch:9
[  438.140056] =====>rtl8192_set_chan()====ch:10
[  438.260089] =====>rtl8192_set_chan()====ch:11
[  438.380146] =====>rtl8192_set_chan()====ch:12
[  438.500195] =====>rtl8192_set_chan()====ch:13
[  438.620104] =====>rtl8192_set_chan()====ch:3
[  438.630321] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  438.630332] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  464.322236] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  470.976907] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  473.330057] too short to sleep::43ba, 43b5, 5
[  489.919653] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  499.136617] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  509.784471] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  520.945804] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  529.138586] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  550.847377] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  557.003887] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  557.004130] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  557.060149] =====>rtl8192_set_chan()====ch:1
[  557.180136] =====>rtl8192_set_chan()====ch:2
[  557.300080] =====>rtl8192_set_chan()====ch:3
[  557.420056] =====>rtl8192_set_chan()====ch:4
[  557.540111] =====>rtl8192_set_chan()====ch:5
[  557.660084] =====>rtl8192_set_chan()====ch:6
[  557.780079] =====>rtl8192_set_chan()====ch:7
[  557.900471] =====>rtl8192_set_chan()====ch:8
[  558.020059] =====>rtl8192_set_chan()====ch:9
[  558.140162] =====>rtl8192_set_chan()====ch:10
[  558.260151] =====>rtl8192_set_chan()====ch:11
[  558.380100] =====>rtl8192_set_chan()====ch:12
[  558.500078] =====>rtl8192_set_chan()====ch:13
[  558.620165] =====>rtl8192_set_chan()====ch:3
[  558.630380] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  558.630390] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  599.791940] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  609.316032] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  629.794380] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  649.659510] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  659.899087] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  677.008070] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  677.008313] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  677.060292] =====>rtl8192_set_chan()====ch:1
[  677.180041] =====>rtl8192_set_chan()====ch:2
[  677.300118] =====>rtl8192_set_chan()====ch:3
[  677.420074] =====>rtl8192_set_chan()====ch:4
[  677.540066] =====>rtl8192_set_chan()====ch:5
[  677.660150] =====>rtl8192_set_chan()====ch:6
[  677.780053] =====>rtl8192_set_chan()====ch:7
[  677.900075] =====>rtl8192_set_chan()====ch:8
[  678.020056] =====>rtl8192_set_chan()====ch:9
[  678.140057] =====>rtl8192_set_chan()====ch:10
[  678.260165] =====>rtl8192_set_chan()====ch:11
[  678.380071] =====>rtl8192_set_chan()====ch:12
[  678.500069] =====>rtl8192_set_chan()====ch:13
[  678.620072] =====>rtl8192_set_chan()====ch:3
[  678.630290] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  678.630301] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  689.799351] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  699.834309] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  709.359530] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  730.041283] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  740.179791] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  749.804210] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  770.283647] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  780.318568] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  790.353574] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  797.007442] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  797.007683] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  797.060281] =====>rtl8192_set_chan()====ch:1
[  797.180138] =====>rtl8192_set_chan()====ch:2
[  797.300154] =====>rtl8192_set_chan()====ch:3
[  797.420168] =====>rtl8192_set_chan()====ch:4
[  797.540158] =====>rtl8192_set_chan()====ch:5
[  797.660156] =====>rtl8192_set_chan()====ch:6
[  797.780040] =====>rtl8192_set_chan()====ch:7
[  797.900048] =====>rtl8192_set_chan()====ch:8
[  798.020091] =====>rtl8192_set_chan()====ch:9
[  798.140057] =====>rtl8192_set_chan()====ch:10
[  798.260097] =====>rtl8192_set_chan()====ch:11
[  798.380151] =====>rtl8192_set_chan()====ch:12
[  798.500094] =====>rtl8192_set_chan()====ch:13
[  798.620113] =====>rtl8192_set_chan()====ch:3
[  798.630330] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  798.630340] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  798.633266] ====>rx ADDBAREQ from :00:1e:58:38:a3:01
[  798.633274] ====>to send ADDBARSP
[  810.423300] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  820.356206] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData

```

thank you for your time and if you need any other information please let me know

---

### Post by praseodym on 2011-08-22
Hello,

what encryption mode do you use? Mixed WPA/WPA2-encryption often causes problems with the network-manager. Better use WPA2-AES instead.

---

### Post by lemeiux1 on 2011-08-22
> **praseodym said:**
> Hello,
 
what encryption mode do you use? Mixed WPA/WPA2-encryption often causes problems with the network-manager. Better use WPA2-AES instead.
 
I actually use an unsecured network at home

---

### Post by praseodym on 2011-08-22
Thats bad, no chance to change the settings? Don't forget to change the settings in the network-manager applet, better delete the current connection after changing the encryption mode and set up a new one using "WPA & WPA2 Personal". What hardware do you use?

```
lspci -nnk | grep -iA2 net
lsusb
```
This

> Power Management period:0us
is strange, try

```
sudo iwconfig wlan0 power off
iwconfig #control
```

---

### Post by lemeiux1 on 2011-08-22
> **praseodym said:**
> Thats bad, no chance to change the settings? Don't forget to change the settings in the network-manager applet, better delete the current connection after changing the encryption mode and set up a new one using "WPA & WPA2 Personal". What hardware do you use?

```
lspci -nnk | grep -iA2 net
lsusb
```This


is strange, try

```
sudo iwconfig wlan0 power off
iwconfig #control
```

Ok so I didnt change the settings for encryption, but I ran the codes you gave me:

lspci -nnk | grep -A2 net

```
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Lenovo Device [17aa:2131]
    Kernel driver in use: r8169
```

lsusb

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 17ef:4811 Lenovo Integrated Webcam [R5U877]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

iw config  # control

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"dlink"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:1E:58:38:A3:01   
          Bit Rate=135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

let me know if you see anything strange, thanks again

---

### Post by lemeiux1 on 2011-08-22
Ok even stranger, I just noticed that when the signal drops on my laptop my other computer (desktop) all of the sudden has conection problems!  But as soon as I turn off my laptop my desktop is fine again!

---

### Post by praseodym on 2011-08-22
Firmware of the router is up-to-date? MAC-adress filter is off/allows new clients?

I miss the wireless card:

```
lspci -nnk | grep -iA2 net
```
The named one is LAN.

---

### Post by lemeiux1 on 2011-08-22
> **praseodym said:**
> Firmware of the router is up-to-date? MAC-adress filter is off/allows new clients?
 
I miss the wireless card:
 
```
lspci -nnk | grep -iA2 net
```
The named one is LAN.
 
firmware is up to date and MAC address filter is off.  Im not sure what you mean about the wireless card.  The wireless card is Realtek RTL8191SEvB no?  I already put the result of that code in my previous post

---

### Post by praseodym on 2011-08-23
This

> 08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Lenovo Device [17aa:2131]
    Kernel driver in use: r8169
is your LAN-card. The wireless device should also be shown with "lspci", but it doesnt, though an interface (wlan0) is there. Maybe:

```
lspci -nnk | grep -iA2 Realtek
```

---

### Post by lemeiux1 on 2011-08-24
[FONT=monospace]lspci -nnk | grep -iA2 Realtek

[/FONT]```
8:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Lenovo Device [17aa:2131]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:e020]
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci
```

My other machine is working fine so im guesing it has something to do with this card, maybe a different driver?
[FONT=monospace]
[/FONT]

---

### Post by praseodym on 2011-08-25
There it is. This card normally works well.

Please show the following outputs:

```
lsmod
dmesg | grep r8
rfkill list
sudo iwlist scan
```

---

### Post by lemeiux1 on 2011-08-25
> **praseodym said:**
> There it is. This card normally works well.

Please show the following outputs:

```
lsmod
dmesg | grep r8
rfkill list
sudo iwlist scan
```

lsmod

```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
joydev                 17606  0 
fglrx                2739144  51 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
thinkpad_acpi          81587  0 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
r8192se_pci           524220  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
btusb                  18600  2 
sp5100_tco             13744  0 
cfg80211              178528  1 r8192se_pci
psmouse                73535  0 
videodev               82052  1 uvcvideo
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,thinkpad_acpi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13303  0 
edac_core              53845  0 
shpchp                 37297  0 
v4l2_compat_ioctl32    17078  1 videodev
serio_raw              13166  0 
soundcore              12680  1 snd
edac_mce_amd           23464  0 
k10temp                13119  0 
lp                     17825  0 
nvram                  14419  1 thinkpad_acpi
video                  19438  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  1 
libahci                26642  1 ahci
r8169                  48022  0 
```

dmesg | grep r8

```
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800afc00000 s84416 r8192 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
[    1.808774] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.808799] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.808833] r8169 0000:08:00.0: setting latency timer to 64
[    1.808876] r8169 0000:08:00.0: irq 43 for MSI/MSI-X
[    1.809259] r8169 0000:08:00.0: eth0: RTL8168d/8111d at 0xffffc90001072000, 60:eb:69:af:49:6b, XID 081000c0 IRQ 43
[   14.017207] r8169 0000:08:00.0: eth0: link down

```

rfkill list

```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:38:A3:01
                    ESSID:"dlink"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:3
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=97/100  Signal level=-51 dBm  Noise level=-118 dBm
                    IE: Unknown: DD0E0050F204104A0001101044000101
                    Extra: Last beacon: 1ms ago
          Cell 02 - Address: 06:72:CF:21:47:DD
                    ESSID:"montana"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-49 dBm  Noise level=-93 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 81ms ago
          Cell 03 - Address: 00:16:B6:04:68:74
                    ESSID:"linksys"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=50/100  Signal level=-49 dBm  Noise level=-95 dBm
                    Extra: Last beacon: 66ms ago
          Cell 04 - Address: 00:23:69:DE:22:CE
                    ESSID:"kaitlyn"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-49 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010002369FFFFFFDE22FFFFFFCF00000000103C000103
                    Extra: Last beacon: 80ms ago
          Cell 05 - Address: C0:3F:0E:59:C4:04
                    ESSID:"ckbtjbleb"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-48 dBm  Noise level=-93 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Extra: Last beacon: 87ms ago
          Cell 06 - Address: 06:72:CF:21:44:01
                    ESSID:"montana"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-47 dBm  Noise level=-93 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 101ms ago
```

and im not sure if this helps but when the internet dies on this machine, all of the other machines in my house cant connect either, and as soon as I power off the machine the others connections are fine again

---

### Post by praseodym on 2011-08-26
First, no encryption is pretty bad.

Second, does you router only broadcast in N-mode? Can you change to b/g/n?

---

### Post by lemeiux1 on 2011-08-28
> **praseodym said:**
> First, no encryption is pretty bad.

Second, does you router only broadcast in N-mode? Can you change to b/g/n?

Ok so I changed my settings to just g mode and it seems to be working now (still early to tell but I havent had a drop yet) Now my question is since N is faster is there a way to make it work with N?

---

### Post by praseodym on 2011-08-28
The network you want to connect to is "dlink"? Try WPA2-encryption if possible and set the rate:

```
sudo iwconfig wlan0 rate auto
sudo service network-manager restart
iwconfig #control
```
"dlink" shows 130 Mb/s in "sudo iwlist scan", which is the maximum in the 2.4 GHz-band. Full-Draft-N (300 Mb/s) only works in the 5 GHz-band. Check with
```
iwlist chan
```
which channels are possible. Change channels in you router interface. If you have no 5GHz-band change to channel 1.

---

