---
title: "Slow wifi connection"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by Kotrfa on 2013-03-23
Hi.

I have very slow wifi connection on Ubuntu. I reach just about 5-10% of my max. speed, which I can reach on Windows or by cable on Ubuntu. I guess it is in power management, but even I turn it off, it doesnt change. I'm sitting right next to router, where I can reach about 12 MB/s with Win7. With Ubuntu it is around 500-1000 KB/s...
I also tried to use another network manager - instead of default one network-manager(-gnome) I installed WICD, but there was same problem.
I'm using powertop, but after uninstall nothing changed.


Here are my logs:

iwconfig wlan0
```
wlan0     IEEE 802.11abgn  ESSID:"DHlink"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: C8:D1:5E:AD:00:E4   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

```
lspci
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

```

lsmod
```
Module                  Size  Used by
msr                    12909  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
joydev                 17458  0 
coretemp               13401  0 
kvm_intel             132760  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
kvm                   414071  1 kvm_intel
arc4                   12530  2 
snd_hwdep              17699  1 snd_hda_codec
ghash_clmulni_intel    13221  0 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
samsung_laptop         14533  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
rfcomm                 46620  0 
bnep                   18141  2 
parport_pc             32689  0 
ppdev                  17074  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
nls_iso8859_1          12714  1 
iwlwifi               386799  0 
microcode              22804  0 
mac80211              540032  1 iwlwifi
snd_timer              29426  2 snd_pcm,snd_seq
psmouse                95595  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13216  0 
btusb                  22475  0 
cfg80211              206797  2 iwlwifi,mac80211
bluetooth             209249  11 rfcomm,bnep,btusb
i915                  520615  3 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
mei                    40691  0 
soundcore              15048  1 snd
video                  19391  2 samsung_laptop,i915
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lpc_ich                17062  0 
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
r8169                  61651  0 
ahci                   25721  2 
libahci                31192  1 ahci



```



Thanks for help

---

