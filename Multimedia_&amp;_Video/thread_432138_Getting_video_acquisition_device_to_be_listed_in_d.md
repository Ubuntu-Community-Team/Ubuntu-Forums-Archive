---
title: "Getting video acquisition device to be listed in /dev"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by mac.ryan on 2007-05-03
I have a Pinnacle Studio PCI-500 (version 10) that worked fine under windows, but that I can't get to work under linux.

The symptom is that acquisition/capture programs would expect to find a device in /dev/video0, while this is not the case. My understanding of the problem is that I miss some kind of driver/package that would allow the card to be recognised correctly and therefore being listed in the /dev tree.

Here is what lspci says about my card:

```
01:07.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
01:07.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Unknown device 0015
```I wonder if I miss to have some kernel module enabled... Just in case, here is the output of lsmod:

```
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vboxdrv                31112  0 
ppdev                  10116  0 
fglrx                 540004  11 
agpgart                35400  1 fglrx
powernow_k8            16064  1 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
cpufreq_powersave       2688  0 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
video                  16388  0 
battery                10756  0 
asus_acpi              17308  0 
ac                      6020  0 
container               5248  0 
button                  8720  0 
dock                   10268  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  5888  1 sbs
ipv6                  268704  14 
ndiswrapper           194608  0 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  1 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               7940  0 
pcspkr                  4224  0 
psmouse                38920  0 
soundcore               8672  1 snd
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
af_packet              23816  2 
k8temp                  6656  0 
i2c_nforce2             6784  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_core               22784  2 i2c_ec,i2c_nforce2
tsdev                   8768  0 
evdev                  11008  3 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  4 
amd74xx                15260  0 [permanent]
generic                 5124  0 [permanent]
sata_nv                20868  3 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ata_generic             9092  0 
forcedeth              46728  0 
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  4 ndiswrapper,ehci_hcd,ohci_hcd
libata                125720  2 sata_nv,ata_generic
scsi_mod              142348  4 sbp2,sg,sd_mod,libata
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```Many thanks to anybody who could give me anything (from an hint to a complete how-to)... I spent the last 2 hours googleing without success... :(

---

