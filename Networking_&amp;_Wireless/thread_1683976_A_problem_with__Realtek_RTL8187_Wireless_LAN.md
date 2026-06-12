---
title: "A problem with  Realtek RTL8187 Wireless LAN"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by folk on 2011-02-08
hi guys , I had a problem since I installed Ubuntu 10.10 . The problem is that there is no INTERNET CONNECTION . I connect with Realtek RTL8187 Wireless LAN . "Ubuntu" says DEVICE NOT MANAGED !!!!
COULD YOU PLEASE HELP ME :confused:

---

### Post by gordintoronto on 2011-02-08
Is that a USB device? Does it appear when you open Accessories/Terminal and enter:
lsusb

Is it possible to have a temporary wired connection and run Administration/Additional Driver?

What type of computer?

---

### Post by walt.smith1960 on 2011-02-08
As Gordon asks, lsusb.  There are different RTL8187 chipsets.  I have an adapter that uses the RTL8187B-it's perfect plug & play.  There's a user with an open thread which has an RTL8187L that is being difficult.  I wish chipset manufacturers wouldn't do that :mad:.

---

### Post by folk on 2011-02-09
Thanks for your help :
My PC is Acer Extensa  5235 laptop .
The reselt of "lsusb " in terminal is 






folk@folk-Extensa-5235:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a103 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by gordintoronto on 2011-02-09
According to this web page:
[http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)
Linux supports that wireless adapter.

Do you have experience with setting up a wireless connection in Ubuntu? There are tutorials on Youtube.

---

### Post by folk on 2011-02-10
thanks

---

### Post by TBABill on 2011-02-10
Can you type the output you get when you type ```
lsmod
``` in a terminal? That's LSMOD in lowercase. Just want to make sure you don't have conflicting drivers.

---

### Post by folk on 2011-02-10
Hello , God helps me "device not managed" . What shall I do to connect to internet , it becomes as a dream as unachieved desire .
the result is 



folk@folk-Extensa-5235:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
rfcomm                 33811  0 
parport_pc             26058  0 
ppdev                   5556  0 
sco                     7998  0 
bnep                    9542  0 
l2cap                  37008  4 rfcomm,bnep
snd_hda_codec_conexant    29736  1 
joydev                  8735  0 
arc4                    1165  4 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ath9k                  88756  0 
i915                  290938  3 
snd_seq_midi            4588  0 
rtl8187                51470  0 
snd_rawmidi            17783  1 snd_seq_midi
ath9k_common            5982  1 ath9k
snd_seq_midi_event      6047  1 snd_seq_midi
ath9k_hw              292297  2 ath9k,ath9k_common
drm_kms_helper         30200  1 i915
ath                     8153  2 ath9k,ath9k_hw
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231541  3 rtl8187,ath9k,ath9k_common
snd_timer              19067  2 snd_pcm,snd_seq
uvcvideo               55847  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  10969  0 
drm                   168054  4 i915,drm_kms_helper
bluetooth              50500  5 rfcomm,sco,bnep,l2cap,btusb
videodev               43098  1 uvcvideo
cfg80211              144470  5 ath9k,rtl8187,ath9k_common,ath,mac80211
v4l1_compat            13359  2 uvcvideo,videodev
eeprom_93cx6            1345  1 rtl8187
intel_agp              26360  2 i915
snd                    49006  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
led_class               2633  2 ath9k,rtl8187
video                  18712  1 i915
psmouse                59033  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
atl1c                  29949  0 
folk@folk-Extensa-5235:~$

---

