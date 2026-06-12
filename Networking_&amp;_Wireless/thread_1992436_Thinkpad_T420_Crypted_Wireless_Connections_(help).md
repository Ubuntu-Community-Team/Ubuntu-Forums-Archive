---
title: "Thinkpad T420 Crypted Wireless Connections (help)"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by Elmnteee on 2012-05-31
Hello Forum,

I have a problem with my wireless-network and  my Lenovo ThinkPad T420- Laptop with an Intel-Centrino Advanced 6205 card. With Windows 7 running, all worked fine. Now i wanted to change to Kubuntu 12.04, because emulating all the time sucks, but wireless doesn't work with a wpa key. Uncrypted connections work fine. 

Thanks for your help :)
Elmnteee

Some infos:
```

lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:16.3 Serial controller [0700]: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller [8086:1c3d] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b4)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation QM67 Express Chipset Family LPC Controller [8086:1c4f] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
0d:00.0 System peripheral [0880]: Ricoh Co Ltd Device [1180:e823] (rev 08)
0d:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller [1180:e832] (rev 04)
lsmod:
Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62128  1 
btusb                  18288  0 
bluetooth             180104  11 rfcomm,bnep,btusb
arc4                   12529  2 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cdc_ncm                17399  0 
usbnet                 26212  1 cdc_ncm
snd_seq_midi           13324  0 
cdc_wdm                17581  0 
cdc_acm                26858  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              205544  2 iwlwifi,mac80211
tpm_tis                18804  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
thinkpad_acpi          81819  0 
nvram                  14413  1 thinkpad_acpi
mac_hid                13253  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
mei                    41616  0 
lp                     17799  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
wmi                    19256  0 
firewire_ohci          41000  0 
e1000e                156693  0 
firewire_core          63558  1 firewire_ohci
i915                  468651  3 
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
nm-tool:
Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62128  1 
btusb                  18288  0 
bluetooth             180104  11 rfcomm,bnep,btusb
arc4                   12529  2 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cdc_ncm                17399  0 
usbnet                 26212  1 cdc_ncm
snd_seq_midi           13324  0 
cdc_wdm                17581  0 
cdc_acm                26858  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              205544  2 iwlwifi,mac80211
tpm_tis                18804  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
thinkpad_acpi          81819  0 
nvram                  14413  1 thinkpad_acpi
mac_hid                13253  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
mei                    41616  0 
lp                     17799  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
wmi                    19256  0 
firewire_ohci          41000  0 
e1000e                156693  0 
firewire_core          63558  1 firewire_ohci
i915                  468651  3 
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:21:cc:6c:4f:aa  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe6c:4faa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:423566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:592397390 (592.3 MB)  TX bytes:27440116 (27.4 MB)
          Interrupt:20 Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:638520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47881730 (47.8 MB)  TX bytes:47881730 (47.8 MB)

usb0      Link encap:Ethernet  HWaddr 02:80:37:ec:02:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 08:11:96:64:04:90  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a11:96ff:fe64:490/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:883358 (883.3 KB)  TX bytes:176373 (176.3 KB)


```

---

### Post by Elmnteee on 2012-06-06
Please need help ::(

---

### Post by Xephyrind on 2012-12-18
> **Elmnteee said:**
> Please need help ::(

I am currently experiencing a similar situation. Have you gotten it resolved? Thanks.

---

