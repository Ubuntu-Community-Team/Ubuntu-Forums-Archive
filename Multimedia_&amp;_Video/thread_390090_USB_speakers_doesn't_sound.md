---
title: "USB speakers doesn't sound"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by letex on 2007-03-21
Hello.

  I have just bought a pair of cheap USB speakers (best Buy.....:confused: )

  they seem to work....In preferences-> Sound, i can select it and play a test sound.

  After plug them:

> ~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 014: ID 0d8c:0001 C-Media Electronics, Inc.

 I have found any information about this device:
[ http://www.qbik.ch/usb/devices/showdev.php?id=3132 ]( http://www.qbik.ch/usb/devices/showdev.php?id=3132 )

and it's supported in kernel 2.6.10, and mine is 2.6.17

The sound driver is  snd-usb-audio,
> $ modinfo soundcore
filename: /lib/modules/2.6.17-11-generic/kernel/sound/soundcore.ko
description: Core sound module
author: Alan Cox
license: GPL
alias: char-major-14-*
vermagic: 2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:
srcversion: C2D094BCAA551D6738DF488

The device is /dev/dsp1 (/dev/dsp0 is pci sound card)

I'm wondering if the problem can be resolved by modifing this file:

> ~$ sudo vim /proc/asound/card1/oss_mixer 
VOLUME "" 0
BASS "" 0
TREBLE "" 0
SYNTH "" 0
PCM "PCM" 0
SPEAKER "" 0
LINE "" 0
MIC "" 0
CD "" 0
IMIX "" 0
ALTPCM "" 0
RECLEV "" 0
IGAIN "" 0
OGAIN "" 0
LINE1 "" 0
LINE2 "" 0
LINE3 "" 0
DIGITAL1 "" 0
DIGITAL2 "" 0
DIGITAL3 "" 0
PHONEIN "" 0
PHONEOUT "" 0
VIDEO "" 0
"/proc/asound/card1/oss_mixer" 25L, 290C                      1,1           Top

 I can paste any information more if is required....

 Thank you in advance

---

### Post by letex on 2007-03-23
I've found this link....

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard)

In this way I can setup the default sound the as the USB one or as the PCI sound car one.

I've writen a script to do this job and not have to remind the conmmands:
to exectu it:

```
bash scriptname
```
To know your Audio Card devices do:
```
$: sudo asoundconf list
Names of available sound cards:
  Live
  V8237
```

These are my Audio Cards

The script text is:
> #!/bin/bash
# This script allows you change Default Audio Card
#GNU GPL license
echo “************************************************************”
while true
do
echo ”¿What do you what to do?”
echo “[1] Enable USB sound.”
echo “[2] Enable PCI sound.”
echo “[0] Exit”
read -p "Type an option: " OPTION
echo “### ### ### ### ### ### ### ### ### ### ### ### ### ### ###”
case $OPTION in
1) sudo asoundconf set-default-card Audio  #here your USB device
echo "USB sound enabled"
break;;
2) sudo asoundconf set-default-card Intel   #here your PCI sound device
echo "PCI sound enabled"
break;;
0) echo "¡Bye…!"
break;;
*)
echo "Invalid option,type an valid option.";;
esac
done
exit 0

---

