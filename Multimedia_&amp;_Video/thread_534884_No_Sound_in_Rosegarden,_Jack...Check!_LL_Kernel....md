---
title: "No Sound in Rosegarden, Jack...Check! LL Kernel...Check!"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by distortedstar on 2007-08-25
Been looking in the forums for hours, with no luck on solving this problem. Basically, I need midi output in Rosegarden4 on Ubuntu 7.04.

Jack seems great; I'm running the low-latency kernel, and all my modules appear to loaded. Just to double check, here's lsmod:

```
Module                  Size  Used by
snd_rtctimer            4384  0 
binfmt_misc            13064  1 
rfcomm                 41752  0 
l2cap                  26112  5 rfcomm
bluetooth              57444  4 rfcomm,l2cap
nfs                   243052  0 
vmnet                  39076  13 
vmmon                 114060  0 
nfsd                  219248  17 
exportfs                7040  1 nfsd
lockd                  65544  3 nfs,nfsd
sunrpc                162364  12 nfs,nfsd,lockd
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9356  0 
cpufreq_stats           7488  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12164  0 
sbs                    15528  0 
dock                   10424  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
i2c_ec                  6016  1 sbs
backlight               6784  1 asus_acpi
video                  16260  0 
button                  8720  0 
battery                10756  0 
ipv6                  274080  12 
it87                   19472  0 
hwmon_vid               4224  1 it87
i2c_isa                 6272  1 it87
eeprom                  8336  0 
lp                     12548  0 
fuse                   46996  0 
snd_intel8x0           34588  5 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            45056  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                80260  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33408  0 
snd_seq_midi            9600  0 
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
nvidia               4714420  32 
parport_pc             36644  1 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport                37576  3 ppdev,lp,parport_pc
snd                    54788  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9440  2 snd
pcspkr                  4224  0 
usblp                  14976  0 
psmouse                38792  0 
serio_raw               7940  0 
i2c_core               23424  5 i2c_ec,it87,i2c_isa,eeprom,nvidia
sis_agp                 9604  1 
agpgart                35788  2 nvidia,sis_agp
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0 
pci_hotplug            33608  1 shpchp
af_packet              24072  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  134152  1 
jbd                    63528  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23556  3 
sg                     35996  0 
sr_mod                 17188  0 
cdrom                  37664  1 sr_mod
sata_sis               10628  2 
generic                 5124  0 [permanent]
sis5513                14856  0 [permanent]
floppy                 59748  0 
ata_generic             9092  0 
ehci_hcd               34316  0 
sis900                 25088  0 
mii                     6528  1 sis900
ohci_hcd               22660  0 
usbcore               135048  4 usblp,ehci_hcd,ohci_hcd
pata_sis               14732  1 sata_sis
libata                125848  3 sata_sis,ata_generic,pata_sis
scsi_mod              143116  4 sd_mod,sg,sr_mod,libata
thermal                14856  0 
processor              31560  1 thermal
fan                     5636  0 
fbcon                  43296  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

Tried using Fluidsynth...no luck though. Maybe I'm doing something wrong there. Any ideas will be very appreciated.

---

