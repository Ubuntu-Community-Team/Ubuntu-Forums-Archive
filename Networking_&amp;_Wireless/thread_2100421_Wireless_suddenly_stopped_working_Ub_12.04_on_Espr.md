---
title: "Wireless suddenly stopped working Ub 12.04 on Esprimo Mobile v5535"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by belenpatrick on 2013-01-01
Hi everyone,

The wireless connection has stopped working on ubuntu 12.04 LTS. The computer is an Esprimo Mobile v5535 (Fujitsu).
The ethernet connaction is working fine.

This is what I get when I run iwconfig, lsmod, rfkill list and sudo iwlist scan :

_**iwconfig**_
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

_**lsmod**_
Module                  Size  Used by
sis                    13175  1 
drm                   197641  2 sis
sisfb                 242226  1 sis
joydev                 17393  0 
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158479  10 rfcomm,bnep
vesafb                 13516  1 
arc4                   12473  2 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
ath5k                 145127  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  1 ath5k
psmouse                86520  0 
mac80211              436493  1 ath5k
serio_raw              13027  0 
snd                    62218  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19068  0 
soundcore              14635  1 snd
mac_hid                13077  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178877  3 ath5k,ath,mac80211
shpchp                 32325  0 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sata_sis               12700  2 
sis190                 22575  0 

_**rfkill list**_
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

_**sudo iwlist scan**_
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.





Many thanks in advance!

---

### Post by Pjotr123 on 2013-01-01
> **belenpatrick said:**
> 
_**rfkill list**_
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

It's hard blocked. Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on)

---

### Post by belenpatrick on 2013-01-02
Hi,

It worked again this morning. I cannot really explain how, as I rebooted the computer several times yesterday night.
I suppose it was a problem with the hardware.

MANY THANKS for the link, pjotr123.

---

