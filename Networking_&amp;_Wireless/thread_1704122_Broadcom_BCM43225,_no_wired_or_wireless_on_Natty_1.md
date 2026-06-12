---
title: "Broadcom BCM43225, no wired or wireless on Natty 11.04"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by megsona on 2011-03-10
Hi forums, here's yet another non-working wireless issue for a Broadcom BCM43225 chip, neither wired nor wireless works at present.

I've followed the two threads below as they seem to have a very similar setup but I've not managed to get mine resolved. The Broadcom STA drivers didn't work for me so I'm going down BRCM80211 route.
[http://ubuntuforums.org/showthread.php?t=1593354]("http://ubuntuforums.org/showthread.php?t=1593354")
[http://ubuntuforums.org/showthread.php?t=1592044]("http://ubuntuforums.org/showthread.php?t=1592044")

I have an Acer Aspire 753 and am running Natty Alpha 3 on it (specifically because the newer kernel 2.6.38-5-generic supports the Sandy Bridge chipset in this machine). I had tried with 10.10 also and had the same wireless issues (but with additional Sandy Bridge problems with 'intel_ips')

I've got bcm43xx, wl, b43, ssb all blacklisted (perhaps I shouldn't?) and have added the firmware symbolic links in /lib/firmware/brcm

```
sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fw
sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw
```

as per this thread [URL="http://ubuntuforums.org/showthread.php?t=1617380"]http://ubuntuforums.org/showthread.php?t=1617380
[/URL]
I think I'm close to get it working but am falling at the last hurdle, if I run

```
sudo iwlist scan
```

I get

```
lo	interface doesn't support scanning

wlan0	Interface doesn't support scanning: Network is down
```

but it I run

```
sudo ifconfig wlan0 up
```

and then

```
sudo iwlist scan
```

I get

```
wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:DE:F8:A5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Bebox247865"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c0727206b
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B4265626F78323437383635
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180203F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:26:5A:A8:25:60
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Dharma5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005851871154
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 0007446861726D6135
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010006
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000008127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000

```

It's obviously working at some level but still nothing in Network Manager  which says 'wireless is disabled'.

Here's my output from various commands.

Really hope someone can help, thanks.#


lsmod
```

Module                  Size  Used by
usbhid                 41704  0 
hid                    77084  1 usbhid
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
brcm80211             690428  0 
i915                  446546  3 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 brcm80211
drm                   180083  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
i2c_algo_bit           13184  1 i915
psmouse                73312  0 
intel_ips              17769  0 
cfg80211              156212  2 brcm80211,mac80211
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
video                  18951  1 i915
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
acer_wmi               23123  0 
sparse_keymap          13666  1 acer_wmi
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
libahci                25548  1 ahci
```

rfkill list all
```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

lshw -C network
```
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 88:9f:fa:1d:0e:18
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-5-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:92400000-92403fff
```

ifconfig
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22080 (22.0 KB)  TX bytes:22080 (22.0 KB)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:1d:0e:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and the last chunk of dmesg
```
[    7.241571] usbcore: registered new interface driver uvcvideo
[    7.241574] USB Video Class driver (v1.0.0)
[    7.427136] [drm] Initialized drm 1.1.0 20060810
[    7.620311] cfg80211: World regulatory domain updated:
[    7.620317] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.620322] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.620327] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.620331] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.620335] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.620339] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.045455] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0400
[    8.101995] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    8.198908] brcm80211: module is from the staging directory, the quality is unknown, you have been warned.
[    8.211836] brcm80211 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.211849] brcm80211 0000:02:00.0: setting latency timer to 64
[    8.213086] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.213094] i915 0000:00:02.0: setting latency timer to 64
[    8.240139] i915 0000:00:02.0: irq 41 for MSI/MSI-X
[    8.240150] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.240153] [drm] Driver supports precise vblank timestamp query.
[    8.414524] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    8.491054] checking generic (80000000 300000) vs hw (80000000 10000000)
[    8.491061] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    8.491095] Console: switching to colour dummy device 80x25
[    8.491379] Console: switching to colour frame buffer device 170x48
[    8.491432] fb0: inteldrmfb frame buffer device
[    8.491434] drm: registered panic notifier
[    8.512013] acpi device:02: registered as cooling_device2
[    8.513148] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    8.513359] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    8.513888] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.969869] Found chip type AI (0x13a1a8d9)
[    8.982065] wlc_bmac_attach:: deviceid 0x4357 nbands 1 board 0xe021 macaddr: 88:9f:fa:1d:0e:18
[    8.982263] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    8.982267] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982271] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    8.982275] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982279] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    8.982283] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982286] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    8.982290] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982294] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    8.982298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982301] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    8.982306] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982309] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    8.982313] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982316] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    8.982320] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982324] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    8.982328] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982331] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    8.982335] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982339] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    8.982343] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982346] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    8.982350] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982354] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    8.982358] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    8.982361] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    8.982365] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.076317] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    9.077186] wl_set_hint: Sending country code US to MAC80211
[    9.077196] wl0: Broadcom BCM43xx 802.11 MAC80211 Driver (1.82.8.0) (Compiled at 17:19:21 on Feb 22 2011)
[    9.077428] cfg80211: Calling CRDA for country: US
[    9.101373] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    9.101380] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101385] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    9.101389] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101393] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    9.101397] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101400] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    9.101404] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101408] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    9.101412] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101415] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    9.101419] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101422] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    9.101426] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101430] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    9.101434] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101437] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    9.101441] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101445] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    9.101449] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101452] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    9.101456] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.101459] cfg80211: Disabling freq 2467 MHz
[    9.101462] cfg80211: Disabling freq 2472 MHz
[    9.101464] cfg80211: Disabling freq 2484 MHz
[    9.101469] cfg80211: Regulatory domain changed to country: US
[    9.101471] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.101475] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    9.101479] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[    9.101483] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.101487] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.101491] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.101495] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[    9.114721] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.114814] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[    9.115283] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.508704] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.688215] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   10.258054] hda_codec: ALC271X: BIOS auto-probing.
[   10.297276] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   10.297443] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.921065] type=1400 audit(1299747447.151:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=762 comm="apparmor_parser"
[   10.921980] type=1400 audit(1299747447.151:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=762 comm="apparmor_parser"
[   10.922479] type=1400 audit(1299747447.151:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=762 comm="apparmor_parser"
[   10.944245] type=1400 audit(1299747447.171:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=761 comm="apparmor_parser"
[   11.224416] type=1400 audit(1299747447.451:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=765 comm="apparmor_parser"
[   11.225738] type=1400 audit(1299747447.455:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=765 comm="apparmor_parser"
[   11.254779] type=1400 audit(1299747447.483:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=769 comm="apparmor_parser"
[   11.337231] ppdev: user-space parallel port driver
[   11.420191] audit_printk_skb: 9 callbacks suppressed
[   11.420196] type=1400 audit(1299747447.647:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=763 comm="apparmor_parser"
[   11.429750] type=1400 audit(1299747447.659:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=763 comm="apparmor_parser"
[   14.274862] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   14.378804] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   17.361320] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   17.366271] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   75.717712] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1222.408968] wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 69:65:6e:74:20:47
[ 1948.351323] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[ 1948.495032] EXT4-fs (sda6): re-mounted. Opts: commit=600
[ 2105.399019] usb 2-1.1: new low speed USB device using ehci_hcd and address 4
[ 2106.786675] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input10
[ 2106.786863] generic-usb 0003:046D:C00F.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1.1/input0
[ 2106.786890] usbcore: registered new interface driver usbhid
[ 2106.786893] usbhid: USB HID core driver
```

---

### Post by Oliver90001 on 2011-03-10
The reason for your malaise, well in my humble opinion is .......

use STA download from broadcom (hybrid-portsrc_x86_64-v5_100_82_38.tar.gz) don't use ubuntu's, it didn't work for me.........sure they'll fix soon

find all instances of it and delete 
check here :
/lib/modules/`uname -r`/updates/dkms/
/lib/modules/`uname -r`/kernel/drivers/net/wireless/

./configure and make(don't make install)....... copy resulting wl.ko into 
/lib/modules/`uname -r`/kernel/drivers/net/wireless/

depmod
modprobe -r wl
modprobe wl
/etc/init.d/networking restart
service network-manager restart

whats going on is your just reloading the buggy wl.ko , its a suggestion, sorry if Im wrong !

---

### Post by megsona on 2011-03-16
Thanks for responding, after much poking about I've found the solution.

As suspected the drivers were installed and working properly since they come with the 2.6.38 kernel however the "acer-wireless: soft blocked: yes" output of 'rfkill list all' was the clue.

Found these two posts

[https://bugzilla.redhat.com/show_bug.cgi?id=655371]("https://bugzilla.redhat.com/show_bug.cgi?id=655371")
[http://forums.opensuse.org/english/get-technical-help-here/pre-release-beta/453991-11-4-rc1-anyone-gotten-broadcom-brcm-driver-working-2.html]("http://forums.opensuse.org/english/get-technical-help-here/pre-release-beta/453991-11-4-rc1-anyone-gotten-broadcom-brcm-driver-working-2.html")

which pointed to acer-wmi module being loaded and causing the fault.

As soon as I did a 'sudo modprobe -r acer-wmi' my wireless sprang into life. At last!

I've since blacklisted the module and all seems well, the wifi LED is not lit but I can live with that.

Hope this helps any other Broadcom + Acer unfortunates out there.

---

### Post by rschauer on 2011-03-20
> **megsona said:**
> 
[...] which pointed to acer-wmi module being loaded and causing the fault.

As soon as I did a 'sudo modprobe -r acer-wmi' my wireless sprang into life. At last!

I've since blacklisted the module and all seems well, the wifi LED is not lit but I can live with that.


Thank you!

I recently got a 7551g, and had the wireless working fine with the proprietary drivers from Ubuntu. However, the wireless was always disabled at boot. Blacklisting that module fixed it!

By the way, for those who don't feel like searching more (if you don't already know how), blacklist a module like so, at the terminal (replace "sudo vi" with "gksudo gedit" if you're not a masochist like me):

```
$ cd /etc/modprobe.d
$ sudo vi blacklist.conf

```

Add the new line "blacklist acer-wmi" (without quotes) to the end of the file.

Let me also note that my wi-fi LED works fine. If I turn it off with Fn+F3, the light goes out and wi-fi turns off, but network-manager still thinks it's enabled and continually attempts to reconnect. Fn+F3 again turns the light back on, and NM reconnects. No more than a minor annoyance to me, just wanted to point it out in case anyone else looks here for help.

Thanks again for posting the solution; been looking for weeks!

---

### Post by Takendown2 on 2011-04-08
Nevermid :P I got it working. :D

---

### Post by icelogic on 2011-04-11
megsona your amazing sudo modprobe -r acer-wmi did it for me too on  Acer Aspire AS7552G-6436 Notebook
Manufacturer Part Number	 LX.RCH02.004
Product Series	 7552G

atheros wireless finally works!

---

### Post by icelogic on 2011-04-12
[rschauer]("http://ubuntuforums.org/member.php?u=820408") thanks for your post too it was very helpful for a noob like me :)

---

### Post by rschauer on 2011-04-29
No problem, icelogic; glad it helped someone!

Since I had forgotten what I did to make this work when I installed Natty this morning, I ended up finding this page again while searching for the solution! What do you know...my own post helped me out! LOL

So, for the record:
1) This same solution worked for me in Natty.
2) Now, my wireless LED goes on and off when I enable/disable wireless, but Fn+F3 does not work at all anymore. *shrug* Again, doesn't bother me too much, but it would be nice if it worked properly.

---

### Post by rupert160 on 2011-05-04
Post #3 worked for me on my ACER 1830

---

### Post by ganil on 2011-06-09
> Post #3 worked for me on my ACER 1830

Same here!

---

### Post by Geeneeus1 on 2011-06-16
Hi - I am  new to Linux, so far I love it but there is one minor hiccup (resolved, thankfully, by this post).

I am lost on the blacklist thing.  When I reboot, the fix goes away.  I know I have to blacklist part of the code but I don't know how.  I also don't know how to "make" or "compile".  

Any suggestions are appreciated.  

Basics below:
Ubuntu 11.04
Acer 1403Z
Atheros AR8151

---

### Post by pieter_segers on 2011-07-20
Many many thanks!

been looking for hours! but the "sudo modprobe -r acer-wmi" does the trick.

Pieter

---

### Post by floggy on 2011-07-22
post #4 worked for me

ubuntu 11.04
acer aspire 1551-4650
lspci output: bc43225

---

### Post by mikerobinson on 2011-07-25
Note that in order to get the Broadcom Corporation BCM43225 card to work in kernels > 2.6.37 you will need to patch the kernel. Here is a link.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I'm still running 2.6.35 on Ubuntu 11.04 for this reason.

---

### Post by ace1011 on 2011-08-03
I had to BLACKLIST by doing the following and it took forever just to figure it out. I have an Acer Aspire 5745 running Ubuntu 11.04.     Open a terminal;     type: sudo nano /etc/modprobe.d/blacklist.conf;     enter your password;     on a blank line in the file type blacklist acer-wmi;     press control s to save;     press control x to exit;     restart you computer;     Uhg. What a mess.     PS don't forget the space between nano and /etc/modprobe.d/blacklist.conf

---

### Post by mikerobinson on 2011-08-03
I just upgraded the kernel to the latest version with KernelCheck and all is well again.

---

### Post by enricogiurin on 2011-10-03
Thanks for the post, it made my BCM43225 working on ubuntu 11.04

---

### Post by chaemil on 2011-11-02
Hi i have an acer notebook with this wireless card and ubuntu 11.10 on it. I have to download the 2.6.39 kernel but it wont work, or the connection isn't stable. is there a way to get it back working in the 11.10?

---

### Post by wildmanne39 on 2011-11-02
Hi, try this please:
```
sudo apt-get update
```
```
sudo apt-get install bcmwl-kernel-source
```
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
unplug wired connection and reboot.
Thank you

---

### Post by chaemil on 2011-11-02
and should i do this with the 2.6.39 kernel or the 3.x kernel?

---

### Post by wildmanne39 on 2011-11-02
Hi, the 3.0
Thank you

---

### Post by chaemil on 2011-11-03
Hi. So I've done this and i hope and believe that it will work again! The connection is now working and i will se how stable it will be. Thank you so much.

---

### Post by chaemil on 2011-11-03
and should i use the broadcom proprietary or the ubuntu's kernel driver?

---

### Post by wildmanne39 on 2011-11-03
Hi, you said it is working,so leave it as it is, the command you ran activated the driver in additional drivers if you mess with it you will end up with no internet again.
Thank you

---

### Post by chaemil on 2011-11-04
hi. i have the problem, again it's still disconnecting from the wifi AP. but after some time it will reconnect but it's unpredictable when!

---

### Post by wildmanne39 on 2011-11-04
Hi, please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
lsmod | grep wl
```
```
dmesg | grep wl | tail -n20
```
Run this following command while you can not connect and without a wired connection plugged in.
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan -e wpa -e etwork | tail -n55
```
Thank you

---

### Post by chaemil on 2011-11-06
hi. don't you think that it will be easier and better to put there the 2.6.35 kernel? where the wifi works? i've googled it somewhere

---

### Post by chaemil on 2011-11-06
but here's the output from

sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan -e wpa -e etwork | tail -n55

when the notebook can't connect

```

Nov  6 14:30:30 julinka-laptop NetworkManager[593]: <info>   hostname 'dhcppc0'
Nov  6 14:30:30 julinka-laptop NetworkManager[593]: <info>   nameserver '10.0.0.138'
Nov  6 14:30:30 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  6 14:30:30 julinka-laptop avahi-daemon[587]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.1.
Nov  6 14:30:30 julinka-laptop avahi-daemon[587]: New relevant interface wlan0.IPv4 for mDNS.
Nov  6 14:30:30 julinka-laptop avahi-daemon[587]: Registering new address record for 10.0.0.1 on wlan0.IPv4.
Nov  6 14:30:30 julinka-laptop kernel: [ 1551.817521] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
Nov  6 14:30:31 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  6 14:30:31 julinka-laptop NetworkManager[593]: <info> Policy set 'PJRI' (wlan0) as default for IPv4 routing and DNS.
Nov  6 14:30:31 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) successful, device activated.
Nov  6 14:30:31 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  6 14:30:31 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  6 14:30:31 julinka-laptop avahi-daemon[587]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::4e0f:6eff:fe77:c709.
Nov  6 14:30:31 julinka-laptop avahi-daemon[587]: New relevant interface wlan0.IPv6 for mDNS.
Nov  6 14:30:31 julinka-laptop avahi-daemon[587]: Registering new address record for fe80::4e0f:6eff:fe77:c709 on wlan0.*.
Nov  6 14:30:40 julinka-laptop kernel: [ 1562.080027] wlan0: no IPv6 routers present
Nov  6 14:30:50 julinka-laptop NetworkManager[593]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov  6 14:30:50 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Nov  6 14:30:50 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Nov  6 14:30:50 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  6 14:30:50 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  6 14:30:50 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Nov  6 14:31:44 julinka-laptop kernel: [ 1625.897367] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Nov  6 14:31:44 julinka-laptop kernel: [ 1625.897375] ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: disassociated
Nov  6 14:31:44 julinka-laptop kernel: [ 1625.897383] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
Nov  6 14:31:44 julinka-laptop wpa_supplicant[1145]: CTRL-EVENT-DISCONNECTED bssid=e8:39:df:b1:c1:80 reason=4
Nov  6 14:31:44 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov  6 14:31:44 julinka-laptop NetworkManager[593]: <info> (wlan0): roamed from BSSID E8:39:DF:B1:C1:80 (PJRI) to (none) ((none))
Nov  6 14:31:44 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  6 14:31:44 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:31:44 julinka-laptop kernel: [ 1626.669882] wlan0: authenticate with e8:39:df:b1:c1:80 (try 1)
Nov  6 14:31:44 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  6 14:31:45 julinka-laptop kernel: [ 1626.868037] wlan0: authenticate with e8:39:df:b1:c1:80 (try 2)
Nov  6 14:31:45 julinka-laptop kernel: [ 1627.068029] wlan0: authenticate with e8:39:df:b1:c1:80 (try 3)
Nov  6 14:31:45 julinka-laptop kernel: [ 1627.268030] wlan0: authentication with e8:39:df:b1:c1:80 timed out
Nov  6 14:31:51 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:31:51 julinka-laptop kernel: [ 1632.926644] wlan0: authenticate with e8:39:df:b1:c1:80 (try 1)
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.124043] wlan0: authenticate with e8:39:df:b1:c1:80 (try 2)
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.324028] wlan0: authenticate with e8:39:df:b1:c1:80 (try 3)
Nov  6 14:31:51 julinka-laptop wpa_supplicant[1145]: Trying to associate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.361474] wlan0: authenticated
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.361663] wlan0: associate with e8:39:df:b1:c1:80 (try 1)
Nov  6 14:31:51 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  6 14:31:51 julinka-laptop wpa_supplicant[1145]: Associated with e8:39:df:b1:c1:80
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.560025] wlan0: associate with e8:39:df:b1:c1:80 (try 2)
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.562089] wlan0: RX ReassocResp from e8:39:df:b1:c1:80 (capab=0x411 status=0 aid=4)
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.562092] wlan0: associated
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.562894] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.562898] ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
Nov  6 14:31:51 julinka-laptop kernel: [ 1633.562919] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
Nov  6 14:31:51 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: associating -> associated
Nov  6 14:31:52 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: associated -> group handshake
Nov  6 14:31:52 julinka-laptop wpa_supplicant[1145]: WPA: Key negotiation completed with e8:39:df:b1:c1:80 [PTK=TKIP GTK=TKIP]
Nov  6 14:31:52 julinka-laptop wpa_supplicant[1145]: CTRL-EVENT-CONNECTED - Connection to e8:39:df:b1:c1:80 completed (reauth) [id=0 id_str=]
Nov  6 14:31:52 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: group handshake -> completed
julinka@julinka-laptop:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan -e wpa -e etwork | tail -n55
Nov  6 14:32:25 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  6 14:32:26 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:26 julinka-laptop kernel: [ 1667.945840] wlan0: authenticate with e8:39:df:b1:c1:80 (try 1)
Nov  6 14:32:26 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  6 14:32:26 julinka-laptop NetworkManager[593]: <info> (wlan0): roamed from BSSID E8:39:DF:B1:C1:80 (PJRI) to (none) ((none))
Nov  6 14:32:26 julinka-laptop kernel: [ 1668.144028] wlan0: authenticate with e8:39:df:b1:c1:80 (try 2)
Nov  6 14:32:26 julinka-laptop kernel: [ 1668.344031] wlan0: authenticate with e8:39:df:b1:c1:80 (try 3)
Nov  6 14:32:26 julinka-laptop kernel: [ 1668.544032] wlan0: authentication with e8:39:df:b1:c1:80 timed out
Nov  6 14:32:38 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:38 julinka-laptop kernel: [ 1679.842664] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:38 julinka-laptop kernel: [ 1680.040036] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:38 julinka-laptop kernel: [ 1680.240049] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:38 julinka-laptop kernel: [ 1680.440033] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <warn> (wlan0): link timed out.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2515
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Auto-activating connection 'PJRI'.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) starting connection 'PJRI'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0/wireless): access point 'PJRI' has security, but secrets are required.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Withdrawing address record for 10.0.0.1 on wlan0.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.1.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0/wireless): connection 'PJRI' has security, and secrets exist.  No new secrets needed.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'ssid' value 'PJRI'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'scan_ssid' value '1'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'auth_alg' value 'OPEN'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'psk' value '<omitted>'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: set interface ap_scan to 1
Nov  6 14:32:43 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  6 14:32:44 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.089835] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:44 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.288064] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.488037] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.688060] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
julinka@julinka-laptop:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan -e wpa -e etwork | tail -n55
Nov  6 14:32:38 julinka-laptop kernel: [ 1680.040036] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:38 julinka-laptop kernel: [ 1680.240049] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:38 julinka-laptop kernel: [ 1680.440033] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <warn> (wlan0): link timed out.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2515
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Auto-activating connection 'PJRI'.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) starting connection 'PJRI'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0/wireless): access point 'PJRI' has security, but secrets are required.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Withdrawing address record for 10.0.0.1 on wlan0.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.1.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0/wireless): connection 'PJRI' has security, and secrets exist.  No new secrets needed.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'ssid' value 'PJRI'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'scan_ssid' value '1'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'auth_alg' value 'OPEN'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'psk' value '<omitted>'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: set interface ap_scan to 1
Nov  6 14:32:43 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  6 14:32:44 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.089835] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:44 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.288064] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.488037] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.688060] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
Nov  6 14:32:50 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:50 julinka-laptop kernel: [ 1692.341841] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:50 julinka-laptop kernel: [ 1692.540032] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:50 julinka-laptop kernel: [ 1692.740028] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:51 julinka-laptop kernel: [ 1692.940028] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
Nov  6 14:32:56 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:56 julinka-laptop kernel: [ 1698.601833] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:57 julinka-laptop kernel: [ 1698.800052] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:57 julinka-laptop kernel: [ 1699.000041] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:57 julinka-laptop kernel: [ 1699.200029] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
julinka@julinka-laptop:~$ clear

