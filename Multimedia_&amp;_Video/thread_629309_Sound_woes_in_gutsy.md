---
title: "Sound woes in gutsy"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by dean20007 on 2007-12-02
HI folks 

I have some sound issues with gutsy. I can't seem to control the volume using the master volume. i.e. it 'mutes' but actually does not affect the sound at all

Another problem is the my multimedia keys volume control seem to work in a very strange fashion, it will either turn sound up maximum or off completely with no middle ground! 

I am using Logitech V20 USB Speakers. In the sound configuration I have set it to use USB Audio and tried ALSA both result in the same problem

Below is the output from lsmod, lsusb, lspci 

LSMOD 
```
Module                  Size  Used by
joydev                 11328  0 
wacom                  17664  0 
usblp                  15104  0 
ipv6                  273892  12 
fglrx                 656352  30 
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
sbs                    19592  0 
ac                      6148  0 
button                  8976  0 
video                  18060  0 
container               5504  0 
dock                   10656  0 
battery                11012  0 
af_packet              24840  2 
ndiswrapper           185240  0 
lp                     12580  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
rt73usb                25344  0 
rt2x00usb              12032  1 rt73usb
rt2x00lib              19584  2 rt73usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
snd_usb_audio          81024  4 
cfg80211                7304  1 mac80211
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  6 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_usb_lib            17920  1 snd_usb_audio
input_polldev           5896  1 rt2x00lib
snd_seq_dummy           4740  0 
crc_itu_t               3072  1 rt2x00lib
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
xpad                    9988  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
serio_raw               8068  0 
psmouse                39952  0 
k8temp                  6656  0 
snd_hwdep              10244  1 snd_usb_audio
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  4 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd                    54660  18 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
amd64_agp              13700  1 
agpgart                35016  2 fglrx,amd64_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sd_mod                 30336  5 
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sata_sis                9988  4 
floppy                 60004  0 
sis900                 24960  0 
mii                     6528  1 sis900
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  12 wacom,usblp,ndiswrapper,rt73usb,rt2x00usb,snd_usb_audio,snd_usb_lib,xpad,usbhid,ehci_hcd,ohci_hcd
pata_sis               15236  1 sata_sis
ata_generic             8452  0 
libata                125168  3 sata_sis,pata_sis,ata_generic
scsi_mod              147084  4 sd_mod,sg,sr_mod,libata
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

LSUSB
```
Bus 004 Device 012: ID 050d:705a Belkin Components 
Bus 004 Device 009: ID 03f0:8904 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 056a:0062 Wacom Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:0a04 Logitech, Inc. 
Bus 001 Device 005: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 001: ID 0000:0000  

```

LSPCI

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0c.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

```

---

### Post by GrouchoMarx on 2007-12-02
Have you tried switching the volume control from "Master" to "Headphones" or "PCM"? I know this doesn't answer WHY the Master Volume control doesn't work, but it may not a bug per se, and it might simply be that not all the channels are fully functional for all cards.

---

