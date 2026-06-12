---
title: "no sound of TV-card (Wintv-Go BT878)"
date: 2008-07-05
forum: Mythbuntu
---

### Post by El_Matthews on 2008-07-05
Dear,


I didn't knew there was a forum for MythBuntu, maybe here I will have more luck.

It looks like many of us have the same problem but I didn't find a solution until now (neither in the forums or on launchpad). I must be doing something wrong because I never received an answer until now so I am getting a little desperate. My MythBox is standing now for weeks on my desk unusable without any progress made.

This is my problem:
I have no sound when watching TV with different applications (mythtv, XawTV or TVTime). All other sounds in MythBuntu are working correctly.

Hardware:
WinTV-GO Card Pal-BG/I Chipset BT878KHF with Asus P4-P800-E mb.

Os:
The problem appeared when doing a fresh install of MythBuntu version 8.04. I still have a dual-boot with 7.10 (Ubuntu) on this system and in 7.10 I have sound without problems.

Test already tried:
- audio system directly connected to rear of TV-Card => getting sound of all channels.
- Connected cable of TV card output to input of soundcard => no tv sound
- installed also mixer and un-muted all sound inputs => still no sound.
- installed all pulse applications but coudn't find a setting helping me out.

Output dmesg | grep BT878
mythbox@mythbox:~$ dmesg | grep bt878
[ 48.890383] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[ 48.998130] msp3400 0-0040: MSP3415D-A2 found @ 0x80 (bt878 #0 [sw])
[ 49.159409] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[ 49.253559] bt878: AUDIO driver version 0.0.0 loaded
[ 49.689348] bt878: Bt878 AUDIO function found (0).
[ 49.689372] bt878_probe: card id=[0x13eb0070], Unknown card.
[ 49.689392] bt878: probe of 0000:02:0b.1 failed with error -22

output lsmod:
Module Size Used by
ipv6 267780 31
speedstep_lib 6532 0
cpufreq_stats 7104 0
cpufreq_ondemand 9740 0
cpufreq_conservative 8712 0
freq_table 5536 2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace 5284 0
cpufreq_powersave 2688 0
video 19856 0
output 4736 1 video
sbs 15112 0
sbshc 7680 1 sbs
dock 11280 0
container 5632 0
battery 14212 0
iptable_filter 3840 0
ip_tables 14820 1 iptable_filter
x_tables 16132 1 ip_tables
af_packet 23812 6
ac 6916 0
cx8802 19588 0
cx8800 35720 0
dst_ca 14592 0
dvb_bt8xx 17796 0
snd_cs8427 10240 0
snd_i2c 6528 1 snd_cs8427
cx88_alsa 14216 0
cx88xx 65960 3 cx8802,cx8800,cx88_alsa
dst 29704 1 dst_ca
dvb_core 81404 3 dst_ca,dvb_bt8xx,dst
w83627hf 23444 0
hwmon_vid 4352 1 w83627hf
lp 12324 0
snd_bt87x 16868 0
arc4 2944 2
ecb 4480 2
blkcipher 8324 1 ecb
bt878 11832 2 dvb_bt8xx,dst
snd_intel8x0 35356 2
snd_ac97_codec 101028 1 snd_intel8x0
tuner 42912 0
tea5767 6788 1 tuner
tda8290 12420 1 tuner
tuner_simple 10248 1 tuner
mt20xx 13192 1 tuner
tea5761 6020 1 tuner
ac97_bus 3072 1 snd_ac97_codec
tvaudio 24476 0
snd_pcm_oss 42144 0
snd_mixer_oss 17920 1 snd_pcm_oss
rt61pci 25472 0
rt2x00pci 11264 1 rt61pci
ftdi_sio 37384 1
msp3400 32160 0
rt2x00lib 22528 2 rt61pci,rt2x00pci
snd_pcm 78596 5 cx88_alsa,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
usbserial 35816 3 ftdi_sio
rfkill 8592 1 rt2x00lib
bttv 175860 2 dvb_bt8xx,bt878
input_polldev 5896 1 rt2x00lib
crc_itu_t 3072 1 rt2x00lib
ir_common 36100 2 cx88xx,bttv
mac80211 165652 3 rt61pci,rt2x00pci,rt2x00lib
compat_ioctl32 2304 2 cx8800,bttv
i2c_algo_bit 7300 2 cx88xx,bttv
snd_seq_dummy 4868 0
videobuf_dma_sg 14980 5 cx8802,cx8800,cx88_alsa,cx88xx,bttv
videobuf_core 18820 5 cx8802,cx8800,cx88xx,bttv,videobuf_dma_sg
btcx_risc 5896 5 cx8802,cx8800,cx88_alsa,cx88xx,bttv
tveeprom 16656 2 cx88xx,bttv
videodev 29440 3 cx8800,cx88xx,bttv
v4l2_common 18304 7 cx8800,cx88xx,tuner,tvaudio,msp3400,bttv,videodev
v4l1_compat 15492 2 bttv,videodev
nvidia 7825536 34
cfg80211 15112 1 mac80211
eeprom_93cx6 3200 1 rt61pci
i2c_core 24832 15 dvb_bt8xx,cx88xx,dst,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,tvaudio,msp3400,bttv,i2c_algo_bit,tveeprom,nvidia
snd_seq_oss 35584 0
snd_seq_midi 9376 0
snd_rawmidi 25760 1 snd_seq_midi
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button 9232 0
snd_timer 24836 2 snd_pcm,snd_seq
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 56996 19 snd_cs8427,snd_i2c,cx88_alsa,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp 25492 1
soundcore 8800 1 snd
snd_page_alloc 11400 3 snd_bt87x,snd_intel8x0,snd_pcm
iTCO_wdt 13092 0
parport_pc 36260 1
shpchp 34452 0
pci_hotplug 30880 1 shpchp
agpgart 34760 2 nvidia,intel_agp
evdev 13056 3
parport 37832 2 lp,parport_pc
iTCO_vendor_support 4868 1 iTCO_wdt
pcspkr 4224 0
ext3 136712 2
jbd 48404 1 ext3
mbcache 9600 1 ext3
sg 36880 0
sr_mod 17956 0
cdrom 37408 1 sr_mod
sd_mod 30720 4
pata_acpi 8320 0
ata_generic 8324 0
usbhid 31872 0
hid 38784 1 usbhid
floppy 59588 0
ata_piix 19588 3
libata 159344 3 pata_acpi,ata_generic,ata_piix
scsi_mod 151436 4 sg,sr_mod,sd_mod,libata
skge 43536 0
ehci_hcd 37900 0
uhci_hcd 27024 0
usbcore 146028 6 ftdi_sio,usbserial,usbhid,ehci_hcd,uhci_hcd
thermal 16796 0
processor 36872 1 thermal
fan 5636 0
fbcon 42912 0
tileblit 3456 1 fbcon
font 9472 1 fbcon
bitblit 6784 1 fbcon
softcursor 3072 1 bitblit
fuse 50580 1

Can somebody help me figure out what I have to do to get the sound working for this TV-Card or tell me what I am doing wrong?

Thanks in advance.

---

