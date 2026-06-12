---
title: "No wireless connections found"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by mchesnaye on 2013-06-01
Hi everyone, 

I'm having trouble getting my wireless to work. There are no wireless connections in the Network Manager (there should be). I did a pretty extensive search, but i don't understand half the stuff that seems to be going on.. i'm quite a noob when it comes to ubuntu. 

I've listed information below that i think may be of help, and I'm running ubuntu 12.4
Hope someone can help!!


iwconfig
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.


rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



lspi
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


lsmod
Module                  Size  Used by
rfcomm                 38104  16 
bnep                   17791  2 
parport_pc             32115  0 
ppdev                  12850  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
arc4                   12474  2 
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_idt      60238  1 
snd_hda_intel          32983  9 
ath9k                 122028  0 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
mac80211              475546  1 ath9k
kvm                   365588  0 
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
ath9k_common           13782  1 ath9k
snd_seq_midi_event     14476  1 snd_seq_midi
radeon                837045  0 
uvcvideo               72249  0 
ath9k_hw              384090  2 ath9k,ath9k_common
ttm                    76326  1 radeon
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
ath                    19436  3 ath9k,ath9k_common,ath9k_hw
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  17952  0 
drm_kms_helper         47459  1 radeon
videobuf2_core         32212  1 uvcvideo
ir_lirc_codec          12740  0 
joydev                 17394  0 
lirc_dev               18701  1 ir_lirc_codec
cfg80211              181041  3 ath9k,mac80211,ath
psmouse                91381  0 
drm                   240232  3 radeon,ttm,drm_kms_helper
videodev              100265  2 uvcvideo,videobuf2_core
bluetooth             189585  24 rfcomm,bnep,btusb
snd                    62675  28 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_mce_kbd_decoder     12682  0 
ir_sanyo_decoder       12466  0 
ir_sony_decoder        12463  0 
ir_jvc_decoder         12460  0 
ir_rc6_decoder         12460  0 
microcode              18396  0 
ir_rc5_decoder         12460  0 
soundcore              14636  1 snd
ir_nec_decoder         12460  0 
video                  19117  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
rc_rc6_mce             12455  0 
sp5100_tco             13496  0 
k10temp                12998  0 
hp_wmi                 13653  0 
hp_accel               25729  0 
sparse_keymap          13659  1 hp_wmi
ene_ir                 18020  0 
videobuf2_vmalloc      12757  1 uvcvideo
lis3lv02d              19270  1 hp_accel
mac_hid                13078  0 
rc_core                21295  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
i2c_piix4              13094  0 
videobuf2_memops       13213  1 videobuf2_vmalloc
serio_raw              13032  0 
i2c_algo_bit           13317  1 radeon
wmi                    18745  1 hp_wmi
input_polldev          13649  1 lis3lv02d
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
usb_storage            39720  0 
r8169                  56853  0 
pata_atiixp            13000  0 
ahci                   25621  2 
libahci                26166  1 ahci

---

### Post by mchesnaye on 2013-06-01
Well i just installed Widc network manager and it seems to be solved.. so the problem was related to Network Manager, allthough i have no idea what it was.

---

