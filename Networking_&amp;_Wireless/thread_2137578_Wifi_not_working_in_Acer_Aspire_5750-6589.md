---
title: "Wifi not working in Acer Aspire 5750-6589"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by manish310794 on 2013-04-21
I installed Ubuntu 12.04 but the wifi is not working. The internet icon on the desktop shows "Wired Network disconnected". Please help. I am new to Ubuntu.

---

### Post by praseodym on 2013-04-21
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Cable connection works?

---

### Post by manish310794 on 2013-04-22
```

manish310794@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
           Subsystem: Acer Incorporated [ALI] Device [1025:0504]
           Kernel driver in use: tg3
_ _
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
           Subsystem: Acer Incorporated [ALI] Device [1025:0504]
           Kernel driver in use: sdhci-pci
_ _
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
           Subsystem: Foxconn International, Inc. Device [105b:e040]
05:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

```

---

### Post by manish310794 on 2013-04-22
```

manish310794@ubuntu:~$ lsmod
Module                                                    Size                  Used by
snd_hda_codec_hdmi                               32476                     1
snd_hda_codec_realtek                            79756                     1
coretemp                                               13642                     0
kvm_intel                                              137888                    0
kvm                                                      422160                  1 kvm_intel
ghash_clmulni_intel                                 13221                      0
cryptd                                                  20531                    1 ghash_clmulni_intel
joydev                                                  17694                    0
acer_wmi                                              32845                     0
sparse_keymap                                      13891                     1 acer_wmi
microcode                                             23030                     0
snd_hda_intel                                        34117                     3
snd_hda_codec                                    135141                    3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep                                           17765                      1 snd_hda_codec
snd_pcm                                              97523                     3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi                                        13325                     0
psmouse                                             102075                    0
serio_raw                                            13216                       0
snd_rawmidi                                         30750                     1 snd_seq_midi
lpc_ich                                               17145                       0
snd_seq_midi_event                              14900                     1 snd_seq_midi
snd_seq                                             61931                      2 snd_seq_midi,snd_seq_midi_event
uvcvideo                                            78117                      0
videobuf2_core                                    33025                     1 uvcvideo
videodev                                           125126                    2 uvcvideo,videobuf2_core
videobuf2_vmalloc                               12861                      1 uvcvideo
videobuf2_memops                              13405                      1 vediobuf2_vmalloc
snd_timer                                          29990                      2 snd_pcm,snd_seq
snd_seq_device                                 14498                      3 snd_seq_midi,snd_rawmidi,snd_seq
snd                                                  83674                      16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                                         15092                      1 snd
snd_page_alloc                                   18573                     2 snd_hda_intel,snd_pcm
mei                                                  41410                      0
parport_pc                                        32867                      0
rfcomm                                             47562                      0
ppdev                                              17114                      0
lp                                                    17800                      0
parport                                            46563                       3 parport_pc,ppdev,lp
bnep                                               18240                      2
bluetooth                                        211812                     10 rfcomm,bnep
mac_hid                                           13254                       0
i915                                               530857                      3
drm_kms_helper                                49259                       1 i915
drm                                               290344                       4 i915,drm_kms_helper
tg3                                                156594                     0
sdhci_pci                                         18749                      0
sdhci                                              33145                      1 sdhci_pci
i2c_algo_bit                                    13565                       1 i915
video                                             19598                       2 acer_wmi,i915
wmi                                               19257                       1 acer_wmi

```

---

### Post by manish310794 on 2013-04-22
```

manish310794@ubuntu:~$ iwconfig
eht0         no wireless extensions
lo             no wireless extensions

```

I would like to mention one thing that when I use my Windows 7 (my pc is on dual boot) the wifi works absolutely well. But as soon as I boot the Ubuntu, my wifi would refuse to turn on no matter how many times I press my wifi function key.

---

### Post by manish310794 on 2013-04-22
```

manish310794@ubuntu:~$ rfkill list
0: acer-wireless: Wireless LAN
           Soft blocked: no
           Hard blocked: no
manish310794@ubuntu:~$

```

---

### Post by praseodym on 2013-04-22
Install the Broadcom-STA driver via cable connection. ->"Additional drivers"

---

### Post by manish310794 on 2013-04-24
I have downloaded Broadcom-STA driver. What to do next? How can I install it?

---

### Post by Hadaka on 2013-04-24
Hi, from a wired connection
please do..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
 
```
thanks.

---

