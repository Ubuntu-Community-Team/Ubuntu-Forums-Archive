---
title: "DVB-T recognized, but not working?"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by Ashrael on 2007-09-18
Hi, i got a usb dv-t stick (MSI digi vox mini-II, V1.02), now it won't work? It seems to recognize it, but i guess some link must still be made somewhere...

lsusb gives me:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 10fd:1513 Anubis Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lsmod gives me:

lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
battery                10756  0 
container               5248  0 
button                  8720  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
video                  16388  0 
nls_utf8                3072  1 
ntfs                  107764  1 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268960  10 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_ac97_codec         98464  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
sn9c102               128900  0 
compat_ioctl32          2304  1 sn9c102
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
nvidia               4713780  22 
videodev               29312  1 sn9c102
v4l2_common            18432  2 sn9c102,videodev
v4l1_compat            15236  1 videodev
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
dvb_usb_m920x          18308  0 
dvb_usb                22924  1 dvb_usb_m920x
dvb_core               82604  1 dvb_usb
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
serio_raw               7940  0 
psmouse                38920  0 
shpchp                 34324  0 
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_sis96x              6532  0 
soundcore               8672  1 snd
i2c_core               22656  4 i2c_ec,nvidia,dvb_usb,i2c_sis96x
sis_agp                 9604  1 
agpgart                35400  2 nvidia,sis_agp
emu10k1_gp              4736  0 
gameport               16520  2 emu10k1_gp
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  3 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  9 
generic                 5124  0 [permanent]
sis5513                14856  0 [permanent]
pata_sis               14732  6 
floppy                 59524  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
sis900                 24704  0 
mii                     6528  1 sis900
ehci_hcd               34188  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ohci_hcd               22532  0 
usbcore               134280  6 sn9c102,dvb_usb_m920x,dvb_usb,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

Any tips or suggestions are welcome.

---

### Post by menollo on 2007-10-26
have you read this?
[http://www.linuxtv.org/v4lwiki/index.php/MSI_DigiVox_mini_II](http://www.linuxtv.org/v4lwiki/index.php/MSI_DigiVox_mini_II)

---

### Post by Ashrael on 2007-11-17
going to do that tomorrow...now for a beer, it's 3 am, that's why...:lolflag:

thanx for posting that...

---

### Post by Ashrael on 2007-11-28
thanks man, workes like a charm on both 7.04 and 7.10.... i have dvb-t tv now!!

---