julinka@julinka-laptop:~$ clear








































julinka@julinka-laptop:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan -e wpa -e etwork | tail -n55
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2515
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Auto-activating connection 'PJRI'.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) starting connection 'PJRI'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0/wireless): access point 'PJRI' has security, but secrets are required.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Withdrawing address record for 10.0.0.1 on wlan0.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.1.
Nov  6 14:32:40 julinka-laptop avahi-daemon[587]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0/wireless): connection 'PJRI' has security, and secrets exist.  No new secrets needed.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'ssid' value 'PJRI'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'scan_ssid' value '1'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'auth_alg' value 'OPEN'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: added 'psk' value '<omitted>'
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  6 14:32:40 julinka-laptop NetworkManager[593]: <info> Config: set interface ap_scan to 1
Nov  6 14:32:43 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  6 14:32:44 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.089835] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:44 julinka-laptop NetworkManager[593]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.288064] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.488037] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:44 julinka-laptop kernel: [ 1686.688060] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
Nov  6 14:32:50 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:50 julinka-laptop kernel: [ 1692.341841] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:50 julinka-laptop kernel: [ 1692.540032] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:50 julinka-laptop kernel: [ 1692.740028] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:51 julinka-laptop kernel: [ 1692.940028] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
Nov  6 14:32:56 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:32:56 julinka-laptop kernel: [ 1698.601833] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:32:57 julinka-laptop kernel: [ 1698.800052] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:32:57 julinka-laptop kernel: [ 1699.000041] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:32:57 julinka-laptop kernel: [ 1699.200029] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
Nov  6 14:33:03 julinka-laptop wpa_supplicant[1145]: Trying to authenticate with e8:39:df:b1:c1:80 (SSID='PJRI' freq=2437 MHz)
Nov  6 14:33:03 julinka-laptop kernel: [ 1704.845832] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
Nov  6 14:33:03 julinka-laptop kernel: [ 1705.044044] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
Nov  6 14:33:03 julinka-laptop kernel: [ 1705.244053] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
Nov  6 14:33:03 julinka-laptop kernel: [ 1705.444044] wlan0: direct probe to e8:39:df:b1:c1:80 timed out

