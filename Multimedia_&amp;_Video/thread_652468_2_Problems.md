---
title: "2 Problems"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by Meizulo on 2007-12-28
1) I am using VLC as my media player for my movies becuase I was  
    having way too many problems with Totem. 
     - The first problem is that when I play non-DVD formats I don't get       
       any  sound
     - The second problem is that when I play DVD format I get this  
       "Unable to open 
        x-nautilus-desktop:/CD-RW%2FDVD-ROM%20Drive.volume"

2) Everytime I go onto a site which has flash Firefox crashes. I am 
    pretty sure I have downloaded and installed Flashplayer, but it is 
    still causing problems.

---

### Post by buntunub on 2007-12-28
1. What version of Ubuntu are you running?
2. post the ouput of lsmod

---

### Post by Meizulo on 2007-12-28
1) Ubuntu 7.10 Fiesty
2) I don't know how to post lsmod?

---

### Post by Sef on 2007-12-28
> 2) I don't know how to post lsmod?

Applications > Accessories > Terminal

then type ```
lsmod
```

Highlight the results > Edit > Copy  > Click reply in this thread and Edit > Paste.

---

### Post by Meizulo on 2007-12-28
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  1 
radeon                125472  2 
drm                    83348  3 radeon
ipv6                  273892  8 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
speedstep_lib           6404  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
sbs                    19592  0 
video                  18060  0 
dock                   10656  0 
button                  8976  0 
battery                11012  0 
container               5504  0 
ac                      6148  0 
sbp2                   24072  0 
lp                     12580  0 
joydev                 11328  0 
pcmcia                 41388  0 
snd_atiixp_modem       17160  0 
snd_seq_dummy           4740  0 
irda                  202300  0 
snd_seq_oss            33152  0 
crc_ccitt               3072  1 irda
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
parport_pc             37412  1 
snd_atiixp             21132  1 
snd_ac97_codec        100644  2 snd_atiixp_modem,snd_atiixp
parport                37448  3 ppdev,lp,parport_pc
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
psmouse                39952  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
snd                    54660  13 snd_atiixp_modem,snd_seq_oss,snd_rawmidi,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
snd_page_alloc         11400  3 snd_atiixp_modem,snd_atiixp,snd_pcm
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  18828  0 
mmc_core               28420  1 sdhci
wlan_scan_sta          15104  1 
ath_rate_sample        14208  1 
ath_pci                98336  0 
wlan                  206660  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192720  3 ath_rate_sample,ath_pci
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
ati_agp                10124  1 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  2 drm,ati_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
8139cp                 25088  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sbp2,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
8139too                27776  0 
mii                     6528  2 8139cp,8139too
atiixp                  7056  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,atiixp
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  3 ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by buntunub on 2008-01-05
> snd_seq_dummy 4740 0 

What is this? You have alot of, what seems to me, to be conflicting sound modules. You might try disabling these or playing with the alsa and oss sound settings. Disable and reenable as needed, and see if that makes any difference. I dont see anything there about alsa (might be looking in the wrong place) but you might try to load/reload alsa as well.

---

