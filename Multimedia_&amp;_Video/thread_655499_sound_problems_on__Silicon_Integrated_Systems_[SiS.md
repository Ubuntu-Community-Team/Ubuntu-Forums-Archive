---
title: "sound problems on  Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by mla0146 on 2008-01-01
I have this sound card, and it seems I have the right driver installed on it. Here is a listing on 'aplay -l' 'lspci' and 'lsmod'. I think it is all installed ok, but I can't hear any sound still. I have gone to alsamixer and all is ok, and I have looked everywhere, and tried all I can find on this. Any help would be nice thanks!
mla0146@malcazar:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mla0146@malcazar:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
mla0146@malcazar:~$ lsmod
Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
binfmt_misc            12936  1 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
video                  18060  0 
button                  8976  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
parport_pc             37412  1 
usbhid                 29536  0 
usb_storage            73024  0 
ide_core              116804  1 usb_storage
snd_seq_midi            9600  0 
hid                    28928  1 usbhid
libusual               18448  1 usb_storage
bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
snd_rawmidi            25728  1 snd_seq_midi
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
ieee80211_crypt         7040  1 ieee80211
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
sis_agp                10116  1 
agpgart                35016  2 drm,sis_agp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sata_sis                9988  0 
ata_generic             8452  0 
floppy                 60004  0 
sis900                 24960  0 
mii                     6528  1 sis900
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
pata_sis               15236  3 sata_sis
libata                125168  3 sata_sis,ata_generic,pata_sis
scsi_mod              147084  5 usb_storage,sg,sd_mod,sr_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by adrian.salceanu on 2008-04-27
Hi
I was having a similar problem with an AC 97 sound card. The sound worked for a while and then suddenly stopped. I searched around, but no answer. But after putting together various pieces of information, it turned out that the problem was caused by a kernel (or maybe some software update) which muted certain components for the sound system.
My solution: run "alsamixer" in terminal and search for any components displaying "MM" -> they are muted. Just click the key "m" on them, and they will be unmuted.
Problem solved!
I hope it will work for you too!

---

