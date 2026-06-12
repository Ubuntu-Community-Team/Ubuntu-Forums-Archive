---
title: "Dial-up modem not detected by gnome-ppp (Smart Link 56k Voice Modem)"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by soundcore on 2012-01-25
Hi folks,

I'm having a hard time setting up my dial-up modem. I would be very thankful if someone could tell me what's wrong.

I'm using a desktop computer with an internal modem which is designed to be connected to a phone line. It's a card plugged into the motherboard through the CNR port below the PCI slots.

When I run "wvdialconf" I get an error saying "Sorry, no modem detected!"

When I do "lspci" a new line appears with the modem inserted:
"00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)"

Lines returned by "lsmod" say:
"Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
arc4                   12473  2 
nvidia               7098131  24 
rtl8187                56323  0 
snd_via82xx            24720  2 
mac80211              393459  1 rtl8187
ppdev                  12849  0 
gameport               15060  1 snd_via82xx
cfg80211              172392  2 rtl8187,mac80211
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
eeprom_93cx6           12653  1 rtl8187
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
via686a                19446  0 
snd_mpu401_uart        13865  1 snd_via82xx
binfmt_misc            17292  1 
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_viapro             12969  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              12600  1 snd
shpchp                 32356  0 
parport_pc             32114  1 
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
floppy                 60310  0 
pata_via               13398  2"


Winblows XP calls the modem "Smart Link 56k Voice Modem", "Attached to: COM3" (/dev/ttyS2 ?)

Is there any way I can make this modem work on GNU/Linux? Thanks.

---

### Post by soundcore on 2012-01-26
I had to go System tools -> Hardware and enable the Smartlink proprietary driver.

:guitar:

---

