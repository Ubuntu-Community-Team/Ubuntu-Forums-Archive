---
title: "Can't install soundcard drivers"
date: 2010-05-20
forum: Multimedia Software
---

### Post by Nordstroemen on 2010-05-20
Hi there.. perhaps somebody is able to give me a pointer or two.. have been following [SIZE=2][COLOR=navy]_Comprehensive Sound Problem  Solutions Guide v0.5e_[/COLOR][/SIZE] to install my soundcard, which for some reason ceased to work yesterday (have had absolutely no problems before, which makes it weird!?)

Please note im a total noob when it comes to ubuntu, so please spell any advice in the "for dummies" format.

Im on a Acer Aspire 6530
Ubuntu 10.04 (lucid)
Kernel Linux 2.6.32-22-generic
Gnome 2.30.0
Processor: AMD Turion(tm) X2 Dual-Core Mobile RM-70


Ubuntu is detecting my soundcard when I type into terminal:  
[SIZE=2]
lspci -v[/SIZE]

Result:
[I]
[SIZE=1]01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at cfeec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel[/SIZE][/I]

But when I type in;
[SIZE=2]sudo modprobe snd-hda-intel

[/SIZE]absolutely nothing happens?? 

Am i doing something wrong, am I a bad person? In short; can anyone help me?

Best
-Nordstroemen
[SIZE=2]


[/SIZE]

---

### Post by unitydesktop on 2010-05-20
download pulse aduio manager from synaptic and see what that will do for you.

---

### Post by Nordstroemen on 2010-05-20
> **unitydesktop said:**
> download pulse aduio manager from synaptic and see what that will do for you.

Not that im the expert here, but i guess that Pulse wont install my soundcard drivers for me,.. when I go to 'Sound' in 'Preferences' nothing is detected, and Alsa has worked perfect for me untill yesterday?

---

### Post by lidex on 2010-05-20
Well, something changed. Will need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
*_Also helpful is the make/model of your PC/Laptop._*
Please post text output using code tags (the # in toolbar)

---

### Post by Nordstroemen on 2010-05-21
Well this is only getting more weird.. today when i turn on my computer, the sound is working perfectly again??

Thanks for your help Lidex, still ran the terminal commands you asked me to , perhaps you can divine something out of this that I cant..

Im on an ACER Aspire 6530
Ubuntu 10.04 (lucid)
Kernel Linux 2.6.32-22-generic
Gnome 2.30.0
Processor: AMD Turion(tm) X2 Dual-Core Mobile RM-70

TERMINAL COMMANDS:

rnp@rnp-laptop:~$ uname -a
```
Linux rnp-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```rnp@rnp-laptop:~$ aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```rnp@rnp-laptop:~$ cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```rnp@rnp-laptop:~$ head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```

---

### Post by lidex on 2010-05-21
Probably an update that went into effect after a reboot. Everything looks good!

---

### Post by Nordstroemen on 2010-05-21
> **lidex said:**
> Probably an update that went into effect after a reboot. Everything looks good!

Fantastic.. thank you very much for your time and help..much appreciated!

---

