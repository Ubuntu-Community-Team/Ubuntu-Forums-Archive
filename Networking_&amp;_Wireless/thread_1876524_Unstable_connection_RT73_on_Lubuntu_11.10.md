---
title: "Unstable connection RT73 on Lubuntu 11.10"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by Psirus1988 on 2011-11-06
Hi, I'm having problems with my wireless connection, it is very slow and unstable. 
I don't have acces to the router, but the connection on my desktop is fine, different wlan-card.
Thanks in advance

Machine: Acer Aspire 3002LC
Wireless Dongle: MSI US54EX
lsusb: ```
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

```uname: ```
3.0.0-12-generic i686
```ifconfig: ```
wlan0     Link encap:Ethernet  HWaddr 00:1f:cf:12:7e:dc  
          inet addr:192.168.178.29  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:cfff:fe12:7edc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4160770 (4.1 MB)  TX bytes:363491 (363.4 KB)
```iwconfig:```
wlan0     IEEE 802.11bg  ESSID:"FRITZ!Box Fon WLAN 7170"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:04:0E:ED:DC:C0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:104  Invalid misc:323   Missed beacon:0
```lsmod: ```
Module                  Size  Used by
arc4                   12473  2 
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20092  1 rt73usb
rt2x00lib              48114  2 rt73usb,rt2x00usb
mac80211              272785  2 rt2x00usb,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
snd_intel8x0           33318  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
pcmcia                 39822  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
k8temp                 12905  0 
yenta_socket           27428  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
i2c_sis96x             12743  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sis900                 22729  0 
```dmesg: ```
[   18.746617] udevd[276]: starting version 173
[   18.846616] Adding 456700k swap on /dev/sda5.  Priority:-1 extents:1 across:456700k 
[   18.854349] lp: driver loaded but no devices found
[   18.969467] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.973869] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   19.098476] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.362638] type=1400 audit(1320584599.409:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=473 comm="apparmor_parser"
[   19.363701] type=1400 audit(1320584599.409:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=473 comm="apparmor_parser"
[   19.364151] type=1400 audit(1320584599.413:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=473 comm="apparmor_parser"
[   19.379799] type=1400 audit(1320584599.425:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=481 comm="apparmor_parser"
[   19.738704] yenta_cardbus 0000:00:06.0: CardBus bridge found [1025:0083]
[   19.738722] yenta_cardbus 0000:00:06.0: Using CSCINT to route CSC interrupts to PCI
[   19.738726] yenta_cardbus 0000:00:06.0: Routing CardBus interrupts to PCI
[   19.738733] yenta_cardbus 0000:00:06.0: TI: mfunc 0x00521d22, devctl 0x64
[   19.968794] yenta_cardbus 0000:00:06.0: ISA IRQ mask 0x06f8, PCI irq 19
[   19.968801] yenta_cardbus 0000:00:06.0: Socket status: 30000006
[   20.154651] eth0: Media Link Off
[   20.155095] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.279574] type=1400 audit(1320584600.325:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=616 comm="apparmor_parser"
[   20.284440] type=1400 audit(1320584600.333:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=616 comm="apparmor_parser"
[   20.284841] type=1400 audit(1320584600.333:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=616 comm="apparmor_parser"
[   20.285515] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   20.313473] type=1400 audit(1320584600.361:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=617 comm="apparmor_parser"
[   20.341261] type=1400 audit(1320584600.389:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=617 comm="apparmor_parser"
[   20.351770] type=1400 audit(1320584600.397:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=617 comm="apparmor_parser"
[   20.518228] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000/0x0
[   20.555045] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   20.931699] init: failsafe main process (655) killed by TERM signal
[   20.934612] init: apport pre-start process (723) terminated with status 1
[   20.940816] init: alsa-restore main process (729) terminated with status 19
[   20.988736] init: apport post-stop process (748) terminated with status 1
[   21.260070] intel8x0_measure_ac97_clock: measured 55386 usecs (2664 samples)
[   21.260077] intel8x0: clocking to 48000
[   21.268280] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   21.269914] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x480-0x48f 0x4d0-0x4d7
[   21.270586] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   21.271166] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   21.271801] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   21.271857] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   21.271914] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   21.271973] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   21.388509] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   21.388515] vesafb: scrolling: redraw
[   21.388520] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   21.388792] vesafb: framebuffer at 0xe8000000, mapped to 0xdca00000, using 1216k, total 1216k
[   21.388932] fbcon: VESA VGA (fb0) is primary device
[   21.389039] Console: switching to colour frame buffer device 80x30
[   21.389060] fb0: VESA VGA frame buffer device
[   21.480995] ppdev: user-space parallel port driver
[   21.818970] Bluetooth: Core ver 2.16
[   21.819036] NET: Registered protocol family 31
[   21.819039] Bluetooth: HCI device and connection manager initialized
[   21.819044] Bluetooth: HCI socket layer initialized
[   21.819046] Bluetooth: L2CAP socket layer initialized
[   21.821467] Bluetooth: SCO socket layer initialized
[   21.826923] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.826931] Bluetooth: BNEP filters: protocol multicast
[   21.884047] Bluetooth: RFCOMM TTY layer initialized
[   21.884057] Bluetooth: RFCOMM socket layer initialized
[   21.884060] Bluetooth: RFCOMM ver 1.11
[   22.140949] init: plymouth-stop pre-start process (896) terminated with status 1
[   27.699265] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   85.440122] cfg80211: Calling CRDA to update world regulatory domain
[   85.466800] cfg80211: World regulatory domain updated:
[   85.466812] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   85.466822] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   85.466831] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   85.466839] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   85.466847] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   85.466855] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  151.058218] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  151.058230] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058238] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  151.058247] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058254] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  151.058262] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058269] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  151.058277] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058284] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  151.058292] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058299] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  151.058308] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058314] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  151.058322] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058329] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  151.058337] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058344] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  151.058352] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058359] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  151.058367] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058374] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  151.058382] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058389] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  151.058397] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058404] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  151.058412] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.058419] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  151.058427] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  151.078701] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  151.086305] Registered led device: rt73usb-phy0::radio
[  151.086367] Registered led device: rt73usb-phy0::assoc
[  151.086422] Registered led device: rt73usb-phy0::quality
[  151.087023] usbcore: registered new interface driver rt73usb
[  151.297358] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1015.491086] wlan0: direct probe to 00:04:0e:ed:dc:c0 (try 1/3)
[ 1015.495615] wlan0: direct probe responded
[ 1015.495643] wlan0: authenticate with 00:04:0e:ed:dc:c0 (try 1)
[ 1015.515475] wlan0: authenticated
[ 1015.562085] wlan0: associate with 00:04:0e:ed:dc:c0 (try 1)
[ 1015.760046] wlan0: associate with 00:04:0e:ed:dc:c0 (try 2)
[ 1015.792908] wlan0: RX AssocResp from 00:04:0e:ed:dc:c0 (capab=0x411 status=0 aid=3)
[ 1015.792919] wlan0: associated
[ 1015.806173] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1026.384028] wlan0: no IPv6 routers present
[ 1036.049663] wlan0: deauthenticating from 00:04:0e:ed:dc:c0 by local choice (reason=3)
[ 1036.061044] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1036.061058] cfg80211: Restoring regulatory settings
[ 1036.061532] cfg80211: Calling CRDA to update world regulatory domain
[ 1036.075691] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075705] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075713] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075722] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075729] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075737] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075744] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075752] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075759] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075767] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075774] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075783] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075789] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075798] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075804] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075813] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075819] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075828] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075834] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075843] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075849] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075858] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075864] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075873] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075880] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075888] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075895] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1036.075903] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1036.075911] cfg80211: World regulatory domain updated:
[ 1036.075916] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1036.075924] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1036.075932] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1036.075940] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1036.075948] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1036.075956] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1040.461079] wlan0: authenticate with 00:04:0e:ed:dc:c0 (try 1)
[ 1040.626136] wlan0: authenticated
[ 1040.648459] wlan0: associate with 00:04:0e:ed:dc:c0 (try 1)
[ 1040.655367] wlan0: RX ReassocResp from 00:04:0e:ed:dc:c0 (capab=0x411 status=0 aid=3)
[ 1040.655377] wlan0: associated
[ 1052.504043] wlan0: no IPv6 routers present

```lshw: ```
 *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1f:cf:12:7e:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.0.0-12-generic firmware=1.7 ip=192.168.178.29 link=yes multicast=yes wireless=IEEE 802.11bg
```iwlist scan: ```
wlan0     Scan completed :
          Cell 01 - Address: 00:04:0E:ED:DC:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a3a14f22d
                    Extra: Last beacon: 8720ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

---

### Post by praseodym on 2011-11-06
Hi,

try pure WPA2-AES encryption instead of mixed WPA/WPA2.

---

### Post by Psirus1988 on 2011-11-06
And how would I go about that? When I go to Network Connections -> Wireless -> Edit -> Wireless Security there are 7 options, 2 of which contain WPA2: "WPA & WPA2 Personal" (which is what I have choosen) and "WPA & WPA2 Enterprise"

---

### Post by praseodym on 2011-11-06
Cnnect via cable to the router, type in the IP address of the router into the browser and change the encryption in the router interface

---

### Post by Psirus1988 on 2011-11-06
> **Psirus1988 said:**
> 
I don't have acces to the router, but the connection on my desktop is fine, different wlan-card.

Not really an option, I wish I could.

---

### Post by Psirus1988 on 2011-11-07
Any Ideas? :(

---

### Post by praseodym on 2011-11-07
Try Wicd instead of the NM:


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
Choose **wlan0** as interface name and **wext** as driver. You can choose mixed encryption there.

---

### Post by Psirus1988 on 2011-11-07
Thanks, but sadly, it didn't work.

---

### Post by amjjawad on 2011-11-07
> **Psirus1988 said:**
> Thanks, but sadly, it didn't work.

Hi there,

Could you please explain more about your problem? no need to post the output for any command, I just need to understand what exactly do you have?

---

### Post by wildmanne39 on 2011-11-07
Hi, please try this and if it works we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
sudo ifconfig wlan0 up
```
Run the commands one at a time.
Do not restart your computer.
Thank you

