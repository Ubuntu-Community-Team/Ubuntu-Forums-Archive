---
title: "Wireless Internet Connection Issues Ubuntu 12.10"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by travelholic on 2013-04-02
Hey guys, I'm having wireless connection issues. Some days I cannot get connection at all, some days it's very slow, and some days it works just fine. Here are some of the logs, but let me know if you need anything else! Thanks. 

```

adam@adam-X370:~$ sudo iwconfig
[sudo] password for adam: 
wlan0     IEEE 802.11bgn ESSID:"xxxxxxxxx"  
          Mode:Managed  Frequency:2.437GHz  Access Point: xx:xx:xx:xx:xx:xx
          Bit Rate=72.2 Mb/s  Tx-Power=20 dBm   
          Retry  long limit:7   RTSthr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=48/70  Signallevel=-62 dBm  
          Rx invalid nwid:0  Rx invalidcrypt:0  Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:1297   Missed beacon:0
lo        no wireless extensions.
eth0      no wireless extensions. 

```

```

adam@adam-X370:~$ lspci -nnk | grep-iA2 net
02:00.0 Ethernet controller [0200]:Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express GigabitEthernet controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star InternationalCo., Ltd. Device [1462:1099]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]:Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter[10ec:8176] (rev 01)
    Subsystem: AzureWave AW-NE139HHalf-size Mini PCIe Card [1a3b:1139]
    Kernel driver in use: rtl8192ce

```

```

adam@adam-X370:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek    63496  1 
snd_hda_codec_hdmi     31457  1 
kvm_amd                54395  0 
kvm                   357807  1kvm_amd
arc4                   12474  2 
snd_hda_intel          32516  5 
snd_hda_codec         111548  3snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13273  1snd_hda_codec
snd_pcm                80235  3snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1snd_seq_midi
parport_pc             31969  0 
bnep                   17708  2 
ppdev                  12818  0 
rfcomm                 37277  0 
microcode              18210  0 
bluetooth             183270  10bnep,rfcomm
rtl8192ce              52880  0 
rtl8192c_common        47076  1rtl8192ce
snd_seq_midi_event     14476  1snd_seq_midi
rtlwifi                64173  1rtl8192ce
snd_seq                51281  2snd_seq_midi,snd_seq_midi_event
rts5139               281401  0 
mac80211              461203  3rtl8192ce,rtl8192c_common,rtlwifi
psmouse                84878  0 
snd_timer              24412  2snd_pcm,snd_seq
serio_raw              13032  0 
cfg80211              175574  2rtlwifi,mac80211
k10temp                12959  0 
snd_seq_device         14138  3snd_seq_midi,snd_rawmidi,snd_seq
radeon                820764  4 
snd                    62146  20snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17162  0 
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
sp5100_tco             13418  0 
drm                   238811  6radeon,ttm,drm_kms_helper
i2c_piix4              12984  0 
i2c_algo_bit           13198  1 radeon
soundcore              14600  1 snd
snd_page_alloc         14037  2snd_hda_intel,snd_pcm
wmi                    18591  0 
video                  18848  0 
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2hid_generic,usbhid
pata_atiixp            13000  0 
r8169                  55977  0  

```

---

### Post by wildmanne39 on 2013-04-02
I posted in the other thread.

---

