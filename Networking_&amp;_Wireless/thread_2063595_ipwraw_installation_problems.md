---
title: "ipwraw installation problems"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by tsiric17 on 2012-09-27
Hi ! 
Im kinda new to ubuntu and linux ( i have itlika e couple of months), and im trying to test my network security using aircrcak-ng suite...
everything seems to work fine except for airplay-ng.

So ive read somewhere that i need to install a different driver like ipwraw which will hopefully make it work... Im currently using iwl3945 and my card is "Wireless Intel(R) PRO/wireless 3945abg network connection...

Im trying to remove or blacklist my old drivers and install ipwraw but i cant seem to install it...
here is a script when using lsmod command

Module                  Size  Used by
ipheth                 13278  0 
dm_crypt               22528  1 
snd_hrtimer            12648  1 
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
dell_wmi               12601  0 
bnep                   17830  2 
sparse_keymap          13658  1 dell_wmi
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
arc4                   12473  0 
hid_logitech_dj        18178  0 
psmouse                87213  0 
snd_hda_codec_idt      60251  1 
uvcvideo               67203  0 
snd_hda_intel          32765  3 
iwl_legacy             71134  0 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
mac80211              436455  1 iwl_legacy
binfmt_misc            17292  1 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
cfg80211              178679  2 iwl_legacy,mac80211
snd_seq_midi           13132  0 
r852                   17901  0 
r592                   17808  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62064  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  1 hid_logitech_dj
hid                    77367  2 hid_logitech_dj,usbhid
nouveau               708260  3 
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
b44                    31412  0 
ssb                    50691  1 b44
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  2 dell_wmi,mxm_wmi
video                  19068  1 nouveau

I have no idea what ive done and when i try to follow instructions to install ipwraw i get this error ( after using cd command and make command)

tomislav@tomislav:~$ cd ipwraw-ng
tomislav@tomislav:~/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/3.2.0-29-generic/build M=/home/tomislav/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/tomislav/ipwraw-ng/ipwraw.o
Assembler messages:
Fatal error: can't create /home/tomislav/ipwraw-ng/.tmp_ipwraw.o: Permission denied
/home/tomislav/ipwraw-ng/ipwraw.c:43:27: fatal error: net/ieee80211.h: No such file or directory
compilation terminated.
make[2]: *** [/home/tomislav/ipwraw-ng/ipwraw.o] Error 2
make[1]: *** [_module_/home/tomislav/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make: *** [modules] Error 2

Im running ubuntu 12.04 32bit
linux kernel 3.2.0-29 generic
Gnome 3.4.2
I have 2.0 Gb of DDR2 memory and a Intel® Core™2 Duo CPU T7300 @ 2.00GHz × 2 
if you need addiotional information i wiil try to provide, just help me clear up the mess i made...

Thx in advance

---

