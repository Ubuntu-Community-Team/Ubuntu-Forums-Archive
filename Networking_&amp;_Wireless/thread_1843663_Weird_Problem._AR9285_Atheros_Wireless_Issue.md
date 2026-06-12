---
title: "Weird Problem. AR9285 Atheros Wireless Issue"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by waqasahmed on 2011-09-13
Hey all,

I got myself a new netbook here and I installed Ubuntu 11.04 on it, and initially the wireless would not work. You could connect to a network, and you would be able to receive an IP address, but you could not actually go to a site and load it. A ping to the default gateway would fail

This is not just restricted to my wireless router, as I thought it might be. I tethered my ZTE Blade and made a wireless access point, with no security (temporarily), and I had the same issue

Interestingly however is that you can put in an ethernet plug in to the netbook (Asus 1011PX) , and you would receive a network connection (ie: one that actually works and not just one that gives you an IP) and once you pull the cable out, the Wireless magically sounds working.

This is the workaround that Im using at the moment. I'd be grateful if any one can help. I've been scratching my head for ages about this

---

### Post by pdc on 2011-09-14
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by waqasahmed on 2011-09-14
Thanks for that. Ill now provide more info

**1 ) Machine Brand and Model (PC/Laptop)**:
   
     Asus 1011PX, 6 cell Li-ion, N570 CPU, 320GB HDD, 1GB DDR3 RAM

[http://www.asus.com/Eee/Eee_PC/Eee_PC_1011PX/#specifications](http://www.asus.com/Eee/Eee_PC/Eee_PC_1011PX/#specifications)

**2 ) Wireless Brand, Model and Wireless Chipset:**
Code:
     $ lspci

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```**Grep**
     Code:
     $ lspci -nn | grep Atheros 

```
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```[B]

3 ) check interface:[/B]

Code:
     $ ifconfig

```
wlan0     Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:192.168.2.6  Bcast:192.168.2.15  Mask:255.255.255.240
          inet6 addr: fe80::762f:68ff:fe34:714a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:903479 (903.4 KB)  TX bytes:322319 (322.3 KB)

