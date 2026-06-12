---
title: "Upgraded to 9.10 today, sound not working"
date: 2009-10-24
forum: Multimedia Software
---

### Post by xorred on 2009-10-24
Hy all.. 
today I upgraded to 9.10, and sound stopped working. 
Here is my lspci output: 
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```and the output ```
of lsmod | grep '^snd'| column -t
``````
snd_hda_intel       559028  1
snd_pcm_oss         52352   0
snd_mixer_oss       24960   2  snd_pcm_oss
snd_pcm             99464   2  snd_hda_intel,snd_pcm_oss
snd_seq_dummy       11524   0
snd_seq_oss         41984   0
snd_seq_midi        15744   0
snd_rawmidi         33920   1  snd_seq_midi
snd_seq_midi_event  16512   2  snd_seq_oss,snd_seq_midi
snd_seq             66272   6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer           34064   2  snd_pcm,snd_seq
snd_seq_device      16276   5  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                 78920   9  snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc      18704   2  snd_hda_intel,snd_pcm
```alsamixer fails... 
```
alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```Also,  previously in kmix I saw that my card is Intel HDA, and I saw the front/back panel jacks, now in Kmix I see RealtekACL1200???

My Alsa info is at [http://www.alsa-project.org/db/?f=4229fe2f8bebb8c7a8fde261ab70ed4545f3fd33](http://www.alsa-project.org/db/?f=4229fe2f8bebb8c7a8fde261ab70ed4545f3fd33)

lsmod: 
> lsmod           
Module                  Size  Used by          
binfmt_misc            18572  1                
vboxnetadp            109484  0                
vboxnetflt            116972  0                
vboxdrv              1721612  1 vboxnetflt     
vmnet                  54092  13               
ppdev                  16904  0                
parport_pc             45096  0                
vmblock                23632  3                
vmci                   65192  0                
vmmon                  85328  0                
snd_hda_intel         559028  2                
snd_pcm_oss            52352  0                
snd_mixer_oss          24960  3 snd_pcm_oss    
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0                          
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter         11392  0
snd                    78920  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              28304  1 iptable_filter
soundcore              16800  3 snd
lp                     19588  0
psmouse                64028  0
serio_raw              14468  0
intel_agp              39280  0
x_tables               31624  1 ip_tables
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
nvidia              10324264  38
parport                49584  3 ppdev,parport_pc,lp
usb_storage           115392  0
8139too                36608  0
8139cp                 31488  0
mii                    14464  2 8139too,8139cp
atl1e                  45844  0
fbcon                  49792  0
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit


---

### Post by xorred on 2009-10-25
up

---

### Post by xorred on 2009-10-25
FIXED -  turned out, that if your menu.lst is hand made, it will not (the upgrade) update it. Installed startupmanager, and it fixed it. Now all works fine.

---

