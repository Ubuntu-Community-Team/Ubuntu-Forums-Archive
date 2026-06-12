---
title: "Upgrade From 8.04 to 9.10 Soundcard Gone"
date: 2009-11-08
forum: Multimedia Software
---

### Post by terrykiwi83 on 2009-11-08
Have upgraded from 8.04 (64bit) to 9.10 (64bit) and now have no sound at all, as well as no devices found in the multimedia selector.

```

terry@terry-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

```

terry@terry-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22

```

lsmod
```

Module                  Size  Used by
isofs                  43688  0 
udf                    92712  1 
tun                    20868  1 
iptable_nat            14724  1 
nf_nat                 30100  1 iptable_nat
xt_MARK                11264  1 
iptable_mangle         11520  1 
xt_mark                10624  3 
xt_tcpudp              11776  2 
nf_conntrack_ipv4      24216  8 iptable_nat,nf_nat
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
xt_state               10624  5 
nf_conntrack           84752  4 iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
binfmt_misc            18572  1 
vboxnetflt            107628  0 
vboxnetadp            100524  0 
vboxdrv              1715852  1 vboxnetflt
ppdev                  16904  0 
parport_pc             45096  0 
aes_x86_64             16384  1 
aes_generic            36264  1 aes_x86_64
snd_hda_intel         559028  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
arc4                   10240  2 
ecb                    11392  2 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt73usb                35716  0 
crc_itu_t              10496  2 udf,rt73usb
snd_timer              34064  2 snd_pcm,snd_seq
iptable_filter         11392  1 
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2500usb              29824  0 
rt2x00usb              20352  2 rt73usb,rt2500usb
rt2x00lib              43008  3 rt73usb,rt2500usb,rt2x00usb
led_class              13064  1 rt2x00lib
snd                    78920  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              251528  2 rt2x00usb,rt2x00lib
ip_tables              28304  3 iptable_nat,iptable_mangle,iptable_filter
psmouse                64028  0 
x_tables               31624  6 iptable_nat,xt_MARK,xt_mark,xt_tcpudp,xt_state,ip_tables
soundcore              16800  1 snd
usblp                  22656  0 
cfg80211               43680  2 rt2x00lib,mac80211
joydev                 20864  0 
coretemp               15360  0 
serio_raw              14468  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
nvidia              10325384  20 
lp                     19588  0 
parport                49584  3 ppdev,parport_pc,lp
usbhid                 47040  0 
usb_storage           115520  2 
atl1e                  45844  0 
floppy                 75816  0 
intel_agp              39408  0 

```

```

terry@terry-desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)

```

Hope someone can help, Thanks.

---

### Post by terrykiwi83 on 2009-11-08
FIXED!! Didn't realise that I was booting into what seemed to be the wrong Linux headers if that makes sense. Looked like I was booting into Jaunty's kernel instead of the newer Karmic kernel.

Hope that makes sense

---