```

---

### Post by chaemil on 2011-11-06
and there are outputs from the other commands when i'm online

```
cat /etc/lsb-release; uname -a
``````

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux julinka-laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

```
```
nm-tool
```
```


NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        88:AE:1D:A6:AF:0E

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [PJRI] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        4C:0F:6E:77:C7:09

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *PJRI:           Infra, E8:39:DF:B1:C1:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA
    CZFree.Net.Tbery:Infra, 00:12:0E:33:D9:FE, Freq 2422 MHz, Rate 54 Mb/s, Strength 19
    uMedu:           Infra, 00:1F:1F:1D:EF:27, Freq 2442 MHz, Rate 54 Mb/s, Strength 15 WPA2
    HST_HOME:        Infra, 00:1F:1F:1D:16:30, Freq 2422 MHz, Rate 54 Mb/s, Strength 64 WPA2

  IPv4 Settings:
    Address:         10.0.0.1
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             10.0.0.138



```



```
lspci -nnk | grep -iA2 net
``````

04:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e021]
    Kernel driver in use: brcmsmac
--
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0139]
    Kernel driver in use: tg3

``````
iwconfig
``````

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"PJRI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E8:39:DF:B1:C1:80   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:748   Missed beacon:0

``````
rfkill list all
``````

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
sudo iwlist scan
``````

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:1F:1D:16:30
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"HST_HOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000017002a28f15d
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 00084853545F484F4D45
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1603050500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A400004243600062323000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3403050500000000000000000000000000000000000000
          Cell 02 - Address: E8:39:DF:B1:C1:80
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"PJRI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e1ccf77dd
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0004504A5249
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:12:0E:33:D9:FE
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"CZFree.Net.Tbery"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008e3976f3c45
                    Extra: Last beacon: 476ms ago
                    IE: Unknown: 0010435A467265652E4E65742E5462657279
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050C000100000400080000002001
                    IE: Unknown: 2A0105
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 00:1F:1F:1D:EF:27
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"uMedu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001173798c6d4
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 0005754D656475
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD07000C4301000000

