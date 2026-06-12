---
title: "Again (and hopefully for the last time) Intel 5xxx WLAN on Linux"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by lucas4 on 2013-08-12
I'm a happy user of old laptop Asus M70Vm - never let me down though his weight is aroung 6 kilos :)

Got an Intel 5000 AGN inside, worked like a charm in win xp/7 I would even say that this wireless network card seems to be better than most of decent oem wifi cards mounted into laptops produced in 2008-2011. But straight to bussiness.

I had Debian Lenny few years ago on this laptop - those were the times with kernel 2.6/2.7 but now when I've installed Precise Pangolin it seems that my iwl5000 stopped working. It takes sooo much time to prompt for a wifi key (using Gnome Unity) and when it's finally getting done then it stops at getting address which it will never get and then prompt again for wifi key (WPA2/AES)

I've searched for the sollution thorought the web - most of the Ubuntu users recommended to use [this firmware.]("http://wireless.kernel.org/en/users/Drivers/iwlwifi/?n=Downloads") Did this but still not working. I am eager to change my wlan card to another with Atheros or Broadcom chipset if nothing will help.

Is there a final sollution for those kind of problems

```
lucas@laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9600M GS] (rev a1)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```
```
lucas@laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```
```
lucas@laptop:~$ lsmod
Module                  Size  Used by
vesafb                 13844  1 
rfcomm                 47604  0 
bnep                   18281  2 
rc_rc6_mce             12502  0 
bluetooth             180113  10 rfcomm,bnep
tpm_infineon           17536  0 
parport_pc             32866  0 
ppdev                  17113  0 
ext2                   73795  1 
joydev                 17693  0 
arc4                   12529  2 
nvidia              11308613  42 
iwldvm                249728  0 
mac80211              556794  1 iwldvm
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
iwlwifi               176433  1 iwldvm
snd_rawmidi            30748  1 snd_seq_midi
cfg80211              558777  3 iwldvm,mac80211,iwlwifi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
r852                   18277  0 
sm_common              16908  1 r852
nand                   54955  2 r852,sm_common
nand_ids               12723  1 nand
r592                   18144  0 
ir_lirc_codec          12859  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
mtd                    33087  2 sm_common,nand
nand_bch               13147  1 nand
bch                    22096  1 nand_bch
lirc_dev               19204  1 ir_lirc_codec
compat                 34143  4 iwldvm,mac80211,iwlwifi,cfg80211
memstick               16569  1 r592
v4l2_compat_ioctl32    17128  1 videodev
nand_ecc               13273  1 nand
ir_mce_kbd_decoder     12777  0 
snd_timer              29990  2 snd_pcm,snd_seq
ir_sony_decoder        12510  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_jvc_decoder         12507  0 
psmouse                97485  0 
serio_raw              13211  0 
ir_rc6_decoder         12507  0 
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
ite_cir                25775  0 
rc_core                26412  10 rc_rc6_mce,ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ite_cir
video                  19651  0 
tpm_tis                18804  0 
snd                    79041  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
sdhci_pci              18826  0 
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci
r8169                  62190  0 

```
```

dmesg
[49838.538684] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[49840.561592] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[49840.568089] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[49840.688842] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[49848.421383] wlan0: authenticate with b0:48:7a:ed:01:80
[49848.423018] wlan0: direct probe to b0:48:7a:ed:01:80 (try 1/3)
[49848.624060] wlan0: direct probe to b0:48:7a:ed:01:80 (try 2/3)
[49848.828046] wlan0: direct probe to b0:48:7a:ed:01:80 (try 3/3)
[49888.384048] wlan0: authentication with b0:48:7a:ed:01:80 timed out
[49890.400043] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues Q 0
[49890.400049] iwlwifi 0000:03:00.0: Current SW read_ptr 9 write_ptr 12
[49890.400076] iwl data: 00000000: 00 0e 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[49890.400090] iwlwifi 0000:03:00.0: FH TRBs(0) = 0x00000000
[49890.400105] iwlwifi 0000:03:00.0: FH TRBs(1) = 0x00000000
[49890.400119] iwlwifi 0000:03:00.0: FH TRBs(2) = 0x00000000
[49890.400133] iwlwifi 0000:03:00.0: FH TRBs(3) = 0x8030000b
[49890.400147] iwlwifi 0000:03:00.0: FH TRBs(4) = 0x00000000
[49890.400162] iwlwifi 0000:03:00.0: FH TRBs(5) = 0x00000000
[49890.400176] iwlwifi 0000:03:00.0: FH TRBs(6) = 0x00000000
[49890.400190] iwlwifi 0000:03:00.0: FH TRBs(7) = 0x0070407b
[49890.400245] iwlwifi 0000:03:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [9,12]
[49890.400298] iwlwifi 0000:03:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[49890.400352] iwlwifi 0000:03:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [0,0]
[49890.400405] iwlwifi 0000:03:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400459] iwlwifi 0000:03:00.0: Q 4 is active and mapped to fifo 7 ra_tid 0x0000 [124,124]
[49890.400513] iwlwifi 0000:03:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400567] iwlwifi 0000:03:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400623] iwlwifi 0000:03:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400683] iwlwifi 0000:03:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400741] iwlwifi 0000:03:00.0: Q 9 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400797] iwlwifi 0000:03:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400852] iwlwifi 0000:03:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400908] iwlwifi 0000:03:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.400964] iwlwifi 0000:03:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.401019] iwlwifi 0000:03:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.401075] iwlwifi 0000:03:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.401132] iwlwifi 0000:03:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.401188] iwlwifi 0000:03:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.401244] iwlwifi 0000:03:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49890.401303] iwlwifi 0000:03:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[49945.965798] wlan0: authenticate with b0:48:7a:ed:01:80
[49945.967364] wlan0: direct probe to b0:48:7a:ed:01:80 (try 1/3)
[49946.168037] wlan0: direct probe to b0:48:7a:ed:01:80 (try 2/3)
[49946.372068] wlan0: direct probe to b0:48:7a:ed:01:80 (try 3/3)
[49946.576041] wlan0: authentication with b0:48:7a:ed:01:80 timed out

```

```
lsb_release -d
Description:    Ubuntu 12.04.2 LTS

```

```
uname -mr
3.2.0-51-generic x86_64

```

---

### Post by lucas4 on 2013-08-12
I'm also using USB WLAN card (Linsys Cisco WUSB600Nv2) just to make sure I'm connecting my AP in the right way and everything runs smoothly on that external USB WLAN for the record.

---