---

### Post by amjjawad on 2011-11-07
> **wildmanne39 said:**
> Hi, please try this and if it works we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
sudo ifconfig wlan0 up
```Run the commands one at a time.
Do not restart your computer.
Thank you

Aha, a better person than myself has showed up :D
Hello my good friend :)

---

### Post by wildmanne39 on 2011-11-07
Hi amjjawad!!!

---

### Post by amjjawad on 2011-11-07
> **wildmanne39 said:**
> Hi amjjawad!!!

Hey :)
I'm sure you are the right person for this job :)

I really need to find some time to learn about these stuff. If you do have some tips/guides to read when I get sometime, please shot (PM) but it that requires more training and learning, then I have to do it myself :)

---

### Post by Psirus1988 on 2011-11-07
> **amjjawad said:**
> Hi there,

Could you please explain more about your problem? no need to post the output for any command, I just need to understand what exactly do you have?

Hi, I can connect to the network, but it is really, really slow (like 450 B/s) and it drops the connection from time to time.

> **wildmanne39 said:**
> Hi, please try this and if it works we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
sudo ifconfig wlan0 up
```Run the commands one at a time.
Do not restart your computer.
Thank you

It seems more stable, it hasn't disconnected in quite a while now, but it's still glacier slow.

---

### Post by wildmanne39 on 2011-11-07
Hi, is that with the code applied that I posted?
Thank you

