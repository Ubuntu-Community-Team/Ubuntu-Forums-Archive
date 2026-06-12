---
title: "Wireless card doen't work in 9.04 - won't scan"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by compu73rg33k on 2009-05-26
Ever since I upgraded to 9.04 my wireless card won't scan the area for networks. When I type iwlist wlan1 scan it says "no scan results"

I tried a dlink card I had and when I was in 8.10 it also worked. Then when I upgraded to 9.04 it stopped working but I noticed that the module ath_pci was now blacklisted and ath5k was being used instead. I ran rmmod on ath5k and modprobe ath_pci and that card work.

I reinstalled my new Linksys wireless card and it didn't work with the ath_pci module. It seemed to be using rt61pci module on 8.10 but when I went into 9.04 again it seemed to be using that too and I can't seem to get the card working on 9.04.
Here's the lshw -class network from my 9.04 installation:
```
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:e5:9f:63:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:8d:51:d2:f6:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
Here's the lsmod for my 9.04 installation when the wireless card doesn't work:```
Module                  Size  Used by
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
isofs                  43688  1 
vfat                   21120  1 
fat                    65592  1 vfat
udf                    92584  0 
binfmt_misc            18572  1 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
ath_pci               108400  0 
wlan                  232736  1 ath_pci
ath_hal               225904  1 ath_pci
sbp2                   34700  0 
lp                     19588  0 
arc4                   10240  2 
ecb                    11392  2 
snd_hda_intel         557364  3 
rt61pci                32260  0 
crc_itu_t              10496  2 udf,rt61pci
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_dummy          11524  0 
rt2x00pci              16768  1 rt61pci
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
rt2x00lib              43008  2 rt61pci,rt2x00pci
snd_seq_oss            41984  0 
led_class              13064  1 rt2x00lib
snd_seq_midi           15744  0 
mac80211              251144  2 rt2x00pci,rt2x00lib
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               43168  2 rt2x00lib,mac80211
psmouse                64028  0 
snd_timer              34064  2 snd_pcm,snd_seq
ppdev                  16904  0 
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           10624  1 rt61pci
k8temp                 13440  0 
pcspkr                 11136  0 
serio_raw              14468  0 
i2c_piix4              20112  0 
joydev                 20864  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
parport_pc             45096  1 
parport                49584  3 lp,ppdev,parport_pc
shpchp                 44572  0 
usbhid                 47040  0 
usb_storage            94912  1 
ohci1394               42036  0 
r8169                  46596  0 
mii                    14464  1 r8169
ieee1394              108288  2 sbp2,ohci1394
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

Here's the lsmod for the 8.10 installation when the wireless card works:```
Module                  Size  Used by
ipv6                  314312  14 
nls_iso8859_1          13568  1 
vfat                   21120  1 
fat                    64824  1 vfat
binfmt_misc            18700  1 
af_packet              29568  4 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
rfcomm                 51104  0 
l2cap                  33280  6 bnep,rfcomm
bluetooth              70820  6 bnep,sco,rfcomm,l2cap
ppdev                  16904  0 
lp                     19588  0 
powernow_k8            23684  1 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
cpufreq_powersave      10368  0 
cpufreq_ondemand       16400  1 
freq_table             13568  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    16392  0 
video                  28948  0 
output                 11776  1 video
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
container              12288  0 
ac                     13448  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
arc4                   10368  2 
snd_hda_intel         489264  3 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
rt61pci                30208  0 
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
crc_itu_t              10496  1 rt61pci
rt2x00pci              16256  1 rt61pci
rt2x00lib              40576  2 rt61pci,rt2x00pci
snd_seq_dummy          11524  0 
rfkill                 19364  1 rt2x00lib
led_class              13192  1 rt2x00lib
snd_seq_oss            42368  0 
mac80211              253440  2 rt2x00pci,rt2x00lib
snd_seq_midi           15872  0 
joydev                 20736  0 
snd_rawmidi            34176  1 snd_seq_midi
cfg80211               37136  2 rt2x00lib,mac80211
psmouse                51612  0 
serio_raw              14596  0 
parport_pc             44200  1 
eeprom_93cx6           10752  1 rt61pci
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
evdev                  20512  8 
parport                50096  3 ppdev,lp,parport_pc
wmi                    15808  0 
k8temp                 13568  0 
i2c_piix4              17936  0 
pcspkr                 11136  0 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_core               36128  1 i2c_piix4
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 15904  0 
lmpcm_usb              13696  0 
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
battery                21128  0 
squashfs               48912  1 
loop                   26380  2 
aufs                  196968  1 
exportfs               13568  1 aufs
nls_cp437              15232  2 
isofs                  44072  1 
ext3                  150544  0 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
usb_storage            92864  1 
libusual               31784  1 usb_storage
usbhid                 39776  0 
hid                    59072  1 usbhid
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ahci                   43148  0 
ehci_hcd               48908  0 
ohci_hcd               34972  0 
pata_atiixp            14208  2 
pata_acpi              13568  0 
ata_generic            14212  0 
usbcore               175376  7 lmpcm_usb,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
libata                200160  4 ahci,pata_atiixp,pata_acpi,ata_generic
r8169                  40196  0 
scsi_mod              183160  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
ohci1394               41524  0 
ieee1394              110592  1 ohci1394
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 
```

---

