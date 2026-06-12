---
title: "Laptop sound"
date: 2006-05-11
forum: Multimedia &amp; Video
---

### Post by KiLLeR_WoMBaT on 2006-05-11
Can I totally remove every and anything that has absolutely anything to do with sound on my laptop?

I had sound when I first installed...now it's only at the login screen and once gnome starts up I got nothing.

I have tried the troubleshooting guide--nothing
I have posted numerous threads asking for help--nothing
It has now been months and still no sound.

I can not and do not want to reinstall Ubuntu just to get the sound working...it would wreck things I have.

My idea is to totally remove EVERYTHING about sound and then maybe try to start over fresh with just the sound.

What do I delete and modify to TOTALLY remove anything that has anything to do with sound drivers, modules, applications, settings, etc?

---

### Post by Sef on 2006-05-11
This is for Ubuntu: If you have another wm, then you will have to adjust it a bit.

First a few questions:

1) Have you installed the codecs?  

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

2) Have you clicked on the speaker icon and opened 'Open Volume Control', and checked that the speakers are not muted?

3a)  If yes, to both of those questions and still no sound then Open the Terminal (Applications > Accessories > Terminal)

3b) Copy and paste the results of the below commands in the thread:

3b-1) cat /proc/asound/cards

3b-2) sudo gedit /etc/modprobe.d/alsa-base

Note: I won't have much access to the net for about 2 days, so please be patient, if I don't answer back.  Drop me a private message to remind me to finish helping you, if you'd like.

---

### Post by KiLLeR_WoMBaT on 2006-05-11
cat /proc/asound/cards
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with ALC650F at 0xe8000c00, irq 17


# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7
# Load optional modules above their base modules
install snd modprobe --ignore-install snd && { modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a modprobe --ignore-install snd-ad1816a && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 modprobe --ignore-install snd-ad1848 && /lib/alsa/modprobe-post-install snd-ad1848
install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 modprobe --ignore-install snd-als100 && /lib/alsa/modprobe-post-install snd-als100
install snd-als4000 modprobe --ignore-install snd-als4000 && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci modprobe --ignore-install snd-armaaci && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi modprobe --ignore-install snd-asihpi && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp modprobe --ignore-install snd-atiixp && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 modprobe --ignore-install snd-au1x00 && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 modprobe --ignore-install snd-au8810 && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 modprobe --ignore-install snd-au8820 && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 modprobe --ignore-install snd-au8830 && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 modprobe --ignore-install snd-azt2320 && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 modprobe --ignore-install snd-azt3328 && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 modprobe --ignore-install snd-ca0106 && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci modprobe --ignore-install snd-cmipci && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 modprobe --ignore-install snd-cs4231 && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 modprobe --ignore-install snd-cs4232 && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 modprobe --ignore-install snd-cs4281 && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx modprobe --ignore-install snd-cs46xx && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-darla20 modprobe --ignore-install snd-darla20 && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 modprobe --ignore-install snd-darla24 && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x modprobe --ignore-install snd-dt019x && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g modprobe --ignore-install snd-echo3g && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x modprobe --ignore-install snd-emu10k1x && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 modprobe --ignore-install snd-ens1370 && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 modprobe --ignore-install snd-ens1371 && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 modprobe --ignore-install snd-es1688 && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx modprobe --ignore-install snd-es18xx && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 modprobe --ignore-install snd-es1938 && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 modprobe --ignore-install snd-es1968 && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 modprobe --ignore-install snd-es968 && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 modprobe --ignore-install snd-fm801 && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x modprobe --ignore-install snd-fm801-tea575x && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 modprobe --ignore-install snd-gina20 && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 modprobe --ignore-install snd-gina24 && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic modprobe --ignore-install snd-gusclassic && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme modprobe --ignore-install snd-gusextreme && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax modprobe --ignore-install snd-gusmax && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony modprobe --ignore-install snd-harmony && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel modprobe --ignore-install snd-hda-intel && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp modprobe --ignore-install snd-hdsp && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm modprobe --ignore-install snd-hdspm && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 modprobe --ignore-install snd-ice1712 && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 modprobe --ignore-install snd-ice1724 && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo modprobe --ignore-install snd-indigo && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj modprobe --ignore-install snd-indigodj && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio modprobe --ignore-install snd-indigoio && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 modprobe --ignore-install snd-intel8x0 && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave modprobe --ignore-install snd-interwave && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb modprobe --ignore-install snd-interwave-stb && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 modprobe --ignore-install snd-korg1212 && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 modprobe --ignore-install snd-layla20 && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 modprobe --ignore-install snd-layla24 && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 modprobe --ignore-install snd-maestro3 && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia modprobe --ignore-install snd-mia && /lib/alsa/modprobe-post-install snd-mia
install snd-miro modprobe --ignore-install snd-miro && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart modprobe --ignore-install snd-mixart && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona modprobe --ignore-install snd-mona && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 modprobe --ignore-install snd-mpu401 && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle modprobe --ignore-install snd-msnd-pinnacle && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav modprobe --ignore-install snd-mtpav && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 modprobe --ignore-install snd-nm256 && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 modprobe --ignore-install snd-opti92x-ad1848 && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 modprobe --ignore-install snd-opti92x-cs4231 && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x modprobe --ignore-install snd-opti93x && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 modprobe --ignore-install snd-pc98-cs4232 && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp modprobe --ignore-install snd-pcsp && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr modprobe --ignore-install snd-pcxhr && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf modprobe --ignore-install snd-pdaudiocf && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus modprobe --ignore-install snd-pdplus && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 modprobe --ignore-install snd-portman2x4 && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac modprobe --ignore-install snd-powermac && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 modprobe --ignore-install snd-pxa2xx-ac97 && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-rme32 modprobe --ignore-install snd-rme32 && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 modprobe --ignore-install snd-rme96 && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 modprobe --ignore-install snd-rme9652 && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 modprobe --ignore-install snd-s3c2410 && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 modprobe --ignore-install snd-sa11xx-uda1341 && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 modprobe --ignore-install snd-sb16 && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 modprobe --ignore-install snd-sb8 && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe modprobe --ignore-install snd-sbawe && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi modprobe --ignore-install snd-serialmidi && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 modprobe --ignore-install snd-serial-u16550 && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy modprobe --ignore-install snd-sgalaxy && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes modprobe --ignore-install snd-sonicvibes && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape modprobe --ignore-install snd-sscape && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 modprobe --ignore-install snd-sun-amd7930 && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 modprobe --ignore-install snd-sun-cs4231 && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri modprobe --ignore-install snd-sun-dbri && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident modprobe --ignore-install snd-trident && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio modprobe --ignore-install snd-usb-audio && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y modprobe --ignore-install snd-usb-usx2y && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 modprobe --ignore-install snd-vx222 && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxp440 modprobe --ignore-install snd-vxp440 && /lib/alsa/modprobe-post-install snd-vxp440
install snd-vxpocket modprobe --ignore-install snd-vxpocket && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront modprobe --ignore-install snd-wavefront && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci modprobe --ignore-install snd-ymfpci && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2


Here are the cut&pastes of those two.

---

### Post by Sutekh on 2006-05-12
That particular card should be supported by the intel8x0 sound module.  I can't decipher that output above.

You can check to see what modules have been installed using
```
lsmod | grep snd
``` 
To see if you have any modules such as **snd-intel8x0**

If you want to install the intel8x0 sound modules you should start here

[ALSA- Intel 8x0 Drver Instructions]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0")

From the [ALSA Soundcard Matrix of supported hardware]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix")

---

