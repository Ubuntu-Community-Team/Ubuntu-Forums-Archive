---
title: "Sound Issues"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by fractus.ordo on 2007-06-14
Ok, I'm using a Creative Extigy and I have sound working for Kaffeine and Amarok, but it's quiet. I've read to adjust the volume in alsamixer but I receive this message: 
```
alsamixer: function snd_ctl_open failed for default: No such device
```

I've also read that if OSS modules are loaded they can interfere, but I've only started using Linux this week, so I'm not sure of what to look for. Any help would be greatly appreciated.
```
wheelerh@wheelerh-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1
vfat                   14208  1
fat                    53916  1 vfat
nls_cp437               6784  2
isofs                  36284  1
udf                    85252  0
binfmt_misc            12680  1
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_ondemand        9228  0
cpufreq_powersave       2688  0
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0
sony_acpi               6284  0
tc1100_wmi              8068  0
dev_acpi               12292  0
pcc_acpi               13184  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
ac                      6020  0
dock                   10268  0
asus_acpi              17308  0
battery                10756  0
backlight               7040  1 asus_acpi
button                  8720  0
container               5248  0
video                  16388  0
ipv6                  268960  8
sbp2                   23812  0
parport_pc             36388  0
lp                     12452  0
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  7
lmpcm_usb               7040  0
usbhid                 26592  0
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_usb_audio          79744  2
snd_pcm_oss            44544  1
snd_mixer_oss          17408  2 snd_pcm_oss
hid                    27392  1 usbhid
nvidia               4713780  22
snd_pcm                79876  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_seq_oss,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,sn
d_timer,snd_seq_device
i2c_core               22656  2 i2c_ec,nvidia
serio_raw               7940  0
psmouse                38920  0
soundcore               8672  3 snd
intel_agp              25244  1
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
agpgart                35400  2 nvidia,intel_agp
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  2
tsdev                   8768  0
evdev                  11008  5
usb_storage            72256  1
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
libusual               17936  1 usb_storage
sg                     36252  0
sr_mod                 17060  1
cdrom                  37664  1 sr_mod
sd_mod                 23428  9
ata_generic             9092  0
8139too                27648  0
ata_piix               15492  6
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
floppy                 59524  0
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
8139cp                 25088  0
mii                     6528  2 8139too,8139cp
generic                 5124  0 [permanent]
ehci_hcd               34188  0
uhci_hcd               25360  0
usbcore               134280  9 lmpcm_usb,usbhid,snd_usb_audio,snd_usb_lib,usb_storage,libusual,ehci_hcd,uhci_hcd
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
wheelerh@wheelerh-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1
vfat                   14208  1
fat                    53916  1 vfat
nls_cp437               6784  2
isofs                  36284  1
udf                    85252  0
binfmt_misc            12680  1
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_ondemand        9228  0
cpufreq_powersave       2688  0
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0
sony_acpi               6284  0
tc1100_wmi              8068  0
dev_acpi               12292  0
pcc_acpi               13184  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
ac                      6020  0
dock                   10268  0
asus_acpi              17308  0
battery                10756  0
backlight               7040  1 asus_acpi
button                  8720  0
container               5248  0
video                  16388  0
ipv6                  268960  8
sbp2                   23812  0
parport_pc             36388  0
lp                     12452  0
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  7
lmpcm_usb               7040  0
usbhid                 26592  0
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_usb_audio          79744  2
snd_pcm_oss            44544  1
snd_mixer_oss          17408  2 snd_pcm_oss
hid                    27392  1 usbhid
nvidia               4713780  22
snd_pcm                79876  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_seq_oss,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               22656  2 i2c_ec,nvidia
serio_raw               7940  0
psmouse                38920  0
soundcore               8672  3 snd
intel_agp              25244  1
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
agpgart                35400  2 nvidia,intel_agp
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  2
tsdev                   8768  0
evdev                  11008  5
usb_storage            72256  1
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
libusual               17936  1 usb_storage
sg                     36252  0
sr_mod                 17060  1
cdrom                  37664  1 sr_mod
sd_mod                 23428  9
ata_generic             9092  0
8139too                27648  0
ata_piix               15492  6
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
floppy                 59524  0
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
8139cp                 25088  0
mii                     6528  2 8139too,8139cp
generic                 5124  0 [permanent]
ehci_hcd               34188  0
uhci_hcd               25360  0
usbcore               134280  9 lmpcm_usb,usbhid,snd_usb_audio,snd_usb_lib,usb_storage,libusual,ehci_hcd,uhci_hcd
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
```

---

