---
title: "Error beep is working but vlc and others not playing sound"
date: 2009-04-04
forum: Multimedia Software
---

### Post by dereferenced on 2009-04-04
Hi, I have upgraded my system to 8.10 recently and realised that Ubuntu is recognizing my sound cards but vlc/mplayer/rhythmbox/firefox, etc. are not playing sound. However in terminal if I type a wrong command, **it is playing beep sound aloud**. Also, while logging in, Ubuntu *is not* playing that regular drums sound as before in Hardy.
I have checked that my sound is not muted, and aplay -l output is as below:

> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I uninstalled and installed below packages using:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

Also, "Test" in sound preferences is not working for any of ALSA, OSS, Pulseaudio. I tried removing pulse audio and installed esound as in the below post:

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

I added medibuntu in sources.lst (as below) and installed all updates it prompted.

```
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free
```

I tried so many other things which I do not remember. But I tried rebooting my system after every change I thought it requires.

Please help. Thanks in advance.

---

### Post by dereferenced on 2009-04-05
any help from anybody?

---

### Post by sully101 on 2009-04-05
can you do aplay /somefile from the command line?
Whats the output of lsmod?

---

### Post by dereferenced on 2009-04-05
Thanks for replying. Below is the lsmod output:

> 
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
i915                   38528  2 
drm                    86056  3 i915
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
nls_iso8859_1          12032  2 
nls_cp437              13696  2 
vfat                   18816  2 
fat                    57376  1 vfat
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
evdev                  17696  11 
snd_hda_intel         384176  6 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
psmouse                45200  0 
snd_pcm                83204  4 snd_hda_intel,snd_pcm_oss
arc4                    9984  2 
battery                18436  0 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_dummy          10884  0 
ac                     12292  0 
video                  25232  0 
output                 11008  1 video
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
pcspkr                 10624  0 
mmc_core               58268  1 sdhci
tifm_7xx1              13824  0 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
tifm_core              16028  1 tifm_7xx1
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
iwl3945                98804  0 
rfkill                 17176  2 iwl3945
snd_seq_oss            38528  0 
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
snd_seq_midi           14336  0 
cfg80211               32392  2 iwl3945,mac80211
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
wmi                    14504  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 14224  0 
snd_timer              29960  4 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
ata_piix               24580  0 
ahci                   37132  4 
ohci1394               37936  0 
libata                178208  4 ata_generic,pata_acpi,ata_piix,ahci
ieee1394               96324  2 sbp2,ohci1394
e100                   41356  0 
mii                    13440  1 e100
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  4 usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  3 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


No luck with the sound but.

---

