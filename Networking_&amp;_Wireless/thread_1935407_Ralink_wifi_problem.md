---
title: "Ralink wifi problem"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by JackOConnor on 2012-03-04
Hello. I'm new to linux completely not just to ubuntu. I obtained a copy of ubuntu 12.04 alpha on a cd. I tested it out and liked it but I decided to go for 11.10. The wifi worked perfectly on 12.04 but when tested 11.10 on the cd, my wireless network would not show up.
    Here is some information about my system:

sudo ismod

Module                  Size  Used by 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep 
parport_pc             32114  0 
dm_crypt               22565  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48717  1 rt2800pci 
crc_ccitt              12595  1 rt2800lib 
rt2x00pci              14202  1 rt2800pci 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib 


snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
cfg80211              172392  2 rt2x00lib,mac80211 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28932  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
eeprom_93cx6           12653  1 rt2800pci 
soundcore              12600  1 snd 
serio_raw              12990  0 
mei                    36466  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_utf8               12493  1 
isofs                  39549  1 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45 
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror 
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash 
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs 
libcrc32c              12543  1 btrfs 
usbhid                 41905  0 
hid                    77367  1 usbhid 
mxm_wmi                12859  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci 
wmi                    18744  1 mxm_wmi 
crc_itu_t              12627  1 firewire_core 
r8169                  43104  0 
xhci_hcd               72915  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915 
drm                   192226  4 i915,drm_kms_helper 
i2c_algo_bit           13199  1 i915 
video                  18908  1 i915 
ahci                   21634  1 
libahci                25727  1 ahci

sudo ispci

ubuntu@ubuntu:~$ sudo lspci 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) 
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) 
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5) 
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) 
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) 
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5) 
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5) 
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) 
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05) 
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) 
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05) 
02:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30) 
03:01.0 Network controller: Ralink corp. Device 3062 
03:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) 
04:00.0 USB Controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01) 
05:00.0 USB Controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01) 
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
07:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11) 


extras asked for:

```
ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
ubuntu@ubuntu:~$ rfkill list 
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
ubuntu@ubuntu:~$ dmesg grep rt2 
Usage: dmesg [-c] [-n level] [-r] [-s bufsize
```] 

Please someone help, I really want to get this working!!!

---

### Post by praseodym on 2012-03-04
Hi,

please show additionally:

```
iwconfig
rfkill list
dmesg | grep rt2
```

---

### Post by JackOConnor on 2012-03-04
I have added what you asked for. I hope it helps!!!

---

### Post by livesourav on 2012-04-20
Might be a problem with the driver... check for additional drivers in the hardware tab after the installation ..

---

