---
title: "WLAN Atheros AR928X vs. kernel 2.6.28-13"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by spoom_ on 2009-07-22
9.04 32bit
Wlan worked with Kernel 2.6.27-11 but with 2.6.28-13 the wlan driver seems to be not active :(

lspci:

Series
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


lsmod:

```
Module Size Used by
aes_i586 15744 2
aes_generic 35880 1 aes_i586
xts 11136 1
gf128mul 16640 1 xts
dm_crypt 20996 1
binfmt_misc 16776 1
ppdev 15620 0
bridge 56340 0
stp 10500 1 bridge
bnep 20224 2
vboxnetflt 91016 0
vboxdrv 117544 1 vboxnetflt
input_polldev 11912 0
nls_iso8859_1 12032 1
nls_cp437 13696 1
vfat 18816 1
fat 58272 1 vfat
lp 17156 0
parport 42220 2 ppdev,lp
snd_hda_intel 434100 3
snd_pcm_oss 46336 0
snd_mixer_oss 22656 2 snd_pcm_oss
snd_pcm 82948 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 10756 0
snd_seq_oss 37760 0
snd_seq_midi 14336 0
snd_rawmidi 29696 1 snd_seq_midi
snd_seq_midi_event 15104 2 snd_seq_oss,snd_seq_midi
snd_seq 56880 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo 63240 0
snd_timer 29704 2 snd_pcm,snd_seq
snd_seq_device 14988 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32 9344 1 uvcvideo
joydev 18368 0
snd 62628 13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev 41600 1 uvcvideo
soundcore 15200 2 snd
fglrx 2081668 31
v4l1_compat 21764 2 uvcvideo,videodev
sis190 26116 0
sis_agp 15360 0
snd_page_alloc 16904 2 snd_hda_intel,snd_pcm
mii 13312 1 sis190
agpgart 42696 2 fglrx,sis_agp
asus_laptop 24440 0
led_class 12036 1 asus_laptop
psmouse 61972 0
serio_raw 13316 0
pcspkr 10496 0
video 25360 0
output 11008 1 video
usb_storage 99520 0
fbcon 46112 0
tileblit 10752 1 fbcon
font 16384 1 fbcon
bitblit 13824 1 fbcon
softcursor 9984 1 bitblit 
```thanks!

---

### Post by ikkefc3 on 2009-07-22
You can install kernel 2.6.29+ or you can install the backport modules by typing
```
sudo apt-get install linux-backports-modules-jaunty

```
in a terminal.

---

### Post by spoom_ on 2009-07-22
thanks man!

---

