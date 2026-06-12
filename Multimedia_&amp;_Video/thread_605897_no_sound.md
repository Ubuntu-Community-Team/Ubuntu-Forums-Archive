---
title: "no sound"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by theknowledgeist on 2007-11-07
Hello,

My sound used to work fine until yesterday when I was playing a DVD and the computer stopped making sound. Now I have no sound at all. I'm using 7.10

I went into volume control and turned everything up to no avail.

Also, when I turn the volume knob on my keyboard it cycles only between mute and very very low. There is no other setting.

I have SB Audigy LS soundcard.

Screenshot of my sound prefs:
[ATTACH]49431[/ATTACH]

_lspci:_
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
05:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

_lsmod:_
Module                  Size  Used by
ipv6                  273892  10 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
af_packet              24840  4 
isofs                  36412  0 
udf                    87204  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
container               5504  0 
dock                   10656  0 
sbs                    19592  0 
video                  18060  0 
ac                      6148  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_ca0106             34720  4 
snd_ac97_codec        100644  1 snd_ca0106
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  34 
zd1211rw               53508  0 
xpad                    9988  0 
ieee80211softmac       31360  1 zd1211rw
ieee80211              35656  2 zd1211rw,ieee80211softmac
snd                    54660  18 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm
agpgart                35016  1 nvidia
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
i2c_nforce2             7040  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
i2c_core               26112  2 nvidia,i2c_nforce2
pcspkr                  4224  0 
psmouse                39952  0 
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
joydev                 11328  0 
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
ide_cd                 32672  1 
sd_mod                 30336  5 
cdrom                  37536  1 ide_cd
usb_storage            73024  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_generic             8452  0 
libusual               18448  1 usb_storage
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
forcedeth              51592  0 
sata_nv                20612  3 
libata                125168  2 ata_generic,sata_nv
scsi_mod              147084  5 sbp2,sg,sd_mod,usb_storage,libata
amd74xx                15260  0 [permanent]
ide_core              116804  3 ide_cd,usb_storage,amd74xx
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  8 zd1211rw,xpad,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

Thanks!

---

### Post by theknowledgeist on 2007-11-09
bump

---

### Post by maxxfell on 2007-11-10
I came across your message because I was spending a frustrating Saturday trouble shooting sound problems.  We have the same sound card and ca0106 alsa driver.

I seem to have solved the problem for my set up.  But this might not be your problem.

In alsamixer, I needed to set the columns that are labeled "analog" something to be on (I set them all to mid-volume).  On the other hand, the "IEC958" column on the extreme left needs to be off (muted).  With these settings, I now have sound from all applications.

The wierd thing is that the the speaker icon on the top panel has a red cross next to it when I can get sound, but shows sound available when I cannot!

The way I eventually fell into this solution was by booting into the oldest kernel available in my grub menu.  You might want to try doing that anyway.  Can't hurt.

Hope this helps.

M

---

### Post by theknowledgeist on 2007-11-10
Thanks maxxfell. I just re-installed ubuntu so the problem is gone now.

---

