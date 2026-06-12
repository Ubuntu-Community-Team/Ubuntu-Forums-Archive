---
title: "wireless driver problems"
date: 2012-09-30
forum: Networking &amp; Wireless
---

### Post by tsiric17 on 2012-09-30
so i was following this guide trying to setup my wireless driver 
[http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless) 

and at the end i type sudo modprobe "driver-name"... i tried inserting iwl3945,mac80211, and other drivers instead of driver -name but with no success...

when i do and iwconfig i see no listing of wlan0 anymore... i think i messed up badly can anyone help me fix this ?? :cry:

---

### Post by tsiric17 on 2012-09-30
Can you people at least explain to me how to remove my wireless drivers because im completely new to ubuntu, i have no idea which one im using ?? pls, ii have no internet now, im using my iphone as a hotspot

---

### Post by chili555 on 2012-09-30
If the built-in iwl3945 is not working, something else is wrong. Check to see your wireless device:```
lspci -nn | grep 0280
```For example:> Intel Corporation Centrino Advanced-N 6200 [[COLOR="Red"]8086:4239[/COLOR]]Search for the pci.id and see what driver is needed. Is it iwl3945? Check the message logs for clues:```
dmesg | grep iwl [COLOR="Red"]<--or your driver if not iwl3945[/COLOR]
```See if the hardware switch is set to enable wireless:```
rfkill list all
```I will be in and out today, so I may not answer immediately.

---

### Post by tsiric17 on 2012-09-30
I understand you are busy, thank you for answering anyway :)

Here is everything you asked me to do :

root@tomislav:~# lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)


root@tomislav:~# dmesg | grep iwl
[   21.045145] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.045148] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.045211] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.045227] iwl3945 0000:0c:00.0: setting latency timer to 64
[   21.105460] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   21.105465] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.105619] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   21.163197] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.099146] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[ 5174.120800] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 5174.120867] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf9fff000)
[ 5174.120880] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 5174.120899] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[14041.568496] iwl3945 0000:0c:00.0: PCI INT A disabled
[14210.722444] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[14210.722449] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[14210.722484] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[14210.722488] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[14210.722500] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[14210.722503] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[14210.722522] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[14210.722525] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[14210.722547] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[14210.722550] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[14210.722589] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[14210.722591] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[14210.722613] iwlegacy: disagrees about version of symbol ieee80211_channel_to_frequency
[14210.722616] iwlegacy: Unknown symbol ieee80211_channel_to_frequency (err -22)
[14210.722630] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[14210.722633] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[14345.552157] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[14345.552162] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[14345.552193] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[14345.552196] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[14345.552207] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[14345.552210] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[14345.552227] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[14345.552230] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[14345.552250] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[14345.552252] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[14345.552287] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[14345.552290] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[14345.552309] iwlegacy: disagrees about version of symbol ieee80211_channel_to_frequency
[14345.552311] iwlegacy: Unknown symbol ieee80211_channel_to_frequency (err -22)
[14345.552325] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[14345.552328] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[14435.000277] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[14435.000282] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[14435.000313] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[14435.000315] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[14435.000326] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[14435.000329] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[14435.000347] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[14435.000349] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[14435.000368] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[14435.000371] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[14435.000405] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[14435.000408] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[14435.000427] iwlegacy: disagrees about version of symbol ieee80211_channel_to_frequency
[14435.000429] iwlegacy: Unknown symbol ieee80211_channel_to_frequency (err -22)
[14435.000443] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[14435.000445] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[15838.545710] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[15838.545714] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[15838.545745] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[15838.545748] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[15838.545759] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[15838.545762] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[15838.545780] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[15838.545782] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[15838.545801] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[15838.545804] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[15838.545839] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[15838.545841] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[15838.545861] iwlegacy: disagrees about version of symbol ieee80211_channel_to_frequency
[15838.545863] iwlegacy: Unknown symbol ieee80211_channel_to_frequency (err -22)
[15838.545877] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[15838.545879] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[22412.992094] Modules linked in: compat(O) btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs reiserfs ext2 dm_crypt snd_hrtimer joydev ipheth dell_wmi sparse_keymap parport_pc ppdev dell_laptop dcdbas snd_hda_codec_idt bnep rfcomm bluetooth snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi binfmt_misc r592 uvcvideo r852 sm_common nand nand_ids mtd nand_bch bch videodev arc4 snd_seq_midi_event psmouse nand_ecc memstick snd_seq serio_raw hid_logitech_dj iwl_legacy mac80211 snd_timer snd_seq_device mac_hid snd cfg80211 soundcore snd_page_alloc lp parport usbhid hid nouveau firewire_ohci ttm sdhci_pci sdhci firewire_core crc_itu_t drm_kms_helper drm i2c_algo_bit mxm_wmi video wmi usb_storage [last unloaded: iwl3945]



root@tomislav:~# rfkill list all
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


I also did lsmod command. i dont know if thats helpful to you but i didi it anyway


root@tomislav:~# lsmod
Module                  Size  Used by
compat                 19507  0 
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
dm_crypt               22528  1 
snd_hrtimer            12648  1 
joydev                 17393  0 
ipheth                 13278  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
parport_pc             32114  0 
ppdev                  12849  0 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hda_codec_idt      60251  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
binfmt_misc            17292  1 
r592                   17808  0 
uvcvideo               67203  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
videodev               86588  1 uvcvideo
arc4                   12473  0 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                87213  0 
nand_ecc               13070  1 nand
memstick               15857  1 r592
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
serio_raw              13027  0 
hid_logitech_dj        18178  0 
iwl_legacy             71134  0 
mac80211              436455  1 iwl_legacy
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62064  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 iwl_legacy,mac80211
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  1 hid_logitech_dj
hid                    77367  2 hid_logitech_dj,usbhid
nouveau               708260  3 
firewire_ohci          40180  0 
ttm                    65344  1 nouveau
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
drm_kms_helper         45466  1 nouveau
drm                   197692  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
video                  19068  1 nouveau
wmi                    18744  2 dell_wmi,mxm_wmi
usb_storage            39646  0 


Thank you in advance :)

---

### Post by chili555 on 2012-09-30
Busy? Yeah, busy taking a vacation in Arizona!> [14210.722444] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[14210.722449] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[14210.722484] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[14210.722488] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[14210.722500] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_nameYou have an unhappy driver there. You need to remove the compat package:> so i was following this guide trying to setup my wireless driver
[http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless) I know nothing about aircrack but compat and the built-in iwl3945 often don't play well together.```
 
 $ sudo make [COLOR="Red"]un[/COLOR]install

 
```

---

### Post by tsiric17 on 2012-09-30
Well thanks for answering :D 
I maneged to solve my problem, my wlan0 is up and running once again...
I guess im gonna have to try with a different driver

Sry if i bothered you with all that text and possibly retarded questions, enjoy your vacation :D

---