```Code:
     $ iwconfig wlan0

```
wlan0     IEEE 802.11bgn  ESSID:"Waqas_Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:55   Missed beacon:0
```[B]

4 ) Check for modules:[/B]
     Code:
     $ lsmod 
```
Module                  Size  Used by
r8712u                281937  0 
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  358 
aes_generic            38023  1 aes_i586
dm_crypt               22463  1 
parport_pc             32111  0 
ppdev                  12849  0 
arc4                   12473  2 
ath9k                 105891  0 
joydev                 17322  0 
mac80211              259567  1 ath9k
ath9k_common           13797  1 ath9k
snd_hda_codec_realtek   255882  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ath9k_hw              311106  2 ath9k,ath9k_common
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ath                    19147  2 ath9k,ath9k_hw
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              155552  3 ath9k,mac80211,ath
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
uvcvideo               66851  0 
psmouse                59039  0 
serio_raw              12990  0 
videodev               75143  1 uvcvideo
eeepc_wmi              18771  0 
sparse_keymap          13666  1 eeepc_wmi
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
i915                  451068  3 
ahci                   21591  2 
drm_kms_helper         40745  1 i915
libahci                25548  1 ahci
drm                   184164  4 i915,drm_kms_helper
atl1c                  35753  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
```     Code:
     $ lsmod | grep "wlan_module_name" 
Not quite so what to do here ^

**5 ) Kernel boot messages**
     Code:
     $ dmesg 
```
[    6.259761] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4719800
[    6.259807] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4719721
[    6.259909] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1973060
[    6.260032] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1968996
[    6.293470] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3539235
[    6.321202] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393777
[    6.321271] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393984
[    6.321413] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393988
[    6.321498] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393982
[    6.321657] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393986
[    6.321757] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4721166
[    6.321800] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4721165
[    6.321839] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 16124458
[    6.321881] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804019
[    6.321964] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3803997
[    6.368053] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804086
[    6.369399] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3802987
[    6.369447] EXT4-fs (sda1): 22 orphan inodes deleted
[    6.369453] EXT4-fs (sda1): recovery complete
[    6.485860] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.845522] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.143043] <30>udev[346]: starting version 167
[   13.919545] type=1400 audit(1315987670.636:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=544 comm="apparmor_parser"
[   13.919757] type=1400 audit(1315987670.636:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=637 comm="apparmor_parser"
[   13.919782] type=1400 audit(1315987670.636:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=514 comm="apparmor_parser"
[   13.920525] type=1400 audit(1315987670.640:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=544 comm="apparmor_parser"
[   13.921017] type=1400 audit(1315987670.640:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=637 comm="apparmor_parser"
[   13.921045] type=1400 audit(1315987670.640:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=514 comm="apparmor_parser"
[   13.921092] type=1400 audit(1315987670.640:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=544 comm="apparmor_parser"
[   13.921772] type=1400 audit(1315987670.640:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=637 comm="apparmor_parser"
[   13.921805] type=1400 audit(1315987670.640:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=514 comm="apparmor_parser"
[   14.020759] lp: driver loaded but no devices found
[   14.062547] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input6
[   14.115273] Linux video capture interface: v2.00
[   14.668320] uvcvideo: Found UVC 1.00 device USB2.0 UVC VGA WebCam (13d3:5702)
[   14.687189] input: USB2.0 UVC VGA WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input7
[   14.687428] usbcore: registered new interface driver uvcvideo
[   14.687436] USB Video Class driver (v1.0.0)
[   14.806651] elantech: assuming hardware version 2, firmware version 20.1.0
[   14.867654] elantech: Synaptics capabilities query result 0x68, 0x15, 0x0a.
[   15.069963] eeepc_wmi: Backlight controlled by ACPI video driver
[   15.188088] elantech: retrying ps2 command 0xe6 (2).
[   15.304673] cfg80211: Calling CRDA to update world regulatory domain
[   15.702484] elantech: retrying ps2 command 0xf8 (2).
[   16.008692] cfg80211: World regulatory domain updated:
[   16.008701] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.008709] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.008716] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.008723] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.008729] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.008736] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.404094] elantech: retrying ps2 command 0xf8 (1).
[   16.984280] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[   17.017281] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.017406] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.017472] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.108913] hda_codec: ALC269VB: BIOS auto-probing.
[   17.118699] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.823607] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.823634] ath9k 0000:02:00.0: setting latency timer to 64
[   17.875338] ath: EEPROM regdomain: 0x60
[   17.875345] ath: EEPROM indicates we should expect a direct regpair map
[   17.875353] ath: Country alpha2 being used: 00
[   17.875357] ath: Regpair used: 0x60
[   17.875364] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.875371] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875377] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.875384] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875389] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.875396] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875402] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.875409] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875414] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.875421] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875426] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.875433] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875439] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.875445] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875451] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.875458] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875463] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.875470] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875476] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.875482] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875488] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.875495] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875500] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.875507] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875513] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.875519] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.875525] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   17.875532] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.877551] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   18.158661] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.160632] Registered led device: ath9k-phy0
[   18.160660] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8ce0000, irq=17
[   19.267229] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.302542] atl1c 0000:01:00.0: irq 46 for MSI/MSI-X
[   19.389006] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.515673] type=1400 audit(1315987676.232:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=928 comm="apparmor_parser"
[   19.516640] type=1400 audit(1315987676.236:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=928 comm="apparmor_parser"
[   19.517162] type=1400 audit(1315987676.236:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=928 comm="apparmor_parser"
[   19.680531] ppdev: user-space parallel port driver
[   19.706388] type=1400 audit(1315987676.424:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=932 comm="apparmor_parser"
[   19.712509] type=1400 audit(1315987676.432:15): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=927 comm="apparmor_parser"
[   19.864162] type=1400 audit(1315987676.584:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=929 comm="apparmor_parser"
[   19.874476] type=1400 audit(1315987676.592:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=929 comm="apparmor_parser"
[   19.880743] type=1400 audit(1315987676.600:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=929 comm="apparmor_parser"
[   19.917273] type=1400 audit(1315987676.636:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=943 comm="apparmor_parser"
[   19.917299] type=1400 audit(1315987676.636:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=931 comm="apparmor_parser"
[   22.065034] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   22.640065] Intel AES-NI instructions are not detected.
[   22.715598] padlock_aes: VIA PadLock not detected.
[   22.882226] padlock_sha: VIA PadLock Hash Engine not detected.
[   23.397480] wlan0: authenticate with 1c:bd:b9:be:89:ca (try 1)
[   23.399413] wlan0: authenticated
[   23.399467] wlan0: associate with 1c:bd:b9:be:89:ca (try 1)
[   23.405589] wlan0: RX AssocResp from 1c:bd:b9:be:89:ca (capab=0x431 status=0 aid=2)
[   23.405598] wlan0: associated
[   23.413234] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.413791] cfg80211: Calling CRDA for country: DE
[   23.422667] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   23.422677] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422683] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   23.422690] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422696] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   23.422703] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422709] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   23.422715] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422721] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   23.422728] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422734] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   23.422740] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422746] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   23.422753] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422759] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   23.422765] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422771] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   23.422778] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422784] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   23.422790] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422796] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   23.422803] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422809] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   23.422815] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422821] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   23.422828] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.422833] cfg80211: Disabling freq 2484 MHz
[   23.422844] cfg80211: Regulatory domain changed to country: DE
[   23.422848] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.422855] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   23.422861] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   23.422867] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   23.422873] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   23.512062] CE: hpet increased min_delta_ns to 20113 nsec
[   24.143600] vboxdrv: Found 4 processor cores.
[   24.144493] vboxdrv: fAsync=0 offMin=0x53c offMax=0x4d12
[   24.144717] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.144725] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   31.614438] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   34.208061] wlan0: no IPv6 routers present
[   37.543496] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  124.146344] wlan0: deauthenticating from 1c:bd:b9:be:89:ca by local choice (reason=3)
[  124.243259] cfg80211: All devices are disconnected, going to restore regulatory settings
[  124.243278] cfg80211: Restoring regulatory settings
[  124.243331] cfg80211: Calling CRDA to update world regulatory domain
[  124.259008] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  124.259022] cfg80211: World regulatory domain updated:
[  124.259027] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  124.259035] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  124.259042] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  124.259048] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  124.259055] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  124.259061] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  125.340220] wlan0: authenticate with 1c:bd:b9:be:89:ca (try 1)
[  125.342240] wlan0: authenticated
[  125.342294] wlan0: associate with 1c:bd:b9:be:89:ca (try 1)
[  125.351245] wlan0: RX AssocResp from 1c:bd:b9:be:89:ca (capab=0x431 status=0 aid=2)
[  125.351260] wlan0: associated
[  125.359547] cfg80211: Calling CRDA for country: DE
[  125.368747] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  125.368757] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368764] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  125.368771] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368776] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  125.368783] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368789] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  125.368796] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368802] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  125.368809] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368815] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  125.368822] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368828] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  125.368835] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368841] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  125.368848] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368853] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  125.368861] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368866] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  125.368873] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368879] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  125.368886] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368892] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  125.368899] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368905] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  125.368912] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  125.368917] cfg80211: Disabling freq 2484 MHz
[  125.368928] cfg80211: Regulatory domain changed to country: DE
[  125.368933] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  125.368939] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.368946] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.368952] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.368958] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[  194.776120] usb 1-3: new high speed USB device using ehci_hcd and address 4
[  195.139669] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[  195.156907] r8712u: DriverVersion: v7_0.20100831
[  195.156949] r8712u: register rtl8712_netdev_ops to netdev_ops
[  195.156955] r8712u: USB_SPEED_HIGH with 4 endpoints
[  195.157842] r8712u: Boot from EFUSE: Autoload OK
[  195.616819] r8712u: CustomerID = 0x0000
[  195.616833] r8712u: MAC Address from efuse = **:**:**:**:**:**
[  195.619640] usbcore: registered new interface driver r8712u
[  196.488666] r8712u: 1 RCR=0x153f00e
[  196.489407] r8712u: 2 RCR=0x553f00e
[  196.597279] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  226.896452] wlan0: deauthenticating from 1c:bd:b9:be:89:ca by local choice (reason=3)
[  226.965826] cfg80211: All devices are disconnected, going to restore regulatory settings
[  226.965846] cfg80211: Restoring regulatory settings
[  226.965878] cfg80211: Calling CRDA to update world regulatory domain
[  226.980713] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  226.980728] cfg80211: World regulatory domain updated:
[  226.980733] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  226.980740] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  226.980747] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  226.980754] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  226.980760] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  226.980767] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  233.976484] wlan0: authenticate with 1c:bd:b9:be:89:ca (try 1)
[  233.980520] wlan0: authenticated
[  234.001448] wlan0: associate with 1c:bd:b9:be:89:ca (try 1)
[  234.005704] wlan0: RX AssocResp from 1c:bd:b9:be:89:ca (capab=0x431 status=0 aid=2)
[  234.005718] wlan0: associated
[  234.014461] cfg80211: Calling CRDA for country: DE
[  234.026182] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  234.026192] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026199] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  234.026205] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026211] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  234.026218] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026224] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  234.026230] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026236] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  234.026243] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026248] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  234.026255] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026261] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  234.026267] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026273] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  234.026280] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026286] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  234.026292] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026298] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  234.026305] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026310] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  234.026317] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026323] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  234.026329] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026335] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  234.026342] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  234.026347] cfg80211: Disabling freq 2484 MHz
[  234.026358] cfg80211: Regulatory domain changed to country: DE
[  234.026362] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  234.026369] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  234.026375] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  234.026381] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  234.026387] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[  243.187947] cfg80211: All devices are disconnected, going to restore regulatory settings
[  243.187983] cfg80211: Restoring regulatory settings
[  243.188001] cfg80211: Calling CRDA to update world regulatory domain
[  243.206648] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  243.206678] cfg80211: World regulatory domain updated:
[  243.206688] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  243.206704] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  243.206719] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  243.206733] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  243.206748] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  243.206762] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  244.224392] wlan0: authenticate with 1c:bd:b9:be:89:ca (try 1)
[  244.226451] wlan0: authenticated
[  244.226531] wlan0: associate with 1c:bd:b9:be:89:ca (try 1)
[  244.231042] wlan0: RX AssocResp from 1c:bd:b9:be:89:ca (capab=0x431 status=0 aid=2)
[  244.231055] wlan0: associated
[  244.239804] cfg80211: Calling CRDA for country: DE
[  244.255458] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  244.255477] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255488] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  244.255500] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255510] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  244.255522] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255532] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  244.255544] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255554] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  244.255566] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255576] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  244.255588] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255598] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  244.255610] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255620] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  244.255633] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255643] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  244.255655] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255665] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  244.255677] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255687] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  244.255699] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255710] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  244.255722] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255732] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  244.255743] cfg80211: 2400000 KHz - 2483500 KHz @  KHz), (N/A mBi, 2000 mBm)
[  244.255752] cfg80211: Disabling freq 2484 MHz
[  244.255771] cfg80211: Regulatory domain changed to country: DE
[  244.255778] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  244.255790] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  244.255801] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  244.255812] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  244.255822] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[  308.335314] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  308.620202] r8712u: [r8712_got_addbareq_event_callback] mac = 1c:bd:b9:be:89:ca, seq = 16, tid = 0
[  318.960061] wlan1: no IPv6 routers present
[  403.282918] usb 1-3: USB disconnect, address 4
```[B]

6 ) Network configuration[/B]
     Code:
     $ sudo lshw -C network 
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: **:**:**:**:**:**
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic-pae firmware=N/A ip=192.168.2.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial:  **:**:**:**:**:**
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
```[B]



