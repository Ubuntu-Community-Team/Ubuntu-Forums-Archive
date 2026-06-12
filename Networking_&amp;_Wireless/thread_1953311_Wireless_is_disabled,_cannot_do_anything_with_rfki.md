---
title: "Wireless is disabled, cannot do anything with rfkill"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by danny16 on 2012-04-06
I have an old HP-500 laptop running Ubuntu 10.04, I downgraded from 11.10 in the hopes of maybe fixing this problem. It is telling me that the "Wireless is disabled". 

After searching up many threads, I still have had no success unblocking it through the rfkill commands. To make matters worse, it seems as though "rfkill list all" or "rfkill unblock all" orsimilar commands have now stopped working; I enter it into the terminal and nothing comes up, just a new line. Maybe I am just using the commands wrong... has anyone had this problem before and know how to fix it?

Thank you in advance :)

EDIT: All good, it was simply disabled in the bios menu..... thank you for the help :)

---

### Post by praseodym on 2012-04-06
Hi,

please show the outputs of

```
lsmod
iwconfig
lspci -nnk | grep -iA2 net
```
Try a BIOS reset.

---

### Post by danny16 on 2012-04-06
lsmod returned:

Module                  Size  Used by
aes_i586                7268  254 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
joydev                  8740  0 
dm_crypt               11331  0 
pcmcia                 30784  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               135216  0 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
libipw                 39896  1 ipw2200
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5046  2 ipw2200,libipw
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
psmouse                63677  0 
serio_raw               3978  0 
ppdev                   5259  0 
parport_pc             25962  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  289683  3 
drm_kms_helper         29329  1 i915
drm                   163779  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
e100                   28211  0 
mii                     4381  1 e100
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp


iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and lspci -nnk | grep -iA2 net gave:


02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200
--
02:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 03)
    Kernel driver in use: e100
    Kernel modules: e100

---

