---
title: "Logitech Quickcam Chat webcam does not work on Intrepid"
date: 2009-01-24
forum: Multimedia Software
---

### Post by atari130xe on 2009-01-24
Hello people
A friend of mine has a Logitech Quickcam Chat webcam and the system detect the webcam correctly but it does not work with aMSN neither with Kopete, but works with Cheeze, any help?

```
emiliano@emiliano-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
emiliano@emiliano-desktop:~$
```

```
emiliano@emiliano-desktop:~$ lsmod |grep spca
gspca_spca561          19328  0 
gspca_main             29312  1 gspca_spca561
videodev               41344  1 gspca_main
usbcore               149360  5 gspca_spca561,gspca_main,uhci_hcd,ehci_hcd
emiliano@emiliano-desktop:~$
```

```
emiliano@emiliano-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16904  1 
via                    49280  2 
drm                    86056  3 via
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
xt_TCPMSS              12160  1 
xt_tcpmss              10112  1 
ppdev                  15620  0 
xt_tcpudp              11008  1 
iptable_mangle         10880  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
container              11520  0 
wmi                    14504  0 
sbs                    19464  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
sbshc                  13440  1 sbs
battery                18436  0 
pppoe                  18496  2 
pppox                  11276  1 pppoe
ipv6                  263972  16 
af_packet              25728  2 
ppp_generic            32668  6 pppoe,pppox
slhc                   14208  1 ppp_generic
iptable_filter         10752  0 
ip_tables              19600  2 iptable_mangle,iptable_filter
x_tables               22916  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
ac                     12292  0 
lp                     17156  0 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                45200  0 
snd_timer              29960  2 snd_pcm,snd_seq
evdev                  17696  7 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13444  0 
gspca_spca561          19328  0 
pcspkr                 10624  0 
gspca_main             29312  1 gspca_spca561
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
videodev               41344  1 gspca_main
v4l1_compat            22404  1 videodev
i2c_viapro             15764  0 
i2c_core               31892  1 i2c_viapro
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
via_agp                16256  1 
agpgart                42184  2 drm,via_agp
ext3                  133256  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_via               16132  0 
ata_generic            12932  0 
ehci_hcd               43788  0 
uhci_hcd               30736  0 
via_rhine              30216  0 
mii                    13440  1 via_rhine
usbcore               149360  5 gspca_spca561,gspca_main,ehci_hcd,uhci_hcd
pata_acpi              12160  0 
sata_via               15492  3 
libata                178208  4 pata_via,ata_generic,pata_acpi,sata_via
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
emiliano@emiliano-desktop:~$ 


```

any help?
thanks in advance!

---

### Post by libra1780 on 2009-07-08
ran into this right now.
if you're still searching for a solution:
for kopete, if you use the gspca v2 driver, you have to preload the v4lcompat.so module for v4l backwards compatibility. after that you should get an image on device conf. gspca 2 is made for v4l2.
I'm searching for a solution from there on. my kopete has no webchat button anymore.. ](*,) 
even amsn is unable to connect, w/ router set to DMZ *headace*

greez

---

