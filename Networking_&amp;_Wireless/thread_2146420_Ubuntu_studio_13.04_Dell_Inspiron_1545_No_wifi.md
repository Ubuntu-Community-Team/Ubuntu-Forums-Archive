---
title: "Ubuntu studio 13.04 Dell Inspiron 1545 No wifi"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by Acepony on 2013-05-18
I manged to figure out how to get the words Enable WiFi but it is not click able (Not black letters.) I am not sure what to do next. I appreciate this forum community and I am sure you can help me fix it. Thanks

---

### Post by Hadaka on 2013-05-18
Hi, please open a terminal  ctrl/alt/t
then COPY and paste these commands..
one at a time..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the results
thanks.

---

### Post by Acepony on 2013-05-18
My terminal output is 

> octavian@octavian-Inspiron-1545:~$ sudo lspci -nn | egrep '0200|0280'
[sudo] password for octavian: 
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
octavian@octavian-Inspiron-1545:~$ lsmod
Module                  Size  Used by
rndis_host             13567  0 
cdc_ether              13245  1 rndis_host
usbnet                 26567  2 rndis_host,cdc_ether
snd_hrtimer            12648  1 
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
binfmt_misc            17260  1 
snd_hda_codec_idt      63896  1 
joydev                 17097  0 
arc4                   12543  2 
b43                   351918  0 
snd_usb_audio         114886  0 
snd_usbmidi_lib        24210  1 snd_usb_audio
bcma                   39645  1 b43
coretemp               13131  0 
dell_wmi               12601  0 
snd_hda_intel          38307  3 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel
gpio_ich               13236  0 
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
mac80211              526519  1 b43
snd_pcm                80890  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
dell_laptop            17161  0 
dcdbas                 14021  1 dell_laptop
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  2 snd_usbmidi_lib,snd_seq_midi
wmi                    18590  1 dell_wmi
cfg80211              436177  2 b43,mac80211
mac_hid                13037  0 
snd_seq                51280  3 snd_seq_midi_event,snd_seq_midi
microcode              18286  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  3 snd_hrtimer,snd_pcm,snd_seq
i915                  535507  2 
video                  18894  1 i915
drm_kms_helper         47545  1 i915
snd                    56485  18 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                81038  0 
drm                   228750  3 i915,drm_kms_helper
lpc_ich                16925  0 
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
serio_raw              13031  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ums_realtek            17669  0 
usb_storage            47684  1 ums_realtek
sky2                   52846  0 
ssb                    50628  1 b43
ahci                   25507  2 
libahci                26108  1 ahci
octavian@octavian-Inspiron-1545:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
octavian@octavian-Inspiron-1545:~$ 
 

---

### Post by Hadaka on 2013-05-18
hi, looks like you have a hard block..

octavian@octavian-Inspiron-1545:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

hold down the Fn key and press F2.. ONE.. time
this truns wifi on and off...after you press the F2 key
then do..
```
rfkill list all
```
to see if it cleared the hardblock
you mght also get into BIOS and do a reset to default.

---

### Post by Acepony on 2013-05-18
Thanks for the quick response's. This is a cherry on top of my day. Now to figure out how to mark this as solved or is this a mods job?

---

