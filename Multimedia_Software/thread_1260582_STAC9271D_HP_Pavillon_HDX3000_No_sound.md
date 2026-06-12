---
title: "STAC9271D HP Pavillon HDX3000 No sound"
date: 2009-09-07
forum: Multimedia Software
---

### Post by David Touzeau on 2009-09-07
Help, i don't understand... 
My HP Pavillon HDX3000 run in Ubuntu 9.04
Everything works except the sound.
It seems that the kernel see devices but no sound exit from.

I have compiled latest alsa drivers 1.0.21 by using this wiki 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

i have checked in alsamixer that all parts are switched to "00" instead "MM"

but the sound didn't want to run.

here it is some informations 

alsamixer output
----------------------------------
Card: HDA Intel                                                                                                                                                                                                   F1:              &#9474;
Chip: SigmaTel STAC9271D  

dmesg
----------------------------------
   13.421312] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   13.500123] Clocksource tsc unstable (delta = -122909431 ns)
[   13.656309] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.657277] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.660287] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.661278] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.664280] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   13.665280] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   13.667270] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16

aplay -L
----------------------------------

front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


modprobe.conf
----------------------------------

../..
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel


/etc/modprobe.d/50-sound.conf
----------------------------------
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel


speaker-test 1.0.21
----------------------------------

Le périphérique de lecture est default
Les paramètres du flux sont 48000Hz, S16_LE, 1 canaux
Utilisation de 16 octaves de bruit rose
Taux fixé à 48000Hz (demandé 48000Hz)
Taille du tampon entre 2048 et 8192
Taille de la periode entre 1024 et 1024
Utilisation du tampon maximal 8192
Périodes = 4
La durée de la période à été définie= 1024
La taille du tampon à été définie = 8192
 0 - Avant Gauche
Temps par période = 2,833779
 0 - Avant Gauche
Temps par période = 2,986533

---

