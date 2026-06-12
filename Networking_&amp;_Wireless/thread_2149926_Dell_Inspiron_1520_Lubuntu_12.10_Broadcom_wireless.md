---
title: "Dell Inspiron 1520 Lubuntu 12.10 Broadcom wireless problem - please help"
date: 2013-05-30
forum: Networking &amp; Wireless
---

### Post by consultme on 2013-05-30
very new to Ubuntu. Installed Lubuntu 12.10 alongside windows vista. Lubuntu working when wired through ethernet but not wireless - frustrating. tried a few steps browsing this forum but couldnt understand and still not working. can someone teach me step-by-step plain english way of solving my problem. thanking you in advance.

---

### Post by Hadaka on 2013-05-30
Hi, and welcome..
please open a terminal ctrl/alt/t
then COPY  and paste the following commands..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the output
thanks.

---

### Post by consultme on 2013-05-30
Thanks @Hadaka for your quick response
the following is what i got

jai@jai-Inspiron-1520:~$ lspci -nn | egrep '0200|0280'
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
jai@jai-Inspiron-1520:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12618  1 
arc4                   12474  2 
gpio_ich               13160  0 
joydev                 17162  0 
coretemp               13169  0 
snd_hda_codec_idt      59762  1 
dell_wmi               12602  0 
sparse_keymap          13659  1 dell_wmi
snd_hda_intel          32516  1 
snd_hda_codec         111548  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
dell_laptop            17162  0 
snd_rawmidi            25383  1 snd_seq_midi
dcdbas                 14055  1 dell_laptop
snd_seq_midi_event     14476  1 snd_seq_midi
microcode              18210  0 
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
psmouse                89552  0 
snd_timer              24412  2 snd_pcm,snd_seq
serio_raw              13032  0 
r852                   17906  0 
sm_common              16773  1 r852
b43                   347453  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   17708  0 
nand                   49497  2 r852,sm_common
nand_ids                8548  1 nand
mtd                    38603  2 sm_common,nand
nand_bch               13004  1 nand
bch                    17227  1 nand_bch
mac80211              461261  1 b43
nand_ecc               13106  1 nand
memstick               15843  1 r592
snd                    62146  11 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              175574  2 b43,mac80211
lpc_ich                16926  0 
ssb_hcd                12750  0 
bcma                   34484  1 b43
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
rfcomm                 37277  0 
bnep                   17708  2 
mac_hid                13038  0 
parport_pc             31969  0 
bluetooth             183270  10 rfcomm,bnep
ppdev                  12818  0 
i915                  461452  2 
drm_kms_helper         47304  1 i915
wmi                    18591  1 dell_wmi
drm                   238811  3 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
b44                    31327  0 
firewire_ohci          35522  0 
firewire_core          57493  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
sdhci_pci              18156  0 
sdhci                  27831  1 sdhci_pci
ssb                    50088  3 b43,ssb_hcd,b44
usb_storage            39351  1 
jai@jai-Inspiron-1520:~$ rfkill list all

---

### Post by Hadaka on 2013-05-30
Your wireless card bcm 4311 [14e4:4311] usually
works best with the linux-nonfree driver, so let's load that
and see what happens.
```
sudo modprobe -r b43
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
is it working now?

---

### Post by consultme on 2013-05-30
Brilliant. working now. thank you so much.

---

### Post by Hadaka on 2013-05-30
Glad that worked for you !
please mark this thread solved..
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