---

### Post by Psirus1988 on 2011-11-07
Yes, thats after changing the option on the rt73usb module.

---

### Post by wildmanne39 on 2011-11-07
Hi, let's make it permanent then reboot and see if speed increases as well as stability.

```
gksudo gedit /etc/modprobe.d/rt73usb.conf
```
Add a single line:
```
options rt73usb nohwcrypt=1
```
Proofread carefully, save and close gedit, then reboot.
Thank you

---

### Post by Psirus1988 on 2011-11-08
Ok, I did that. However, no speed increase.

---

### Post by wildmanne39 on 2011-11-08
Hi, have you made sure that ipv6 is set to ignore? Look at screenshot. It may look different if you are using wicd.

I have an usb adapter that uses the same driver I just hooked it up and followed the same procedure that I gave you and mine is stable and fast.

What speed did you get before 11.10?

How are you determining it is a slow connection? maybe this information will help to narrow the problem down.
Thank you

---

### Post by Psirus1988 on 2011-11-08
Hi, there is no setting to ignore iqv6 on wicd. I haven't used this laptop in quite a while, and never on this network before. I do remember using it with the speed about 1,2 Mb/s; I don't need this much, but normal internet browsing would be nice.
I determined the speed a) with normal web usage, pages barely load at all, download speeds as mentioned earlier b) ping google: 25% package loss, avg: 135ms, max: 689ms, mdev: 188ms; for comparison, my desktop, on the same network (also wireless): avg: 34ms, max: 43mi, mdev: 2.8ms, 0% loss

---

### Post by wildmanne39 on 2011-11-08
Hi, I have been researching your issue for quit a while now and I have not found much but I would disable ipv6 here is a link.
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
Thank you

---

### Post by Psirus1988 on 2011-11-10
I've tried that, but sadly, no improvement.
Thank you so much for your effort anyway.

---

### Post by wildmanne39 on 2011-11-10
Hi, this is the last thing I know to try to get the speed increased.

I am going to include a screenshot as an example of what the nameserver should look like but it is with network manager so you will need to make this setting change in wicd.

Add the google nameservers 8.8.8.8 and 8.8.4.4) in "IPv4-settings" in wicd network-manager.

Change to "Automatic (DHCP), addresses only" and add the nameservers in the field "DNS-servers". Reboot
Thank you

---