``````
iwlist chan
``````

lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

``````
lsmod | grep wl
``````

wl                   2646601  0 
lib80211               14570  1 wl

``````
dmesg | grep wl | tail -n20
``````

wl                   2646601  0 
lib80211               14570  1 wl
julinka@julinka-laptop:~$ dmesg | grep wl | tail -n20
[ 2466.860034] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
[ 2467.060035] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
[ 2617.889864] wlan0: direct probe to e8:39:df:b1:c1:80 (try 1/3)
[ 2618.088036] wlan0: direct probe to e8:39:df:b1:c1:80 (try 2/3)
[ 2618.288026] wlan0: direct probe to e8:39:df:b1:c1:80 (try 3/3)
[ 2618.488074] wlan0: direct probe to e8:39:df:b1:c1:80 timed out
[ 2624.169893] wlan0: authenticate with e8:39:df:b1:c1:80 (try 1)
[ 2624.368052] wlan0: authenticate with e8:39:df:b1:c1:80 (try 2)
[ 2624.568036] wlan0: authenticate with e8:39:df:b1:c1:80 (try 3)
[ 2624.768033] wlan0: authentication with e8:39:df:b1:c1:80 timed out
[ 2630.441821] wlan0: authenticate with e8:39:df:b1:c1:80 (try 1)
[ 2630.443588] wlan0: authenticated
[ 2630.443765] wlan0: associate with e8:39:df:b1:c1:80 (try 1)
[ 2630.446328] wlan0: RX ReassocResp from e8:39:df:b1:c1:80 (capab=0x411 status=0 aid=4)
[ 2630.446332] wlan0: associated
[ 2630.447360] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
[ 2630.447366] ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
[ 2630.447388] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 2630.866768] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2641.792021] wlan0: no IPv6 routers present

