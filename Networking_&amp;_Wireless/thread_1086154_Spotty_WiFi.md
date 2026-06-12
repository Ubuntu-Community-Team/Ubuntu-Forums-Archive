---
title: "Spotty WiFi"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by camberiu on 2009-03-03
I've just started using Ubuntu and overall I am very impressed with the OS and really looking foward to dumping Windows for good and using Linux instead. However, I am having some serious WiFi issues that until resolved, will prevent me from having Ubuntu as my primary OS.

The issue is that for some bizare reason, my Wifi connection at home when using Ubuntu is very spotty. Right after boot, the WiFi connection works extremely well. However, over time, the drops become more frequent. The connection gets dropped and restored automatically, with this cycle happening every few minutes. I've tried disabling ht IPV6 protocal on Ubuntu, but without any improvement. My home WiFi uses WPA encryption and I never experienced similar problems with the MacOS, Android phone, Windows machine or even the Playstation portable, so it has to be an Ubuntu/driver issue. Here is some more information. Any assistance would be greatly appeciated.

OS - Ubuntu 8.10 32-bit
Machine - Compaq c714NR laptop

**$lspci**
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

**$iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

**$lsmod**
Module                  Size  Used by
usbhid                 35840  0 
hid                    50560  1 usbhid
michael_mic            10496  2 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
i915                   38528  2 
drm                    86056  3 i915
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ipv6                  263972  14 
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
container              11520  0 
pci_slot               12680  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         384176  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
evdev                  17696  12 
snd_rawmidi            29824  1 snd_seq_midi
serio_raw              13444  0 
pcspkr                 10624  0 
psmouse                45200  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

