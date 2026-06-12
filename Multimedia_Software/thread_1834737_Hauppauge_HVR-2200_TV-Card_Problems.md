---
title: "Hauppauge HVR-2200 TV-Card Problems"
date: 2011-08-28
forum: Multimedia Software
---

### Post by Parrallax on 2011-08-28
Hi everyone,

I have a  Hauppauge HVR-2200 in my media center computer, and I previously have had it working fine. Unfortunately it has stopped working. It probably coincided with when I upgraded the kernel, though I can't be sure because I never use the TV card and my girlfriend didn't tell it wasn't working for a couple of weeks :P

Anyways, I went back and repeated the steps outlined here [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200") and here [http://ubuntuforums.org/showthread.php?t=1167640]("http://ubuntuforums.org/showthread.php?t=1167640") so I'm pretty sure I've installed the new drivers. After performing a reboot and running *lsmod* I get the following output:

```
Module                  Size  Used by
nfnetlink_queue         6820  1
nfnetlink               3266  2 nfnetlink_queue
nls_utf8                1069  3
cifs                  248767  6
binfmt_misc             6587  1
nf_conntrack_ipv4      10346  3
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ipt_REJECT              1928  1
xt_tcpudp               2011  2
iptable_filter          1369  1
ip_tables               9899  1 iptable_filter
xt_iprange              1357  0
xt_state                1098  3
nf_conntrack           60975  2 nf_conntrack_ipv4,xt_state
xt_mark                  711  6
xt_NFQUEUE              1832  3
x_tables               14175  7 ipt_REJECT,xt_tcpudp,ip_tables,xt_iprange,xt_state,xt_mark,xt_NFQUEUE
ppdev                   5259  0
snd_hda_codec_atihdmi     2367  1
snd_hda_codec_realtek   203376  1
snd_hda_intel          22069  2
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0
snd_seq_oss            26722  0
snd_seq_midi            4557  0
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2092908  48
agpgart                31724  1 fglrx
vga16fb                11385  1
vgastate                8961  1 vga16fb
saa7164                57766  0
serio_raw               3978  0
joydev                  8740  0
lp                      7028  0
i2c_piix4               8335  0
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
[B]dvb_core               85978  1 saa7164
tveeprom               11038  1 saa7164[/B]
shpchp                 28835  0
parport                32635  2 ppdev,lp
hid_logitech            7388  0
ff_memless              4093  1 hid_logitech
usbhid                 36110  1 hid_logitech
hid                    67096  2 hid_logitech,usbhid
r8169                  34140  0
mii                     4381  1 r8169
pata_atiixp             3148  0
ahci                   32360  1

```

and if I run *cat /proc/modules* the following lines are in there:

```
saa7164 57766 0 - Live 0xf80cb000
dvb_core 85978 1 saa7164, Live 0xf820e000
tveeprom 11038 1 saa7164, Live 0xf81e6000

```

So doesn't this mean that the card is installed correctly? Despite this I have no */dev/dvb/* folder like I should, and Kaffeine or MythTV tell me that there's no TV cards attached.

Can someone point me in the right direction to fixing this? I've had a look around all over the Linux TV site and this one, but I can't find out what went wrong.

Thanks guys.

EDIT: Sorry guys, I should mention I'm running Ubuntu 10.4.

---

### Post by thewolfman on 2011-08-28
In case you haven't already, install the "medibuntu" repo and then download and install the package "linux-firmware-nonfree", also make sure that linux firmware is installed, then re-boot and see if it fixes the problem!!.

Regards thewolfman:)

---

