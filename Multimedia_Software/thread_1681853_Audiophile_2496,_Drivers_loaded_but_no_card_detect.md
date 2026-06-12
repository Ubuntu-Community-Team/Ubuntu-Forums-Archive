---
title: "Audiophile 2496, Drivers loaded but no card detected"
date: 2011-02-04
forum: Multimedia Software
---

### Post by dulouz on 2011-02-04
Hi, I've read over some other posts regarding m-audio audiophile 2496, but none that I have seen are quite the same problem. This card use to work on my 9.04 system but I recently built a new computer and installed 10.10. It also works in Windows7 so I know the card is functional. 

I am running ubuntu 10.10 upgraded to kubuntu 10.10 with the kde 4.6 backports. I am also running 2.6.36-020636-generic on an intel x86_64 system. 

I have disabled the onboard sound card through bios (i think, the bios sort of sucks). I've added 
blacklist snd_hda_intel
to /etc/modprobe.d/blacklist.conf since that seemed to be the driver for the other card. 

Below is the output of several commands:

> lsmod | grep snd
```
snd_ice1712            70040  0 
snd_ice17xx_ak4xxx      3115  1 snd_ice1712
snd_ak4xxx_adda         9741  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              8225  1 snd_ice1712
snd_ac97_codec        125009  1 snd_ice1712
snd_pcm                91964  2 snd_ice1712,snd_ac97_codec
snd_page_alloc          8740  1 snd_pcm
ac97_bus                1442  1 snd_ac97_codec
snd_i2c                 5695  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6802  1 snd_ice1712
snd_seq_midi            5914  0 
snd_rawmidi            21856  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7195  1 snd_seq_midi
snd_seq                57128  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24248  2 snd_pcm,snd_seq
snd_seq_device          6816  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64310  11 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                                                                                                                    
soundcore               1240  1 snd
```> aplay -l
aplay: device_list:235: no soundcards found...

>  lspci -v | grep -i audio
```
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
04:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile 2496

```I think that nVidia Corporation is part of the onboard device.

> cat /proc/asound/cards 
--- no soundcards ---

> envy24control 
No ICE1712 cards found

So it looks like the system somewhat knows that I have an Audiophile 2496 but not quite. 

For kicks, i've added:
options snd-ice1712 model=audiophile index=0

to /etc/modprobe.d/alsa-base.conf, but it did nothing noticeable. 

I've also added:
```
slave.format S32_LE
slave.channels 10
```to /usr/share/alsa/cards/ICE1712.conf in the iCE1712.pcm.front.0 section as mentioned some place else.  This also had no noticeable effect. 

lastly, 

./alsa-info.sh --stdout
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.QAMu33hfVK/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Feb  5 02:19:36 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      P67A-UD4
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.36-020636-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
04:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

01:00.1 0403: 10de:0beb (rev a1)
        Subsystem: 1462:2321
--
04:00.0 0401: 1412:1712 (rev 02)
        Subsystem: 1412:d634


!!Modprobe options (Sound related)
!!--------------------------------

snd-ice1712: model=audiophile index=0
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 3 Feb  4 19:02 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Feb  4 19:02 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aesni_intel
cryptd
aes_x86_64
aes_generic
binfmt_misc
parport_pc
ppdev
dm_crypt
nvidia
snd_ice1712
snd_ice17xx_ak4xxx
snd_ak4xxx_adda
snd_cs8427
snd_ac97_codec
snd_pcm
snd_page_alloc
ac97_bus
snd_i2c
snd_mpu401_uart
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
lp
xhci_hcd
shpchp
parport
floppy
usbhid
r8169
mii
hid
intel_agp


!!ALSA/HDA dmesg
!!------------------
```My next step is to try to get the "Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)" to not show up when doing   "lspci -v | grep -i audio". The other onboard sound card use to show up there but stopped after disabling in bios and blacklisting it (did them simultaneously so I don't know which did it). So perhaps that will help.

Failing that, does anyone have any ideas?

Many thanks

[Edit: "Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)" seems to be part of the HDMI input on the video card. I don't think I'll mess with that at the moment."]

---