**$dmesg**
[    4.337492]  sda1 sda2 < sda5 >
[    4.363970] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.369526] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.369533] Uniform CD-ROM driver Revision: 3.20
[    4.369671] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.635320] PM: Starting manual resume from disk
[    4.635325] PM: Resume from partition 8:5
[    4.635327] PM: Checking hibernation image.
[    4.635595] PM: Resume from disk failed.
[    4.698529] kjournald starting.  Commit interval 5 seconds
[    4.698566] EXT3-fs: mounted filesystem with ordered data mode.
[   10.324113] usb 2-1: device descriptor read/64, error -84
[   10.540107] usb 2-1: new full speed USB device using uhci_hcd and address 4
[   10.817063] usb 2-1: device descriptor read/64, error -84
[   11.001546] udevd version 124 started
[   11.462885] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.484301] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.549221] Linux agpgart interface v0.103
[   11.597815] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   11.598227] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   11.613175] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[   11.721168] iTCO_vendor_support: vendor-support=0
[   11.736211] ACPI: AC Adapter [AC] (on-line)
[   11.745183] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   11.745324] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0460)
[   11.745470] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.840256] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   11.868058] ACPI: Power Button (FF) [PWRF]
[   11.868215] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   11.900034] ACPI: Power Button (CM) [PWRB]
[   11.900142] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   11.900252] ACPI: Lid Switch [LID0]
[   11.900321] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   11.936036] ACPI: Sleep Button (CM) [SLPB]
[   12.186118] ACPI: Battery Slot [BAT0] (battery present)
[   12.186320] ACPI: WMI: Mapper loaded
[   12.263334] ieee80211_crypt: registered algorithm 'NULL'
[   12.267456] wl: module license 'unspecified' taints kernel.
[   12.279645] acpi device:17: registered as cooling_device2
[   12.280188] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14/input/input6
[   12.300030] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   12.309115] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.309126] wl 0000:01:00.0: setting latency timer to 64
[   12.361224] ieee80211_crypt: registered algorithm 'TKIP'
[   12.361465] eth1: Broadcom BCM4311 802.11 Wireless Controller 5.10.27.12
[   12.501541] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.047165] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.047203] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.070568] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   13.147149] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   13.553052] usb 2-1: device descriptor read/64, error -84
[   13.769043] usb 2-1: new full speed USB device using uhci_hcd and address 5
[   14.532097] usb 2-1: device not accepting address 5, error -84
[   14.644092] usb 2-1: new full speed USB device using uhci_hcd and address 6
[   14.967409] lp: driver loaded but no devices found
[   15.202278] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k
[   15.835367] EXT3 FS on sda1, internal journal
[   16.629036] usb 2-1: device not accepting address 6, error -84
[   16.629062] hub 2-0:1.0: unable to enumerate USB device on port 1
[   17.128759] type=1505 audit(1236124552.350:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3964
[   17.205419] type=1505 audit(1236124552.429:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=3969
[   17.430691] type=1505 audit(1236124552.653:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3973
[   17.431041] type=1505 audit(1236124552.653:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3973
[   17.673968] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.434266] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.536270] apm: BIOS not found.
[   19.756387] ppdev: user-space parallel port driver
[   21.749555] NET: Registered protocol family 10
[   21.750765] lo: Disabled Privacy Extensions
[   23.240665] Bluetooth: Core ver 2.13
[   23.241709] NET: Registered protocol family 31
[   23.241719] Bluetooth: HCI device and connection manager initialized
[   23.241727] Bluetooth: HCI socket layer initialized
[   23.285242] Bluetooth: L2CAP ver 2.11
[   23.285253] Bluetooth: L2CAP socket layer initialized
[   23.313110] Bluetooth: SCO (Voice Link) ver 0.6
[   23.313118] Bluetooth: SCO socket layer initialized
[   23.335397] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.335404] Bluetooth: BNEP filters: protocol multicast
[   23.380745] Bridge firewalling registered
[   23.391662] Bluetooth: RFCOMM socket layer initialized
[   23.392360] Bluetooth: RFCOMM TTY layer initialized
[   23.392366] Bluetooth: RFCOMM ver 1.10
[   23.436060] usb 2-1: new full speed USB device using uhci_hcd and address 7
[   24.316061] usb 2-1: device descriptor read/64, error -84
[   24.620070] usb 2-1: device descriptor read/64, error -84
[   24.837056] usb 2-1: new full speed USB device using uhci_hcd and address 8
[   27.089052] usb 2-1: device descriptor read/64, error -84
[   27.541014] eth0: link down
[   27.541679] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.631902] NET: Registered protocol family 17
[   27.656928] [drm] Initialized drm 1.1.0 20060810
[   27.666461] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.666475] pci 0000:00:02.0: setting latency timer to 64
[   27.668858] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   33.569019] eth1: no IPv6 routers present
[   42.305086] usb 2-1: device descriptor read/64, error -110
[   42.521069] usb 2-1: new full speed USB device using uhci_hcd and address 9
[   52.929033] usb 2-1: device not accepting address 9, error -110
[   53.041047] usb 2-1: new full speed USB device using uhci_hcd and address 10
[   60.955746] CPU0 attaching NULL sched-domain.
[   60.955768] CPU1 attaching NULL sched-domain.
[   60.957643] CPU0 attaching sched-domain:
[   60.957654]  domain 0: span 0-1 level MC
[   60.957661]   groups: 0 1
[   60.957675] CPU1 attaching sched-domain:
[   60.957680]  domain 0: span 0-1 level MC
[   60.957687]   groups: 1 0
[   63.448083] usb 2-1: device not accepting address 10, error -110
[   63.448126] hub 2-0:1.0: unable to enumerate USB device on port 1
[  101.288198] usb 4-3: new high speed USB device using ehci_hcd and address 3
[  101.422632] usb 4-3: configuration #1 chosen from 1 choice
[  101.423472] hub 4-3:1.0: USB hub found
[  101.423776] hub 4-3:1.0: 4 ports detected
[  101.704440] usb 4-3.4: new high speed USB device using ehci_hcd and address 4
[  101.799634] usb 4-3.4: configuration #1 chosen from 1 choice
[  101.799940] hub 4-3.4:1.0: USB hub found
[  101.800478] hub 4-3.4:1.0: 4 ports detected
[  102.088420] usb 4-3.4.4: new low speed USB device using ehci_hcd and address 5
[  102.185514] usb 4-3.4.4: configuration #1 chosen from 1 choice
[  102.306890] usbcore: registered new interface driver hiddev
[  102.310411] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.7/usb4/4-3/4-3.4/4-3.4.4/4-3.4.4:1.0/input/input10
[  102.313180] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.7-3.4.4
[  102.313212] usbcore: registered new interface driver usbhid
[  102.313217] usbhid: v2.6:USB HID core driver
[  414.364899] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  414.367068] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  417.949425] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  428.399701] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  428.400969] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  451.024104] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  463.927274] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  469.763564] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  470.685181] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  471.714621] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  471.715460] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  472.733213] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  472.734115] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  473.654930] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  473.757217] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  474.678832] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  474.781237] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  475.703754] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  476.727816] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  480.926965] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  481.949339] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  482.875315] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  483.894999] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  484.922342] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  485.943185] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  492.091251] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  495.056835] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  496.085766] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  498.236504] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  504.376861] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  507.140383] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  508.168029] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  509.085706] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  510.109723] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  511.133744] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  511.134594] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  512.056421] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  518.608980] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  519.633016] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  520.554669] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  521.581643] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  522.603835] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  523.627927] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  523.941004] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  558.346452] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  559.679625] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  571.243352] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  583.634316] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  583.941415] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  584.453523] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  585.170618] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  602.885361] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  603.807555] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  604.830945] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  605.855002] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  606.879601] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  607.800567] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  609.952588] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  610.770660] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  611.487482] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  618.450370] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  623.469647] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  628.080151] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  629.100113] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  630.124123] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  631.148152] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  631.362563] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  643.437943] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  643.440613] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  643.948489] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  691.463052] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  703.955450] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  712.558461] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  713.478739] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  714.504066] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  715.526795] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  716.554355] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  723.723344] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  724.651561] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  725.768746] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  727.714107] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  728.736708] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  729.761384] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  732.627808] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  737.748270] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  737.749907] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  741.743031] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  742.769635] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  744.715195] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  746.767177] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  748.716947] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  750.762732] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  751.578923] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  751.778165] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  752.699059] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  753.011259] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  753.927414] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  754.765927] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  754.768509] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  754.777652] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  754.779203] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  754.781840] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  754.958312] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  755.777213] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  756.694162] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  756.999293] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  757.725993] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  757.926740] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  759.765652] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  761.711201] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  763.656904] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  763.860406] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  765.704922] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  765.706462] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  767.649551] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  767.651011] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  767.751538] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  769.697542] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  769.699070] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  771.644105] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  771.645540] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  773.691177] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  773.693565] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  773.699158] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  773.701862] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  773.704407] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  775.433903] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  777.479548] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  778.503561] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  779.531014] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  780.552984] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  781.473163] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  782.502586] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  792.742023] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  794.274967] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  823.867301] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  843.841046] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  844.757286] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  846.806084] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  849.160743] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  871.791065] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  872.917982] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  877.833081] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  889.814417] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  890.741406] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  891.759732] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  892.790469] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  893.809154] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  906.505059] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  909.171442] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  931.900529] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  933.538983] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  934.460567] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  935.484570] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  936.508563] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  937.532681] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  937.839836] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  938.454235] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  947.772744] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  948.796756] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  949.820770] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  950.742377] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  951.766389] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  954.736027] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  955.760036] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  956.784046] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  957.807991] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  958.729666] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  959.753678] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  969.174586] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  979.622342] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  992.010047] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[  997.847275] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1003.584513] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1003.685256] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1004.503390] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1004.605348] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1004.653753] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1004.655252] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1004.665619] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1005.220330] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1005.635012] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1005.734974] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1006.246673] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1006.653349] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1006.755958] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1007.682525] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1008.190943] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1010.238903] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1012.187110] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1012.599989] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1014.137331] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1014.138855] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1014.141457] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1016.184587] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1016.186010] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1018.122816] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1018.124368] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1020.170912] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1020.172392] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1022.116536] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1022.118865] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1022.121501] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1022.124073] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1022.126580] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1022.732386] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1029.079230] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1034.711686] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1034.719195] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1035.428486] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1036.148823] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1052.119527] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1068.606823] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1069.630901] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1070.654101] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1071.575701] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1072.599716] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1072.702116] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1073.623729] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1078.334498] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1079.358159] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1080.386520] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1081.406247] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1082.327973] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1083.351828] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1084.789568] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1085.707100] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1087.755086] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1088.779091] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1091.543993] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1093.489584] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1094.513580] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1095.537615] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1096.561616] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1098.509763] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1099.428817] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1101.476831] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1112.228940] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1114.379411] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1115.300986] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1116.325034] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1117.349050] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1118.373030] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1119.294598] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1132.811619] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1163.327805] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1164.351160] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1165.375183] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1166.399468] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1167.423195] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1167.730397] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1168.345455] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1172.338455] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1188.934265] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1191.180229] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1192.103273] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1192.921147] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1194.154008] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1195.173908] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1196.201522] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1207.154830] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1208.079969] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1209.100458] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1210.124468] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1211.148476] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1232.447908] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1248.935272] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1253.030534] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1272.077139] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1273.101150] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1274.125169] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1274.739567] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1275.149179] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1275.151742] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1275.154805] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1275.157412] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1275.662426] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1276.071084] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1276.685337] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1277.094797] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1277.710117] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1278.733214] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1279.654766] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1292.557302] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1304.753423] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1304.754823] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1304.763326] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1304.764668] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1304.765744] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1305.767404] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1306.689129] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1306.696575] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1306.698936] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1306.699963] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1308.737141] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1308.739614] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1311.708942] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1313.653802] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1313.656058] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1315.702034] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1315.704107] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1315.705652] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1317.647122] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1317.648628] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1317.650198] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1319.695174] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1319.696607] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1319.698124] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1321.640712] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1321.642333] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1321.645315] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1321.647911] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1321.650633] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1321.653168] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1323.688817] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1327.271325] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1328.192954] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1329.216958] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1330.242286] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1331.264985] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1334.236220] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1334.237595] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1334.238723] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1352.666817] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1368.948874] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1373.249434] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1392.194425] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1393.217989] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1394.242257] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1395.163245] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1396.187250] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1396.701009] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1397.211284] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1404.891372] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1405.812988] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1406.837331] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1407.861010] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1408.885011] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1409.806564] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1428.858772] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1433.359363] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1458.857350] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1459.880907] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1460.802518] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1469.711503] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1470.735253] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1471.759554] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1472.680902] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1472.885670] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1473.704912] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1474.729339] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1475.548125] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1476.572145] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1477.596507] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1478.620171] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1479.541771] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1488.962679] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1493.468477] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1498.691252] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1520.298230] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1521.321451] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1522.243035] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1523.267048] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1524.291463] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1532.995111] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1548.867312] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40
[ 1553.577768] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f1964b40



**$sudo lshw -C network**
*-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:a5:69:ed
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.0.183 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network

**$iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
[B]

$sudo /etc/init.d/networking restart[/B]
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.

---

### Post by camberiu on 2009-03-04
No one can take a stab at it? Oh well, pity, since I really wanted to like and use Ubuntu. I guess Windows still has a role to fulfill in the world.  I'll look forward to the day when Ubuntu will be ready to be used by the masses.

---

