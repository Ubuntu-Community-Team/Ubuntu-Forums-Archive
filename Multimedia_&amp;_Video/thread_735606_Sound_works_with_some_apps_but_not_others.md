---
title: "Sound works with some apps but not others"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by RRixas on 2008-03-25
I just installed Ubuntu 7.10 and now some of my applications (wine, mplayer, and pidgin specifically) don't play sound.  Others do (gxine, aplay)

 I was previously running XUbuntu 7.04 and had sound problems there too.  Could it be a hardware problem?  I have two sound cards.  One is a CL Sounblaster Audigy and the other is onboard (Intel-something).

After running "aplay -l", I saw that my sound card was listed.

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I followed the advice of the sound troubleshooter post and checked my "alsamixer" but everything was unmuted as it should be.  Volumes turned up.

Here is a readout of my lsmod:

Module                  Size  Used by
snd_rtctimer            4384  0 
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
ipv6                  273892  8 
speedstep_lib           6404  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
video                  18060  0 
ac                      6148  0 
container               5504  0 
sbs                    19592  0 
dock                   10656  0 
button                  8976  0 
battery                11012  0 
af_packet              24840  2 
sbp2                   24072  0 
lp                     12580  0 
analog                 13344  0 
snd_intel8x0           34972  1 
gameport               16776  1 analog
psmouse                39952  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
quickcam               73124  0 
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
serio_raw               8068  0 
videodev               29312  1 quickcam
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev
snd_ca0106             34720  0 
snd_ac97_codec        100644  2 snd_intel8x0,snd_ca0106
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipaq                   34584  0 
usbserial              34920  1 ipaq
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
usbhid                 29536  0 
hid                    28928  1 usbhid
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
acx                    98692  0 
snd_pcm                80388  4 snd_intel8x0,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24324  3 snd_rtctimer,snd_seq,snd_pcm
ac97_bus                3200  1 snd_ac97_codec
nvidia               6221648  24 
i2c_core               26112  1 nvidia
snd                    54660  13 snd_intel8x0,snd_seq_oss,snd_ca0106,snd_ac97_codec,snd_rawmidi,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_intel8x0,snd_ca0106,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
evdev                  11136  4 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  6 
b44                    28300  0 
mii                     6528  1 b44
ata_piix               17540  5 
floppy                 60004  0 
sata_promise           13956  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  3 ata_piix,sata_promise,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 quickcam,ipaq,usbserial,usbhid,acx,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

