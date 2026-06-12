---
title: "alsamixer won't start: cannot load mixer controls"
date: 2010-09-20
forum: Multimedia Software
---

### Post by semteXKG on 2010-09-20
Hello.

OS: fresh installed 10.04.1 64 Bit,
Kernel: 2.6.32-24-generic

Mainboard: Gigabyte GA-G41MT-ES2L with 
# 2/4/5.1/7.1-channel
# Realtek ALC888B codec 

ALSA: Alsa Update Script ([http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)), 
> cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep 20 2010 for kernel 2.6.32-24-generic (SMP).

> apex@soundbox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> apex@soundbox:~$ head -n 1 /proc/asound/card0/codec* 
Codec: Realtek ALC887


> aplay /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
- works, i hear the sound

> apex@soundbox:~$ alsamixer
cannot load mixer controls: Invalid argument

> apex@soundbox:~$ amixer
amixer: Mixer default load error: Invalid argument

I've added 
> options snd-hda-intel index=0 model=auto
to the /etc/modprobe.d/alsa-base.conf

any ideas why alsamixer and amixer aren't working? i'm more or less out of ideas... 

amixer controls throws:
> 
apex@soundbox:~$ amixer controls
numid=26,iface=MIXER,name='Master Playback Switch'
amixer: Control default snd_hctl_elem_info error: Invalid argument


Help greatly appreciated!

Thx
Klaus

---

### Post by zeis on 2010-10-27
alsamixer won't start:  cannot load mixer controls  Hello.  Same with    OS: Fresh installed 10.10 64 bits, Kernel: 2.6.35-22-generic   Mainboard: MSI GF615M-P33  V. 1.3  # 7.1-channel  # Realtek ALC887 codec  # Compliant with Azalia 1.0 spec

---

### Post by zeis on 2010-11-01
Found fix,


 in /etc/modprobe.d/alsa-base.conf, add


 options snd-hda-intel model=generic
 

but I do not like, I can not use the other channels.
 

Waiting for a real solution
 

Thanks.

---

### Post by TitanFlyer on 2010-11-30
> **zeis said:**
> Found fix,


 in /etc/modprobe.d/alsa-base.conf, add


options snd-hda-intel model=generic




Zeis ...  thanks for posting this. I just built a PC
with a Gigabyte GA-M68M-2SP and an AMD Sempron 140
processor and couldn't get the sound to work. This entry
got it going.

---

