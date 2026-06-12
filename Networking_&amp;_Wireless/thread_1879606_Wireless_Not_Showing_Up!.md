---
title: "Wireless Not Showing Up!?"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by ptom13 on 2011-11-11
Okay, I am extremely new to Ubuntu and I do not know the tech terms so PLEASE keep it simple :P

I have a Compaq Presario V6000. I had Windows 7 but I decided to go with Ubuntu after doing some research on Linux programs. I tried it out and the wireless showed up but didn't work. However, during the installation process I used an ethernet cable to install Ubuntu. Now when I click on the network icon in the top right corner there is no mention of a wireless connection (even though before there wasn't one but it still mentioned wireless) and I've been googling for an hour but I don't understand the tech talk! Please help!!

---

### Post by wildmanne39 on 2011-11-11
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ptom13 on 2011-11-12
Okay, this is what I got...

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ptom13-Presario-V6000-RG390UA-ABA 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
``````
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel modules: wl, ssb
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30bb]
    Kernel driver in use: e100

``````

lo        no wireless extensions.

eth0      no wireless extensions.


``````

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
wl                   2646601  0 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
psmouse                73673  0 
serio_raw              12990  0 
snd_rawmidi            25241  1 snd_seq_midi
i915                  505108  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
lib80211               14570  1 wl
drm                   192226  4 i915,drm_kms_helper
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
e100                   36289  0 

```

---

### Post by wildmanne39 on 2011-11-12
Hi, please do this:
```
sudo apt-get purge bcmwl-kernel-source
```
```
sudo apt-get update
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
disconnect wired connection then.
```
sudo modprobe b43
```
Thank you

---