7 ) Scan for networks:[/B]
     Code:
     $ iwlist scan 
```
wlan0     Scan completed :
          Cell 01 - Address: **:**:**:**:**:**
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Waqas_Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002e75032b5
                    Extra: Last beacon: 55860ms ago
                    IE: Unknown: 000E57617161735F576972656C657373
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000C127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706444520010D10
```**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d 
```
Ubuntu 11.04
```[B]

9 ) Kernel/architecture (including 32 vs. 64 bit): [/B]
     Code:
     $ uname -mr 
```
2.6.38-11-generic-pae i686
```[B]


10 ) Restarting the network:[/B]
     Code:
     $ sudo /etc/init.d/networking restart
```

* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
```

---

### Post by pdc on 2011-09-14
I am not an expert: 

if you type

> gedit /etc/resolv.conf

in a terminal; and copy and paste the result back here

eg mine gives

> # Generated by NetworkManager
domain home
search home
nameserver 192.168.1.1

---

### Post by waqasahmed on 2011-09-14
> **pdc said:**
> I am not an expert: 

if you type

```
gedit /etc/resolv.conf 			 		
```

in a terminal; and copy and paste the result back here

eg mine gives

```
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.1 			 		
```


Hey, I typed
Code:
$ gedit /etc/resolv.conf

