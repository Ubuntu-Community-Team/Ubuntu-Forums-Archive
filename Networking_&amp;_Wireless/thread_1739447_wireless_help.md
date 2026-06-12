---
title: "wireless help"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by jetbangdink on 2011-04-25
i have just installed ubuntu 10.10 and have no internet. I cant connect via ethernet because i am no where near the router. i am using a laptop with windows xp to search the net for answers to my problem. i have three wireless usb adapters (did have 2 just found another old one i forgot about)
 
first one is: Cisco Linksys ae1000
 
second one is: NetGear wna1100
 
third is: SMC EZ connect g 802.11g 
 
when i plug in the first two nothing happens but when i plug in the third the green light comes on 
 
with all three plugged in no wireless networks show up in the wireless list 
 
heres all the usefull info 
 
joshua@joshua-HP-Compaq-dc7100-CMT-PJ363UA:~$ lsusb
Bus 005 Device 003: ID 046d:c05a Logitech, Inc. 
Bus 005 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 083a:4505 Accton Technology Corp. SMCWUSB-G 802.11bg
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 080: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]
Bus 001 Device 079: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
joshua@joshua-HP-Compaq-dc7100-CMT-PJ363UA:~$ iwconfig
 
lo no wireless extensions.
 
eth0 no wireless extensions.
 
joshua@joshua-HP-Compaq-dc7100-CMT-PJ363UA:~$ lsmod
Module Size Used by
ndiswrapper 184207 0 
ath9k 88756 0 
ath9k_common 5982 1 ath9k
ath9k_hw 292297 2 ath9k,ath9k_common
ath 8153 2 ath9k,ath9k_hw
mac80211 231541 2 ath9k,ath9k_common
cfg80211 144470 4 ath9k,ath9k_common,ath,mac80211
led_class 2633 1 ath9k
nls_iso8859_1 3261 0 
nls_cp437 4931 0 
vfat 9201 0 
fat 48240 1 vfat
usb_storage 40172 0 
nls_utf8 1069 1 
isofs 30022 1 
binfmt_misc 6599 1 
snd_hda_codec_nvhdmi 12879 4 
snd_intel8x0 25632 2 
snd_ac97_codec 99227 1 snd_intel8x0
ac97_bus 1014 1 snd_ac97_codec
snd_hda_intel 22107 0 
snd_hda_codec 87552 2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep 5040 1 snd_hda_codec
snd_pcm 71475 4 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_seq_midi 4588 0 
snd_rawmidi 17783 1 snd_seq_midi
snd_seq_midi_event 6047 1 snd_seq_midi
snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event
snd_timer 19067 2 snd_pcm,snd_seq
nouveau 516971 2 
ttm 56633 1 nouveau
drm_kms_helper 30200 1 nouveau
snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq
drm 168054 4 nouveau,ttm,drm_kms_helper
snd 49006 14 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp 26360 0 
soundcore 880 1 snd
agpgart 32011 3 ttm,drm,intel_agp
ppdev 5556 0 
i2c_algo_bit 5168 1 nouveau
snd_page_alloc 7120 3 snd_intel8x0,snd_hda_intel,snd_pcm
psmouse 59033 0 
serio_raw 4022 0 
usbhid 36882 0 
parport_pc 26058 1 
hid 67742 1 usbhid
lp 7342 0 
parport 31492 3 ppdev,parport_pc,lp
floppy 54311 0 
tg3 123310 0 
joshua@joshua-HP-Compaq-dc7100-CMT-PJ363UA:~$

---

### Post by Bucky Ball on 2011-04-26
If you can get near a router and plug in an ethernet then plug in a dongle you should have no problems. The updates should load the appropriate software/firmware for the wireless card that is in the router (if there is one) also. It is a catch 22 situation; most cards need to be installed by getting online with a cable.

---

### Post by jetbangdink on 2011-04-26
my desktop with ubuntu doesnt have a wireless card i have to use wireless usb adapters

---