```

---

### Post by wildmanne39 on 2011-11-06
Hi, I believe installing wicd and then purging network manager will fix the problem, people that have needed to revert to an older kernel are using intel cards.

However if you want to revert to an older kernel you can but I will not be able to help you with that, but I have helped people get 3.0 working with this issue.

Before I give you the directions for wicd please post the complete output of:
```
lsmod
```
Thank you

---

### Post by chaemil on 2011-11-06
hi. so here's the output:

```

Module                  Size  Used by
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
wl                   2646601  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
lib80211               14570  1 wl
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
brcmsmac              591864  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmutil               16885  1 brcmsmac
mac80211              272785  1 brcmsmac
uvcvideo               67271  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               85626  1 uvcvideo
soundcore              12600  1 snd
joydev                 17393  0 
psmouse                73673  0 
serio_raw              12990  0 
cfg80211              172392  2 brcmsmac,mac80211
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
crc_ccitt              12595  1 brcmsmac
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
mxm_wmi                12859  0 
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
wmi                    18744  1 mxm_wmi

```

and is the wicd working good with the unity? i mean the indicator compatibility...

---

### Post by wildmanne39 on 2011-11-06
Hi, > and is the wicd working good with the unity? i mean the indicator compatibility...
I know that it shows up in the notification area, but I do not know if it shows signal strength or not.

I did notice that your signal strength is not very strong so I would not get any further from the router then you are.

It may or may not help but you can install wicd with software center or if you have synaptic installed you can use it, then run this command to get rid of network manager.
```
sudo apt-get purge network-manager network-manager-gnome
```
You must install wicd first, I believe there are two packages you will need to install, then reboot.
Thank you

---

### Post by chaemil on 2011-11-10
hi. i have to tell you that with the wicd is it the same. wicd is saying that i have wrong password. but i set the password and ecryption right. the wireless connection work just for a while and the it stops working and i can't connect just like before.

so I've installed back the network-manager-gnome bcs i dont like the wicd...

---

### Post by wildmanne39 on 2011-11-10
Hi, please try this:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```
Reboot
Thank you

---

### Post by chaemil on 2011-11-10
i think that it does not do anything. i'm on wifi but the internet wont work... isn't here any workaround to downgrade the kernel and use the old configuration which works? i!m sick of this, I doesn't need the 3.0 kernel i just need my wifi to work.

---

### Post by wildmanne39 on 2011-11-10
Hi, I went and found you a link so you can do what you want with the kernel, I will not be able to help with that but here is the link. The information you need is in post 42.
[http://ubuntuforums.org/showthread.php?t=1862484&highlight=downgrade+kernel&page=5](http://ubuntuforums.org/showthread.php?t=1862484&highlight=downgrade+kernel&page=5)
Thank you

---

### Post by chaemil on 2011-11-14
or do you have any other ideas how to fix the wireless with the 3.0 kernel? the upstream bug fix would be nice too if we will solve it. thanks

---

### Post by chaemil on 2011-11-15
so i've accidentally deleted the /etc folder. so i will have to reinstall the ubuntu now.

---

### Post by chaemil on 2011-11-15
so even the clean installation didn't help...

---

