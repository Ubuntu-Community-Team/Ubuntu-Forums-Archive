---
title: "Sound not working but sound card detected"
date: 2009-01-03
forum: Multimedia Software
---

### Post by something132 on 2009-01-03
i am stuck!!!! i have recently installed linux and have had problems with sound. i am not very good at linux yet but can you help me? i have posted this problem at another forum so all the info is there. link to that is;
[http://www.techsupportforum.com/alternative-computing/linux-support/318095-linux-help-sound-not-working-but-sound-card-detected.html#post1830209](http://www.techsupportforum.com/alternative-computing/linux-support/318095-linux-help-sound-not-working-but-sound-card-detected.html#post1830209)
please visit and look at info there.:popcorn:
some of you may not be bothered to go there so here is is;
lsmod
Module Size Used by
af_packet 23812 4
ipv6 267780 8
binfmt_misc 12808 1
radeon 124192 2
drm 82452 3 radeon
rfcomm 41744 2
l2cap 25728 13 rfcomm
bluetooth 61156 4 rfcomm,l2cap
ppdev 10372 0
speedstep_lib 6532 0
cpufreq_conservative 8712 0
cpufreq_ondemand 9740 0
cpufreq_userspace 5284 0
cpufreq_powersave 2688 0
cpufreq_stats 7104 0
freq_table 5536 2 cpufreq_ondemand,cpufreq_stats
sbs 15112 0
container 5632 0
dock 11280 0
video 19856 0
output 4736 1 video
sbshc 7680 1 sbs
battery 14212 0
iptable_filter 3840 0
ip_tables 14820 1 iptable_filter
x_tables 16132 1 ip_tables
aes_i586 33536 0
dm_crypt 15364 0
dm_mod 62660 1 dm_crypt
ac 6916 0
sbp2 24072 0
lp 12324 0
evdev 13056 4
parport_pc 36260 1
parport 37832 3 ppdev,lp,parport_pc
psmouse 40336 0
serio_raw 7940 0
pcspkr 4224 0
arc4 2944 2
usbhid 32128 0
ecb 4480 2
blkcipher 8324 1 ecb
hid 38784 1 usbhid
usblp 15872 0
rt61pci 25472 0
rt2x00pci 11264 1 rt61pci
rt2x00lib 22528 2 rt61pci,rt2x00pci
rfkill 8596 1 rt2x00lib
snd_hda_intel 344856 3
input_polldev 5896 1 rt2x00lib
snd_pcm_oss 42144 0
snd_mixer_oss 17920 2 snd_pcm_oss
crc_itu_t 3072 1 rt2x00lib
mac80211 165652 3 rt61pci,rt2x00pci,rt2x00lib
cfg80211 15112 1 mac80211
snd_pcm 78596 2 snd_hda_intel,snd_pcm_oss
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm
snd_hwdep 10500 1 snd_hda_intel
eeprom_93cx6 3200 1 rt61pci
snd_seq_dummy 4868 0
snd_seq_oss 35584 0
snd_seq_midi 9376 0
snd_rawmidi 25760 1 snd_seq_midi
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
iTCO_wdt 13092 0
iTCO_vendor_support 4868 1 iTCO_wdt
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24836 2 snd_pcm,snd_seq
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 56996 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button 9232 0
intel_agp 25492 0
soundcore 8800 2 snd
shpchp 34452 0
pci_hotplug 30880 1 shpchp
agpgart 34760 2 drm,intel_agp
ext3 136840 1
jbd 48404 1 ext3
mbcache 9600 1 ext3
sg 36880 0
sr_mod 17956 0
cdrom 37408 1 sr_mod
sd_mod 30720 3
pata_acpi 8320 0
ata_generic 8324 0
usb_storage 73664 0
libusual 19108 1 usb_storage
8139too 27520 0
ohci1394 33584 0
ata_piix 19588 2
ieee1394 93752 2 sbp2,ohci1394
8139cp 24704 0
mii 6400 2 8139too,8139cp
libata 159344 3 pata_acpi,ata_generic,ata_piix
scsi_mod 151436 6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ehci_hcd 37900 0
uhci_hcd 27024 0
usbcore 146412 7 usbhid,usblp,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal 16796 0
processor 37384 1 thermal
fan 5636 0
fbcon 42912 0
tileblit 3456 1 fbcon
font 9472 1 fbcon
bitblit 6784 1 fbcon
softcursor 3072 1 bitblit
fuse 50708 1


uname -r

2.6.24-21-generic

modinfo soundcore


filename: /lib/modules/2.6.24-21-generic/kernel/sound/soundcore.ko
alias: char-major-14-*
license: GPL
author: Alan Cox
description: Core sound module
srcversion: 548AA54AF08207316C104F8
depends:
vermagic: 2.6.24-21-generic SMP mod_unload 586

modinfo snd-HDA-intel


filename: /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
description: Intel HDA driver
license: GPL
srcversion: 788923729243CAF84C8707E
alias: pci:v000010DEd00000AC3sv*sd*bc*sc*i*
alias: pci:v000010DEd00000AC2sv*sd*bc*sc*i*
alias: pci:v000010DEd00000AC1sv*sd*bc*sc*i*
alias: pci:v000010DEd00000AC0sv*sd*bc*sc*i*
alias: pci:v000010DEd000007FDsv*sd*bc*sc*i*
alias: pci:v000010DEd000007FCsv*sd*bc*sc*i*
alias: pci:v000010DEd00000777sv*sd*bc*sc*i*
alias: pci:v000010DEd00000776sv*sd*bc*sc*i*
alias: pci:v000010DEd00000775sv*sd*bc*sc*i*
alias: pci:v000010DEd00000774sv*sd*bc*sc*i*
alias: pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias: pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias: pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias: pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias: pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias: pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias: pci:v000010DEd00000371sv*sd*bc*sc*i*
alias: pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias: pci:v000010B9d00005461sv*sd*bc*sc*i*
alias: pci:v00001039d00007502sv*sd*bc*sc*i*
alias: pci:v00001106d00003288sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA48sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA40sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA38sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA30sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA28sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA20sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA18sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA10sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA08sv*sd*bc*sc*i*
alias: pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias: pci:v00001002d0000970Fsv*sd*bc*sc*i*
alias: pci:v00001002d0000960Fsv*sd*bc*sc*i*
alias: pci:v00001002d00007919sv*sd*bc*sc*i*
alias: pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias: pci:v00001002d00004383sv*sd*bc*sc*i*
alias: pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias: pci:v00008086d0000811Bsv*sd*bc*sc*i*
alias: pci:v00008086d00003A6Esv*sd*bc*sc*i*
alias: pci:v00008086d00003A3Esv*sd*bc*sc*i*
alias: pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias: pci:v00008086d0000293Esv*sd*bc*sc*i*
alias: pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias: pci:v00008086d0000269Asv*sd*bc*sc*i*
alias: pci:v00008086d000027D8sv*sd*bc*sc*i*
alias: pci:v00008086d00002668sv*sd*bc*sc*i*
depends: snd-pcm,snd-page-alloc,snd,snd-hwdep
vermagic: 2.6.24-21-generic SMP mod_unload 586
parm: power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm: index:Index value for Intel HD audio interface. (array of int)
parm: id:ID string for Intel HD audio interface. (array of charp)
parm: enable:Enable Intel HD audio interface. (array of bool)
parm: model:Use the given board model. (array of charp)
parm: position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (array of int)
parm: probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm: single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm: enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm: power_save_controller:Reset controller in power save mode. (bool)


ls -1 /proc/asound/card0/

codec#2
id
oss_mixer
pcm0c
pcm0p
pcm4c

nothing is muted.....:popcorn:

---

### Post by something132 on 2009-01-03
that should be enough.... i have posted this everywhere and no one has helped me.

---

### Post by something132 on 2009-01-03
and by the way i am on ubuntu v. 8.10

---

### Post by something132 on 2009-01-03
DAMN no one wants to help me out

---

### Post by HamHamT on 2009-01-03
so i didnt even bother attempting to dechiper that block of text you posted but it took me 3-4 days of research to fix a rather simple problem on my sound

markbuntu posted a thread that troubleshoots every (should be) possible problem that you could have with your sound so give that a search

i dont know what sound card you using, but if by chance you are using a soundblaster audigy make sure that audigy analog/digital output jack (under volume control>switches) is not checked and your (under system>preferences>sound) is the first possible sound card w/ ALSA

search the for the thread though big guy

---

### Post by something132 on 2009-01-04
> **HamHamT said:**
> so i didnt even bother attempting to dechiper that block of text you posted but it took me 3-4 days of research to fix a rather simple problem on my sound

markbuntu posted a thread that troubleshoots every (should be) possible problem that you could have with your sound so give that a search

i dont know what sound card you using, but if by chance you are using a soundblaster audigy make sure that audigy analog/digital output jack (under volume control>switches) is not checked and your (under system>preferences>sound) is the first possible sound card w/ ALSA

search the for the thread though big guy

yea i viewed his page... it couldnt help me much. i appreciate your help but i am getting no where. and btw i think i am messing up my ubuntu.......:confused::popcorn:

---