in to the terminal, and I got this back:
```
# Generated by NetworkManager
nameserver 192.168.2.1
```

---

### Post by pdc on 2011-09-14
hmmmmmmm

hopefully praesodym or some other expert will pounce

if you google on your problem one gets hits like

[http://kb.mozillazine.org/Error_loading_any_website](http://kb.mozillazine.org/Error_loading_any_website)

---

### Post by SecretCode on 2011-09-14
If you
```
ping 192.168.2.1
```
can you reach that name server?

What are the results from nslookup?
```
nslookup www.google.com
```

---

### Post by waqasahmed on 2011-09-14
> **pdc said:**
> hmmmmmmm

hopefully praesodym or some other expert will pounce

if you google on your problem one gets hits like

[http://kb.mozillazine.org/Error_loading_any_website](http://kb.mozillazine.org/Error_loading_any_website)

That seems to suggest that it's a firewall fissue when I havent messed around with any firewall configurations, and the workaround seems to get WiFi for me

> **SecretCode said:**
> If you
```
ping 192.168.2.1
```can you reach that name server?

Yes and No. When I boot up the netbook, or its gone to sleep then I can not ping the default gateway. If I attach an ethernet cable in to the port, get a wired connection and pull it out, I get a connection. This workaround also works if I attach an external WiFi dongle and search for my network through there

All this time however I do get an IP from the router which is weird
What are the results from nslookup?
```
nslookup www.google.com
```[/QUOTE]

Whilst my WiFi is working, I get this:

```
Server:        192.168.2.1
Address:    192.168.2.1#53

Non-authoritative answer:
Name:    google.com
Address: 209.85.229.99
Name:    google.com
Address: 209.85.229.104
Name:    google.com
Address: 209.85.229.147

```

Interestingly enough, the previous version of this netbook has been certified by Ubuntu:
[http://www.ubuntu.com/certification/hardware/201101-6992](http://www.ubuntu.com/certification/hardware/201101-6992)

The only difference with this one is the hard drive and the CPU

---

### Post by waqasahmed on 2011-09-14
Bump

---

### Post by pdc on 2011-09-15
I get 

> $ nslookup [www.google.com](www.google.com)
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	[www.google.com](www.google.com)
Address: 72.14.203.104
Name:	[www.google.com](www.google.com)
Address: 72.14.203.105
Name:	[www.google.com](www.google.com)
Address: 72.14.203.106
Name:	[www.google.com](www.google.com)
Address: 72.14.203.147
Name:	[www.google.com](www.google.com)
Address: 72.14.203.99
Name:	[www.google.com](www.google.com)
Address: 72.14.203.103


I could only google to try to answer your problems now

---

### Post by fdrake on 2011-09-15
reboot and try the wifi (do not try the ethernet cable yet) after running this command:
```

sudo route add default gw 192.168.2.1 wlan0

```
are you able to connect now?

it looks to me that your wifi cannot get the gateway address, but the Ethernet does.

---

### Post by SecretCode on 2011-09-16
Odd. Looks like your /etc/resolv.conf is fine, but DHCP may not be working properly.

Reboot and try the wifi (only) and see what this command returns:
```
grep dhclient /var/log/syslog
```
(before running fdrake's route add command, which is also worth trying)

---

