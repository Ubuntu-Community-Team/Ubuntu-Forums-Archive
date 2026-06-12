---
title: "/dev/video0 not found"
date: 2009-04-04
forum: Multimedia Software
---

### Post by josergc on 2009-04-04
Hello everybody,

I have an old usb webcam and when I plug it with my Ubuntu 8.10. Executing lsusb I got:

Bus 005 Device 002: ID 1019:0f62 Elitegroup Computer Systems (ECS) 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera <--- This is my webcam
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

but no /dev/video*

I also execute lsmod with this output:

Module                  Size  Used by
videodev               41344  0 
v4l1_compat            22404  1 videodev
i915                   38528  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
wmi                    14504  0 
sbs                    19464  0 
container              11520  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
ipv6                  263972  21 
af_packet              25728  4 
ppp_generic            32668  0 
slhc                   14208  1 ppp_generic
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_hda_intel         384176  6 
iwl3945                98804  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  2 snd_pcm_oss
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
battery                18436  0 
led_class              12164  1 iwl3945
snd_seq_dummy          10884  0 
evdev                  17696  9 
cfg80211               32392  2 iwl3945,mac80211
ac                     12292  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
video                  25232  0 
output                 11008  1 video
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                45200  0 
serio_raw              13444  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  2 snd
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
button                 14224  0 
pcspkr                 10624  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
usb_storage            82752  0 
libusual               30356  1 usb_storage
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  5 sd_mod,sr_mod,sg,usb_storage,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
r8169                  36100  0 
mii                    13440  1 r8169
uhci_hcd               30736  0 
usbcore               149360  6 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

Any idea about how to fix this issue?

Thank you!

---

### Post by itix on 2009-04-05
are you sure this is an issue?

I don't get any /dev/video0 either when I plug my webcam into the USB, and yet I can still use it in "cheese" (sudo apt-get install cheese).

---

