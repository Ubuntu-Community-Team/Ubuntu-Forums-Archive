---
title: "How to enable IPv6 in kubuntu 9.04"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by test006 on 2009-06-18
Hi,
I have kubuntu running as my desktop. It seems to me that IPv6 is disabled by default. How do i enable IPv6 on kubuntu 9.04.
Here my lsomd output:
[PHP]
lsmod
Module                  Size  Used by
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  4 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               21712  0 
pcspkr                 11136  0 
nvidia               8123768  36 
intel_agp              39408  0 
usbhid                 47040  0 
iTCO_vendor_support    12420  1 iTCO_wdt
snd                    78792  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_
seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
floppy                 75816  0 
atl1                   45448  0 
mii                    14464  1 atl1
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
[/PHP] 

Thanks in advance

---

### Post by papangul on 2009-06-18
1. Ensure that there is a line like> alias net-pf-10 ipv6 in the /etc/modprobe.d/aliases file.

2. Ensure there isn't a line like> blacklist ipv6 in the /etc/modprobe.d/blacklist file.

Hope this will solve the problem.

---

